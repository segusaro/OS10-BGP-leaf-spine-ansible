Route-map role
==============

This role facilitates the configuration of route-map attributes, and the role is abstracted for dellos10. The route-map role requires an SSH connection for connectivity to a Dell EMC Networking device. You can use any of the built-in Dell EMC Networking OS connection variables, or the ``provider`` dictionary.

Installation
------------

    ansible-galaxy install Dell-Networking.dellos-route-map

Role variables
--------------

- Role is abstracted using the *ansible_net_os_name* variable that can take dellos10 values
- If *dellos_cfg_generate* is set to true, the variable generates the role configuration commands in a file
- Any role variable with a corresponding state variable set to absent negates the configuration of that variable 
- Setting an empty value for any variable negates the corresponding configuration
- Variables and values are case-sensitive

**dellos_route_map keys**

| Key        | Type                      | Description                                             | Support               |
|------------|---------------------------|---------------------------------------------------------|-----------------------|
| ``route_map`` | list | Configures the route-map (see ``route_map.*``) | dellos10 |
| ``route_map.name`` | string (required)        | Configures the route-map name  | dellos10 |
| ``route_map.permit`` | boolean | Configures permit/deny set operations | dellos10 |
| ``route_map.seq_num`` | integer         | Configures the sequence number | dellos10 |
| ``route_map.continue`` | integer         | Configures next sequence number. | dellos10 |
| ``route_map.set`` | dictionary | Configures route map to set values in destination routing protocol. See the following set.* keys for each list item. | dellos10 |
| ``set.local_pref`` | integer   | Configures the BGP local preference path attribute.     | dellos10 |
| ``set.metric`` | string, choices: "+ &lt;value&gt;","- &lt;value&gt;", &lt;value&gt; | Configures add or subtract from the existing metric value.     | dellos10 |
| ``set.metric_type`` | string, choices: internal,type-1,type-2 | Configures the metric type for destination routing protocol.     | dellos10 |
| ``set.origin`` | string, choices: igp,egp,incomplete   | Configures the BGP origin attribute.     | dellos10 |
| ``set.weight`` | integer   | Configures the weight for the BGP route.     | dellos10 |
| ``set.comm_list`` | dictionary   | Configures the BGP community list. See the following comm_list.* for each item.     | dellos10 |
| ``comm_list.add`` | string | Adds community attribute of a BGP update. | dellos10 |
| ``comm_list.delete`` | string | Removes community attribute of a BGP update. | dellos10 |
| ``set.community`` | string   | Configures the community attribute for a BGP route update.     | dellos10 |
| ``set.extcomm_list`` | dictionary   | Configures the BGP extcommunity list. See the following extcomm_list.* for each item.     | dellos10 |
| ``extcomm_list.add`` | string | Adds extended community attribute of a BGP update. | dellos10 |
| ``extcomm_list.delete`` | string | Removes extended community attribute of a BGP update. | dellos10 |
| ``set.extcommunity`` | string   | Configures the extended community attribute for a BGP route update.     | dellos10 |
| ``set.next_hop`` | list   | Configures the next hop address. See the following next_hop.* for each item.     | dellos10 |
| ``next_hop.type`` | string, choices: ip,ipv6 | Configures type of next hop address. | dellos10 |
| ``next_hop.address`` | string | Configures next hop address. | dellos10 |
| ``next_hop.track_id`` | integer | Configures object track ID. | dellos10 |
| ``next_hop.state`` | string, choices: present*,absent   | If set to absent deletes the next hop address.  | dellos10 |
| ``route_map.match`` | list | Configures route map to match values from route table. See the following match.* keys for each list item. | dellos10 |
| ``match.ip_type`` | string (required), choices: ipv4, ipv6   | Configures the IPv4/IPv6 address to match.     | dellos10 |
| ``match.access_group`` | string     | configures the access group or list to match.                   | dellos10 |
| ``match.prefix_list`` | string     | configures the IP prefic list to match against.                   | dellos10 |
| ``route_map.state`` | string, choices: present*,absent   | If set to absent deletes the route map.  | dellos10 |
| ``as_path`` | list | Configures BGP autonomous system path filter. See the following as_path.* keys for each list item. | dellos10 |
| ``as_path.access_list`` | string (required)         | Configures the access list name.               | dellos10 |
| ``as_path.permit`` | boolean(required) | Configures as path to accept or reject.   | dellos10  |
| ``as_path.regex``| string (required)         | Configures the regular expression.               | dellos10 |
| ``as_path.state`` | string, choices: absent, present*     | If set to absent, deletes the BGP as path filter.          | dellos10 |
| ``community_list`` | list | Configures community list entry. See the following community_list.* keys for each list item. | dellos10 |
| ``community_list.type`` | string (required), choices: standard, expanded        | Configures the type of community list entry.               | dellos10 |
| ``community_list.name`` | string (required)     | Configures the name of community list entry.               | dellos10 |
| ``community_list.permit`` | boolean(required) | Configures community to accept or reject.   | dellos10 |
| ``community_list.regex`` | string (required)         | Configures the regular expression for expanded community list. This key is mutual exclusive with community_list.community.    | dellos10 |
| ``community_list.community`` | string (required)         | Configures well known community or community number for standard community list. This key is mutual exclusive with community_list.regex.            | dellos10 |
| ``community_list.state`` | string, choices: absent, present*     | If set to absent, deletes the community list entry.   | dellos10 |
| ``extcommunity_list`` | list | Configures extcommunity list entry. See the following extcommunity_list.* keys for each list item.  | dellos10 |
| ``extcommunity_list.type`` | string (required), choices: standard, expanded    | Configures the type of extcommunity list entry.               | dellos10 |
| ``extcommunity_list.name`` | string (required)     | Configures the name of extcommunity list entry.               | dellos10 |
| ``extcommunity_list.permit`` | boolean(required) | Configures extcommunity to accept or reject.   | dellos10  |
| ``extcommunity_list.regex`` | string (required)         | Configures the regular expression for expanded extcommunity list. This key is mutual exclusive with extcommunity_list.community.    | dellos10 |
| ``extcommunity_list.community`` | string (required)         | Configures extended community for standard community list. This key is mutual exclusive with extcommunity_list.regex.            | dellos10 |
| ``extcommunity_list.state`` | string, choices: absent, present*     | If set to absent, deletes the extcommunity list entry.   | dellos10 |


> **NOTE**: Asterisk (\*) denotes the default value if none is specified. 

Connection variables
--------------------

Ansible Dell EMC Networking roles require connection information to establish communication with the nodes in your inventory. This information can exist in the Ansible *group_vars* or *host_vars* directories, or in the playbook itself.

| Key         | Required | Choices    | Description                                         |
|-------------|----------|------------|-----------------------------------------------------|
| ``host`` | yes      |            | Specifies the hostname or address for connecting to the remote device over the specified transport |
| ``port`` | no       |            | Specifies the port used to build the connection to the remote device; if unspecified, the value defaults to 22 |
| ``username`` | no       |            | Specifies the username that authenticates the CLI login for the connection to the remote device; if value is unspecified, the ANSIBLE_NET_USERNAME environment variable value is used  |
| ``password`` | no       |            | Specifies the password that authenticates the connection to the remote device; if value is unspecified, the ANSIBLE_NET_PASSWORD environment variable value is used |
| ``authorize`` | no       | yes, no\*   | Instructs the module to enter privileged mode on the remote device before sending any commands; if value is unspecified, the ANSIBLE_NET_AUTHORIZE environment variable value is used, and the device attempts to execute all commands in non-privileged mode |
| ``auth_pass`` | no       |            | Specifies the password to use if required to enter privileged mode on the remote device; if *authorize* is set to no, this key is not applicable; if value is unspecified, the ANSIBLE_NET_AUTH_PASS environment variable value is used  |
| ``provider`` | no       |            | Passes all connection arguments as a dictonary object; all constraints (such as required or choices) must be met either by individual arguments or values in this dictionary |

> **NOTE**: Asterisk (\*) denotes the default value if none is specified.

Dependencies
------------

The *dellos-route-map* role is built on modules included in the core Ansible code. These modules were added in Ansible version 2.2.0.

Example playbook
----------------

This example uses the *dellos.dellos-route-map* role for the route-map, policy-map, and class-map. It creates a *hosts* file with the switch details and corresponding variables. The hosts file should define the *ansible_net_os_name* variable with corresponding Dell EMC networking OS name. When *dellos_cfg_generate* is set to true, the variable generates the configuration commands as a .part file in *build_dir* path. By default, the variable is set to false.

It writes a simple playbook that only references the *dellos-route-map* role. By including the role, you automatically get access to all of the tasks to configure route-map features. 

**Sample hosts file**
 
    leaf1 ansible_host= <ip_address> ansible_net_os_name= <OS name(dellos10)>

**Sample host_vars/leaf1**

    hostname: leaf1
    provider:
      host: "{{ hostname }}"
      username: xxxxx 
      password: xxxxx
      authorize: yes
      auth_pass: xxxxx 
    build_dir: ../temp/dellos10
	  
    dellos_route_map:
      as_path:
        - access_list: aa
          permit: true
          regex: www
          state: present
      community_list:
        - type: expanded
          name: qq
          permit: true
          regex: aaa
          state: present
        - type: standard
          name: qqq
          permit: false
          community: internet
          state: present
      extcommunity_list:
        - type: expanded
          name: qq
          permit: true
          regex: aaa
          state: present
        - type: standard
          name: qqq
          permit: false
          community: "rt 22:33"
          state: present
      route_map:
        - name:  test
          permit: true
          seq_num: 1
          continue: 20
          match:
           - ip_type: ipv4
             access_group: testaccess
             prefix_list: testprefix
          set:
            local_pref: 1200
            metric_type: internal
            metric: + 30
            origin: igp
            weight: 50
            next_hop:
              - type: ip
                address: 10.1.1.1
                track_id: 3
                state: present
            community: internet
            comm_list:
              add: qq
              delete: qqq
            extcommunity: "22:33"
            extcomm_list:
              add: aa
              delete: aa
          state: present

**Simple playbook to setup qos - leaf.yaml**

    - hosts: leaf1
      roles:
         - Dell-Networking.dellos-route-map

**Run**

    ansible-playbook -i hosts leaf.yaml

(c) 2017 Dell EMC

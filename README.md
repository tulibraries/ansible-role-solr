Role Name
=========

Installs Solr 5 and above as a system process using the embedded jetty. Follows the methods
outlined in the standard install-solr-service.sh script distributed with solr,
but allow for more overrides, and customization, and idempotency.

Requirements
------------

Requires Java to be installed. 

Role Variables
--------------
```yaml

solr_create_user: true
solr_user: solr
solr_group: "{{ solr_user }}"

solr_service_name: solr

solr_version: "5.5.1"
solr_mirror: "https://archive.apache.org/dist"
solr_filename: solr-{{ solr_version }}
solr_download_path: /root

solr_install_base_path: /opt
solr_versioned_install_path: "{{ solr_install_base_path}}/{{ solr_filename }}"
solr_working_path: "{{ solr_install_base_path}}/solr"


solr_base_path: /var/solr
solr_home_path: "{{solr_base_path}}/data"

solr_logs_path: "{{ solr_base_path}}/logs"
solr_log4j_props: "{{ solr_base_path }}/log4j.properties"


solr_heap_size: 1024M

solr_port: 8983

# set to false to not configure solr as a system service
solr_configure_service: true

# Set to true to use systemd unit instead of a init.d script 
solr_use_systemd: false
```

Installation
------------

`ansible-galaxy install tulibraries.solr`

or add it to you [required roles file](https://galaxy.ansible.com/intro#download-advanced).

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - tulibraries.solr

Local Testing
-------------

To test locally before using in your playbook, a minimal vagrant setup is included. Defaults to a centos 7 box and uses systemd. 

To use, change directory into `tests/vagrant` and run vagrant up.  
 

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).

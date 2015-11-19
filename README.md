## Infrastructure: Development Tools
========
###### By David Harper <rndpxl@gmail.com>

`The usage of these scripts is at your own risk. They have been tested in production environments, but we cannot be held responsible for anything that happens in your environments.`

These playbooks install our suite of development tools and build servers automatically. They can be used for clean installs or upgrades. They are designed for use on Ubuntu 14.04LTS boxes.

Run the playbook like this:

    ansible-playbook -i hosts/production atlassian-jira-server.yml

The `-i` parameter takes a name of a file within the `hosts` directory. This file contains the servers that are involved in the deployment to that environment.

The above YML file would install JIRA to the servers mentioned in the hosts and the version specified in `group_vars\atlassian-jira-server-hosts`.

# Updating to newer versions of the tools

These playbooks will also handle updating to newer versions. Just update the version numbers and download paths in the variable files for each tool and the next time
you run the playbook it will 

# Getting started
To make use of these scripts, you need to update `group_vars` and `hosts` to match your environment. 
Set different database passwords for all the applications along with base url's where they will be hosted. These MUST match your environment.

Use the `production.example` inventory file as a base template. This allows you to specify only a few root hosts, and lots of the plays inherit from these.

A recommended setup would be:

 - Server 1 [devtools-management]  (8GB of RAM)
     - Apache Proxy
     - Jira
     - Crowd
     - Confluence


 - Server 2 [devtools-code]   (8GB of RAM)
     - Apache Proxy
     - Bitbucket
     - Bamboo
     - Sonarqube
     - Selenium Host
   
   
 - Build Servers
     - Bamboo Agent
     - SonarRunner
     - Selenium Node

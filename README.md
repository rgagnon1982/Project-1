# Project-1
Project 1 in class

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Project 1 diagram](https://github.com/rgagnon1982/Project-1/blob/main/Diagrams/Project%201%20diagram.jpg)



These files have been tested and used to generate a live ELK deployment on Azure. Yaml files. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the file may be used to install only certain pieces of it, such as Filebeat.



#  [ansible.cfg](Ansible\ansible.cfg) 

 [filebeat-config .yml](Ansible\filebeat-config .yml) 

 [filebeat-playbook.yml](Ansible\filebeat-playbook.yml) 

 [hosts.yml](Ansible\hosts.yml) 

 [install-elk.yml](Ansible\install-elk.yml) 

 [metricbeat-config.yml](Ansible\metricbeat-config.yml) 

 [metricbeat-playbook.yml](Ansible\metricbeat-playbook.yml) 

This document contains the following details:

- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build




### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be high availability and reliability, in addition to restricting _____traffic to the network.

-  What aspect of security do load balancers protect? a network from DDoS attacks  What is the advantage of a jump box?the advantage of having a jumpbox is that only one machine on the network will be connected to the internet.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and and system logs.

- Filebeat helps generate and organize log files to send to Logstash and Elasticsearch. Specifically, it logs information about the file system, including which files have changed and when. (source class slide)
- Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify such as Elasticsearch or Logstash. (source google)

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
| -------- | -------- | ---------- | ---------------- |
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Elk      | DVWA     | 10.2.0.4   | Linux            |
| web1     | DVWA     | 10.0.0.5   | Linux            |
| web2     | DVWA     | 10.0.0.6   | Linux            |
| web3     | DVWA     | 10.0.0.7   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

# local public IP through TCP 5601

Machines within the network can only be accessed by the jumpbox____.

Which machine did you allow to access your ELK VM?  Jumpbox What was its IP address?_20.102.63.28

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses                   |
| -------- | ------------------- | -------------------------------------- |
| Jump Box | Yes (SSH)           | local machine public IP address        |
| Web1     | Yes (HTTP)          | local machine IP address 104.43.250.51 |
| Web2     | Yes (HTTP)          | local machine IP address 104.43.250.51 |
| Web3     | Yes (HTTP)          | local machine IP address 104.43.250.51 |
| ELK      | Yes (HTTP)          | local machine IP address 104.43.250.51 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

- What is the main advantage of automating configuration with Ansible?_ Ansible is advantageous because it provides consistant deployment and management

The playbook implements the following tasks:

- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- install docker.io, 
- intall python3.pip,
-  install the docker module,
-  increase virtual memory, allocate
- allocate increased memory
- download docker ELK image and launch
- enable docker service on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Project 1 diagram](https://github.com/rgagnon1982/Project-1/blob/main/Images/Project%20screenshot%2012-4-21.JPG)

### Target Machines & Beats

This ELK server is configured to monitor the following machines:web 1, web2 web 3

- List the IP addresses of the machines you are monitoring_ 10.0.05, 10.0.06, 10.0.0.7

We have installed the following Beats on these machines:

- FIlebeat and Metric beat

These Beats allow us to collect the following information from each machine:

- _Metricsbeats allows us to collect macine metrics and cpu usage of the machine.  

- _Filebeats allows us to collect and montior logs files generated by Apache, Microsoft Azure tools, the Nginx web server and my SQL databases.,_

  

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

- Copy the Playbook file to /etc/ansible
- Update the hosts file to include the IP addresses of machines you want to configure, as well as python interpreter itll be using.
- Run the playbook, and navigate to the new configured virutal machine to check that the installation worked as expected.

 Answer the following questions to fill in the blanks:_

- _Which file is the playbook? This question is not specific but the playbooks that we have are .yml and begin with "---" .  _
- _Where do you copy it?_ /etc/ansible
- _Which file do you update to make Ansible run the playbook on a specific machine? Host file
- _How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ The host file is used to tell Ansible which machines to configure. The hosts file can desginate groups by writing a group name in brackets such as webservers.
- _Which URL do you navigate to in order to check that the ELK server is running?
- http://<public_ELK_IP>:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

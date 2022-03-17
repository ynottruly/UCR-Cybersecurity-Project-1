# UCR-Cybersecurity-Project-1
Collection of works from my first cybersecurity project at UCR extension
Automated ELK Stack Deployment in Azure Cloud

The files in this repository were used to configure the network depicted below:

![alt text](https://github.com/ynottruly/UCR-Cybersecurity-Project-1/blob/main/Images/ElkDiagram.JPG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the configuration file may be used to install only certain pieces of it, such as Filebeat.

[Filebeat Playbook](https://github.com/ynottruly/UCR-Cybersecurity-Project-1/blob/main/Ansible/Filebeat_Playbook) - [Metricbeat Playbook](https://github.com/ynottruly/UCR-Cybersecurity-Project-1/blob/main/Ansible/Metricbeat_Playbook) - [Install VM with Docker](https://github.com/ynottruly/UCR-Cybersecurity-Project-1/blob/main/Ansible/Install_Docker_Playbook) - [Install ELK PLaybook](https://github.com/ynottruly/UCR-Cybersecurity-Project-1/blob/main/Ansible/Install_Elk_Playbook)

**Description of the Topology**

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting the exposure of the backend servers to the external network.


Load Balancers contribute to the Availability aspect of security in regards to the CIA Triad by support of redundancy , network performance.

JumpBox used for System Administration and secured external network access.

The advantage of a JumpBox is the origination point for launching Administrative Tasks. This ultimately sets the JumpBox as a Secure Admin Workstation. All administrators, when conducting any management Tasks will be required to connect to the JumpBox. The Jumpbox is configured for restrictive access providing a more secure environment.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the  and system resources.

Filebeat watches for log files or locations that are configured, collecting log events and forwards them to Elasticsearch or Logstash for indexing

Metricbeat records metric and statistical data from the operating system and from the services running on the host servers.

The configuration details of each machine may be found below.

![Table1](https://user-images.githubusercontent.com/94151496/158731602-3c71324b-421c-4259-9fbe-070482dc09a9.JPG)

**Access Policies**

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

Whitelisted IP address: Admin’s personal home network

Machines within the network can only be accessed by SSH.

Which machine did you allow to access your ELK VM? What was its IP address? JumpBoxProvisioner 10.0.0.4


A summary of the access policies in place can be found in the table below.

![Table2](https://user-images.githubusercontent.com/94151496/158731763-d444ff0a-83a0-4d4c-9d75-daad265db741.JPG)

**Elk Configuration**

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually.

The main advantage that Ansible brings is automation of and simplification of repetitive, complex, and tedious operations as a systems admin.


The playbook implements the following tasks:

Install: docker.io

Install: python3-pip

Install: docker module

Increase Memory Use: sysctl -w vm.max_count=262144

Download and launch docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![alt text](https://github.com/ynottruly/UCR-Cybersecurity-Project-1/blob/main/Images/ElkContainer.JPG)

**Target Machines & Beats**

This ELK server is configured to monitor the following machines:

![Table3](https://user-images.githubusercontent.com/94151496/158732193-25937413-a814-4abb-a5c6-ce787f9fef64.JPG)

These Beats allow us to collect the following information from each machine:

Filebeat is a lightweight shipper for forwarding and centralizing log data. Filebeat monitors log files or locations you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.

Metricbeat collects metrics from the operating system and from services running on the server. Metricbeat then takes the metrics and statistics that it collects and ships them to the output that you specify.


**Using the Playbook**

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

Copy the config file to the /etc/ansible/files directory.

Update the configuration file to include the private IP (10.1.0.5) of the Elk Server to the ElasticSearch and Kibana

Run the playbook, and navigate to http://104.43.169.128:5601/app/kibana to check that the installation worked as expected.

Create a new playbook in the /etc/ansible/roles/ directory that will install, drop in the updated configuration file, enable and configure system module, run the filebeat setup, and start the filebeat service


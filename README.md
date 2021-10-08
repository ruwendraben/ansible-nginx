# ansible-nginx
# Motive
ansible based ubuntu 20.04 LTS AMI for launch Nginx Server

# Purpose
Excetel practice module

# Problem
Reduce the burden of setting up the IAAS modules faster, accurate using a cook book

# Learn
Ansible, terraform basics and improve AWS managed services knowledge

## How to Use ##
1. git clone https://github.com/ruwendraben/ansible-nginx.git 

2. cd ansible-nginx/sample-playbooks

3. Ansible steps are contained under roles/web/nginx/tasks/main.yaml
(Update and upgrade apt packages -> Install the nginx package -> Copy custom index.html file -> Edit Configuration in Nginx -> start the nginx service)

4. Nginx webcontent are located in roles/web/nginx/files/index.html

Note:- 	configure proxy_pass <IP> inside roles/web/nginx/files/index.html
	Listener port:	/etc/nginx/sites-available/default {Listen port 9001}
	Proxy pass config in proxy server(/etc/nginx/sites-available/default):	location / { proxy_pass http://172.31.30.62:9001;}i
        proxy_pass Server IP should be added to env/hosts file

5. configure host ip file: env/hosts ( example: [webservers]   )
				     (          172.31.8.209   )

6. Run ansible checks
   ansible-playbook -i env/hosts site.yaml --check

7. Run ansible
   ansible-playbook -i env/hosts site.yaml 

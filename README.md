# Ansible playbooks for tools installation
This repo holds playbooks used to install different logging and monitoring tools

## Requirements
- Ansible
- Inventory host file containing
    - a "log" group containing
	- a "logsource" group
	- a "logdestination" group
	- a variable "log_dest_port" indicating the destination port
    - a "logsource" group containing
	- the hostname of the server producing the logs
	- a variable log_file indicating the log file where the logs are produced
	- a variable log_dest_host indicating the hostname of the server collecting the logs
    - a "logdestination" group containing
	- the hostname of the server receiving the logs

## Inventory file example
```
[log:children]
logsource
logdestination

[log:vars]
log_dest_port=6514

[logsource]
localhost log_file=/var/log/messages log_dest_host=localhost

[logdestination]
localhost 
```

# Manage virtualbox with `VBoxManage`

### List all VMS
`VBoxManage list vms`
### List of Running VMs
`VBoxManage list runningvms`
### Restart VM
`VBoxManage controlvm "<VM-ID>" reset`
-------
### Check Remote Display settings
	* For a particular VM
	```
	VBoxManage showvminfo <VMNAME> | grep "VRDE"
	```
	* For all VMS
	```
	for vm in $(VBoxManage list vms | awk -F'"' '{print $2}'); do echo "VM Name: $vm"; VBoxManage showvminfo "$vm" | grep "VRDE"; echo "------------------"; done
	```
### List forwarded VM ports
	* For a particular VM
	```
	VBoxManage showvminfo <VMNAME> --machinereadable | grep 'Forwarding'
	```
	* For all VMS
	```
	for vm in $(VBoxManage list vms | awk -F'"' '{print $2}'); do echo "VM Name: $vm"; VBoxManage showvminfo "$vm" | grep 'Forwarding'; echo "------------------"; done
	```
-------
### Add Remote Display settings
	* For a particular VM
	```
	VBoxManage modifyvm <VMNAME> --vrdeport 4000
	```
------
### Delete VM with all files
`VBoxManage unregistervm "<VM-ID>" --delete`


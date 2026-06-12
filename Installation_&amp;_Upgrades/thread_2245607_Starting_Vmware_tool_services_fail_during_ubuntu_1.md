---
title: "Starting Vmware tool services fail during ubuntu 14.04 boot"
date: 2014-09-24
forum: Installation &amp; Upgrades
---

### Post by facosta on 2014-09-24
I would like to resolve Vmware tool services fail during Ubuntu 14.04 boot.
I am running:

Linux ubuntu 3.13.0-36-generic #63-Ubuntu SMP
VM Player 6.0.2 build

Thanks

---

### Post by facosta on 2014-09-26
Problem resolved.

1. Uninstalled Vmware Tools:

facosta@ubuntu:~$ sudo vmware-uninstall-tools.pl
[sudo] password for facosta: 
Uninstalling the tar installation of VMware Tools.

Stopping services for vmware-tools

initctl: Unknown instance: 
Stopping services for vmware-tools-thinprint

vmware-tools-thinprint stop/waiting
File /etc/pulse/default.pa is backed up to /etc/pulse/default.pa.old.0.

update-initramfs: Generating /boot/initrd.img-3.13.0-36-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
update-initramfs: Generating /boot/initrd.img-3.13.0-35-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
update-initramfs: Generating /boot/initrd.img-3.13.0-34-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
update-initramfs: Generating /boot/initrd.img-3.13.0-33-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
update-initramfs: Generating /boot/initrd.img-3.13.0-32-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
update-initramfs: Generating /boot/initrd.img-3.13.0-30-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
update-initramfs: Generating /boot/initrd.img-3.13.0-24-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
The removal of VMware Tools 9.6.2 build-1688356 for Linux completed 
successfully.  Thank you for having tried this software.

2. Reinstalled Vmware Tools:

To install VMware Tools, you must mount the  VMware Tools CD image, extract the contents (VMware Tools), and then  run the installer.

**Note**: If VMware Tools is  already installed, these steps uninstall and then reinstall VMware  Tools. When the product updates, the VMware Tools package is also  updated, so an update of the installed version of VMware Tools is  required.
**Ubuntu or Ubuntu Server with a graphical user interface**

To mount the CD image and extract the contents:

[LIST=1]
[*]Power on the virtual machine.
[*]Log into the virtual machine using an account with administrator or root privileges.
[*]Go to **Virtual Machine** > **Install VMware Tools** (or **VM** > **Install VMware Tools**).

**Note**:  If you are running the light version of Fusion, a version of  Workstation without VMware Tools, or VMware Player, you are prompted to  download VMware Tools before they can be installed. Click **Download Now** to begin the download.
[*]Open the VMware Tools CD mounted on the Ubuntu desktop.
[*]Right-click the file name that is similar to VMwareTools.x.x.x-xxxx.tar.gz, click **Extract to**, and select the Ubuntu Desktop to save the extracted contents.

The vmware-tools-distrib folder is extracted to the Ubuntu Desktop.
[/LIST]
To install VMware Tools in Ubuntu:

[LIST=1]
[*]Open a Terminal window. For more information, see [Opening a command or shell prompt (1003892)]("http://kb.vmware.com/selfservice/search.do?cmd=displayKC&docType=kc&docTypeID=DT_KB_1_1&externalId=1003892").
[*]In the Terminal, run this command to navigate to the vmware-tools-distrib folder:

cd Desktop/vmware-tools-distrib
[*]Run this command to install VMware Tools:

sudo ./vmware-install.pl -d

**Note**: The -d switch assumes that you want to accept the defaults. If you do not use -d, press **Return** to accept the defaults or supply your own answers.
[*]Enter your Ubuntu password.
[*]Restart the Ubuntu virtual machine after the VMware Tools installation completes.
[/LIST]

Vmware Tool Services Fail error is now gone.

---


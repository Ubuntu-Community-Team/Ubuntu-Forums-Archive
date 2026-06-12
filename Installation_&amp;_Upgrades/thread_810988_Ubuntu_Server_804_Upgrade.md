---
title: "Ubuntu Server 804 Upgrade?"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by razeshkale on 2008-05-28
Hi there,
After upgrading to 804 Ubuntu Server my VMWare server is not more available on system which was install on Ubuntu Server 704
after that was trying to get install on 804 but getting some weird errors!
here is the log for installation!

> administrator@ubuntuserver:~$ aptitude install linux-headers-`uname -r` build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
administrator@ubuntuserver:~$ su
Password: 
root@ubuntuserver:/home/administrator# aptitude install linux-headers-`uname -r` build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for linux-headers-2.6.22-14-generic
No candidate version found for linux-headers-2.6.22-14-generic
The following packages are unused and will be REMOVED:
  fping hwdb-client-common hwdb-client-gnome module-assistant netkit-inetd 
The following NEW packages will be automatically installed:
  g++ g++-4.2 libc6-dev libstdc++6-4.2-dev linux-libc-dev 
The following packages have been kept back:
  f-spot 
The following NEW packages will be installed:
  build-essential g++ g++-4.2 libc6-dev libstdc++6-4.2-dev linux-libc-dev 
0 packages upgraded, 6 newly installed, 5 to remove and 1 not upgraded.
Need to get 7492kB of archives. After unpacking 27.5MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-17.31 [694kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main libc6-dev 2.7-10ubuntu3 [2538kB]     
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main libstdc++6-4.2-dev 4.2.3-2ubuntu7 [1217kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main g++-4.2 4.2.3-2ubuntu7 [3035kB]      
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main g++ 4:4.2.3-1ubuntu3 [1446B]         
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main build-essential 11.3ubuntu1 [7070B]  
Fetched 7492kB in 1min40s (74.2kB/s)                                            
(Reading database ... 109103 files and directories currently installed.)
Removing hwdb-client-gnome ...
Removing fping ...
Removing hwdb-client-common ...
Removing module-assistant ...
Removing netkit-inetd ...
 * Stopping internet superserver...                                      [ OK ] 
Selecting previously deselected package linux-libc-dev.
(Reading database ... 108959 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-17.31_amd64.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu3_amd64.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.3-2ubuntu7_amd64.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.3-2ubuntu7_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu3_amd64.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_amd64.deb) ...
Setting up linux-libc-dev (2.6.24-17.31) ...
Setting up libc6-dev (2.7-10ubuntu3) ...
Setting up libstdc++6-4.2-dev (4.2.3-2ubuntu7) ...
Setting up g++-4.2 (4.2.3-2ubuntu7) ...
Setting up g++ (4:4.2.3-1ubuntu3) ...

Setting up build-essential (11.3ubuntu1) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
root@ubuntuserver:/home/administrator# aptitude install xinetd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  f-spot 
The following NEW packages will be installed:
  xinetd 
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 146kB of archives. After unpacking 397kB will be used.
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main xinetd 1:2.3.14-5 [146kB]
Fetched 146kB in 2s (53.5kB/s) 
Selecting previously deselected package xinetd.
(Reading database ... 110664 files and directories currently installed.)
Unpacking xinetd (from .../xinetd_1%3a2.3.14-5_amd64.deb) ...
Setting up xinetd (1:2.3.14-5) ...
 * Stopping internet superserver xinetd                                  [ OK ] 
 * Starting internet superserver xinetd                                  [ OK ] 

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
root@ubuntuserver:/home/administrator# tar -xzf /Path/To/VMware-server-1.0.3-xxx.tar.gz
tar: /Path/To/VMware-server-1.0.3-xxx.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
root@ubuntuserver:/home/administrator# tar -xzf '/home/administrator/Desktop/VMware-server-1.0.4-56528.tar.gz' 
root@ubuntuserver:/home/administrator# cd vmware-server-distrib
root@ubuntuserver:/home/administrator/vmware-server-distrib# sudo vmware-install.pl
sudo: unable to resolve host ubuntuserver
sudo: vmware-install.pl: command not found
root@ubuntuserver:/home/administrator/vmware-server-distrib# sudo vmware-install.pl
sudo: unable to resolve host ubuntuserver
sudo: vmware-install.pl: command not found
root@ubuntuserver:/home/administrator/vmware-server-distrib# sudo vmware-config.pl
sudo: unable to resolve host ubuntuserver
sudo: vmware-config.pl: command not found
root@ubuntuserver:/home/administrator/vmware-server-distrib# vmware
bash: vmware: command not found
root@ubuntuserver:/home/administrator/vmware-server-distrib# sudo vmware-install
sudo: unable to resolve host ubuntuserver
sudo: vmware-install: command not found
root@ubuntuserver:/home/administrator/vmware-server-distrib# '/home/administrator/Desktop/vmware-server-distrib/vmware-install.pl' 
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.

root@ubuntuserver:/home/administrator/vmware-server-distrib# 


---

### Post by dstew on 2008-05-28
In the command```
tar -xzf /Path/To/VMware-server-1.0.3-xxx.tar.gz
```you need to substitute the actual path name and file name for the placeholders.

---

### Post by zvacet on 2008-05-29
You can try [this.]("http://www.howtoforge.com/vmware-server-on-ubuntu8.04")

---


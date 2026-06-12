---
title: "Problem installing Samba on Ubuntu 6.06"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by marcin.mtl on 2006-09-07
I try to install Samba on new installed Ubuntu.
I am receiving the following error:

marcin@asiulka:~$ sudo apt-get install samba smbfs
Reading package lists... Done
Building dependency tree... Done
samba is already the newest version.
smbfs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up samba (3.0.22-1ubuntu3.1) ...
 * Starting Samba daemons...                                             [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code 

 Any idea what is wrong?


thanks

Marcin

---

### Post by wpshooter on 2006-09-07
I am no expert of these things but it sounds like to me that SAMBA is already installed.

Here is the way I install SAMBA.  I go to SHARED FOLDERS under I think the ADMINISTRATION menu and when you click on shared folders, if SAMBA is not installed, it will tell you so and then all you have to do is check the SAMBA box and it will download and install it for you.  Advice, IMO, stop using these terminal commands (apt-get) and use the GUI functions in Ubuntu to do these task as they have designed them to do.

Good luck.

---

### Post by marcin.mtl on 2006-09-08
I agree that Samba is installed but it can't start.
**Starting Samba daemons...   [fail]**

I did installation both ways; using apt-get and then Synaptic Package Manager
both returning the same error: 
**Sub-process /usr/bin/dpkg returned an error code (1)**

I tried to uninstal Samba using "folders" as you suggested. Same problem.

thaks anyway

Marcin

---


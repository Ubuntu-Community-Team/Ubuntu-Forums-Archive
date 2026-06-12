---
title: "Installing VPN-client software"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by Qtips on 2008-08-18
Hi,

I'm trying to install on ubuntu 8.04 a vpn-client software provided by the informatics department of my university. This software permits me to access several database of the university libraries at my home via internet.

When i try to install, i obtain the following errors: 

```
steeve@steeve-laptop:~/VPN-client$ sudo ./vpn_install
[sudo] password for steeve: 
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.24-21-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-21-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-21-generic/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.24-21-generic/build SUBDIRS=/home/steeve/VPN-client modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /home/steeve/VPN-client/linuxcniapi.o
In file included from /home/steeve/VPN-client/Cniapi.h:15,
                 from /home/steeve/VPN-client/linuxcniapi.c:31:
/home/steeve/VPN-client/GenDefs.h:113: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/home/steeve/VPN-client/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/steeve/VPN-client] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

```

Can anyone explain me what i'm doing wrong ?

Thanks !

---

### Post by moneymonk on 2008-08-19
I am currently having the EXACT same issue.  any input would be appreciated...

mm

---

### Post by mellowd on 2008-08-19
Just a quick question, as this is a cisco vpn client have you checked cisco's site yet?

---

### Post by moneymonk on 2008-08-19
Cisco is no help unless you have a support contract with them.  I am installing this in order to connect to one of my client's networks, which requires a Cisco brand VPN client.

I went through the steps here: [http://ubuntuforums.org/showthread.php?t=883267](http://ubuntuforums.org/showthread.php?t=883267)
which did not fix my issue.

Thinking it was a problem with my kernel headers and kernel source , I followed the steps here:
[http://ubuntuforums.org/showthread.php?t=675906](http://ubuntuforums.org/showthread.php?t=675906)

Still no resolution.

I find it odd that there is no configure script in the un-tarred dir: 

> macas@macas:~/RP VPN Client/vpnclient$ ls
cisco_cert_mgr         ipseclog          sample.pcf
Cniapi.h               libdriver64.so    unixcniapi.h
config.h               libdriver.so      unixkernelapi.h
cvpnd                  libvpnapi.so      vpnapi.h
driver_build.sh        license.rtf       vpnclient
frag.c                 license.txt       vpnclient.ini
frag.h                 linuxcniapi.c     vpnclient_init
GenDefs.h              linuxcniapi.h     vpnclient-linux-2.6.22.diff
interceptor.c          linuxkernelapi.c  vpn_install
IPSecDrvOSFunctions.h  linux_os.h        vpn_ioctl_linux.h
IPSecDrvOS_linux.c     Makefile          vpn_uninstall
IPSecDrvOS_linux.h     mtu.h


this is my exact error:

> macas@macas:~/RP VPN Client/vpnclient$ sudo ./vpn_install 
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.24-19-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-19-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-19-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/macas/RP VPN Client/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** No rule to make target `VPN'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

---

### Post by moneymonk on 2008-08-20
OK!!!! i FINALLY got this thing to work!

Here are the instructions I followed from "jsn" ([http://ubuntuforums.org/showthread.php?t=769273&page=2](http://ubuntuforums.org/showthread.php?t=769273&page=2)), which were not very different from other instructions except that I removed all of my other downloads and grabbed these specifically:

> OK got it.. If you are still having issues.. Delete all your vpn downloads and get the ones from this thread,.

Extract the "vpnclient-linux-x86...." to your home folder (you can use the Archive manager)

Then copy the .diff file (patch) into the new vpnclient folder in your home folder.

cd into the vpnclient folder "cd vpnclient"

then do the

1. sudo apt-get install patch
2. patch <./vpnclient-linux-2.6.24-final.diff
3. sudo ./vpn_install

It installed right away for me.

Then you can put your .pcf file into /etc/opt/cisco-vpnclient/Profiles/ folder

To connect you open a terminal and type "sudo vpnclient connect (your pcf file name)

If it fails and says something about something not loaded.. then type
sudo /etc/init.d/vpnclient_init start (this starts the vpn "service" or what ever it is called)

then try to connect again..

You can add a icon to your desktop (Launcher) to do this for you.. Thats how I roll..


Hope this helps someone out there.

thanks!

mm

---

### Post by tlowery on 2008-10-17
Well, I had this working fine according to the directions in this thread. It's been working for several months until today when I installed the latest kernel and header updates from Ubuntu (2.6.24-21.27). Tonight when I ran

vpnclient_init start

I got a message that the kernel version specific modules directory didn't exist. I tried uninstalling the vpn package (vpn_uninstall), rebuilding the client, and reinstalling it (vpn_install).

I no longer get the message about the missing module directory when I run

vpnclient_init start

but I can't connect to my vpn server any more. When I run

vpnclient connect <myprofilename>

I get a message about failure to resolve host. I can ping the hostname, so I tried modifying the profile using the resulting IP address as the host. In that case when I try to connect I don't get the "failure to resolve" message, but the connect is closed by the local client.

Has anyone else had this problem? Any suggestions on how to resolve it?

Thanks in advance!

---

### Post by wired98 on 2008-10-18
Hi,

no suggestions, but I have exactly the same issue. Plus, I need this vpn connection for my work and this work has to be finished really soon (TM).

Somebody?

---

### Post by wired98 on 2008-10-18
I found the solution, somehow I had not the newest version of the cisco vpnclient. My version was

4.8.01.0640

and the newest version would be

4.8.02.0030 

and as written in the wiki of the German ubuntu community ([http://wiki.ubuntuusers.de/](http://wiki.ubuntuusers.de/)), you can download the latest version on the websites of Universität Konstanz:

[http://cms.uni-konstanz.de/index.php?id=90/](http://cms.uni-konstanz.de/index.php?id=90/)

Hope this also works for you. Good luck!

---

### Post by tlowery on 2008-10-18
> **wired98 said:**
> I found the solution, somehow I had not the newest version of the cisco vpnclient. My version was

4.8.01.0640

and the newest version would be

4.8.02.0030 

and as written in the wiki of the German ubuntu community ([http://wiki.ubuntuusers.de/](http://wiki.ubuntuusers.de/)), you can download the latest version on the websites of Universität Konstanz:

[http://cms.uni-konstanz.de/index.php?id=90/](http://cms.uni-konstanz.de/index.php?id=90/)

Hope this also works for you. Good luck!


The latest stable build on that site is 4.8.00.0490(rev1).  Is that the build you got to work?  Or did you download the "k9" build?  I'm already running version 4.8.01 (0640).  That's the version causing me the problem.

Thanks.

Tim

---

### Post by tlowery on 2008-10-18
Sorry, misread your post.  I'll try 4.8.02.

Thanks again!

Tim

---

### Post by tlowery on 2008-10-18
> **wired98 said:**
> I found the solution, somehow I had not the newest version of the cisco vpnclient. My version was

4.8.01.0640

and the newest version would be

4.8.02.0030 

and as written in the wiki of the German ubuntu community ([http://wiki.ubuntuusers.de/](http://wiki.ubuntuusers.de/)), you can download the latest version on the websites of Universität Konstanz:

[http://cms.uni-konstanz.de/index.php?id=90/](http://cms.uni-konstanz.de/index.php?id=90/)

Hope this also works for you. Good luck!


This suggestion worked great!

Thanks very much for your help.

Tim

---


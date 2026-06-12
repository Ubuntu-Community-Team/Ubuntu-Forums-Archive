---
title: "EEE PC 1000 with Jaunty - hardware problems"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kay_rus on 2009-04-14
**[COLOR="Red"]First of all[/COLOR]** it is impossible to install the eeepc-acpi-scripts:

```
apt-get install eeepc-acpi-scripts -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  eeepc-acpi-scripts: Depends: acpi-support-base but it is not installable
E: Broken packages
```

**[COLOR="#ff0000"]Secondly[/COLOR]**, it is impossible to turn on the Bluetooth. When I push Fn + Wireless buttons, the WiFi adapter is turning off. Also after it is impossible to turn it on. You need to reboot to activate the WiFi driver.

**[COLOR="#ff0000"]Thirdly[/COLOR]**, Camera doesn't work (maybe because it is impossible to turn it on via ACPI).

I have upgraded from the Ubuntu Intrepid with [www.array.org](www.array.org) kernel, wher ehardware worked perfectly.

The only positive moment is fast suspend/resume =)

I thought that Ubuntu Janty is the best Linux Distributive for netbooks. Well, I had not to upgrade to Jaunty from Intrepid with array.org kernel... or Not?

Look forward to your replies =)

---

### Post by snowpine on 2009-04-14
Hi, can you post the contents of your /etc/apt/sources.list file? My guess is that you still have an Intrepid repository in there; everything should be Jaunty. :)

I do not know if the various array.org eee projects have been released for Jaunty yet. You may have to wait a little bit until Jaunty is released and array.org can catch up.

---

### Post by kay_rus on 2009-04-14
Be sure, its ok =)

```
deb http://archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-backports restricted main multiverse universe
#deb http://ppa.launchpad.net/netbook-remix-team/ubuntu jaunty main
deb http://ppa.launchpad.net/synce/ubuntu jaunty main
deb http://ppa.launchpad.net/blueman/ppa/ubuntu jaunty main
```

---

### Post by snowpine on 2009-04-14
Your list looks good. I just tried to install the package myself and got the same error.

I guess eeepc-acpi-scripts is just not ready yet... Jaunty is beta software you know. :)

---

### Post by kay_rus on 2009-04-14
> **snowpine said:**
> Your list looks good. I just tried to install the package myself and got the same error.

I guess eeepc-acpi-scripts is just not ready yet... Jaunty is beta software you know. :)
I hope my post will speed up the eeepc bugfixing before the release :)

---

### Post by snowpine on 2009-04-14
> **kay_rus said:**
> I hope my post will speed up the eeepc bugfixing before the release :)

I promise you the developers working on the Jaunty release are way too busy to read these forums. :)

Here is information on how to report bugs: [http://mdzlog.alcor.net/2009/03/31/please-dont-report-ubuntu-bugs-directly-to-launchpad/](http://mdzlog.alcor.net/2009/03/31/please-dont-report-ubuntu-bugs-directly-to-launchpad/)

---

### Post by ahbart on 2009-04-14
In the meantime you could have a look at this script: [Link](http://forum.eeeuser.com/viewtopic.php?id=65606). It works very well on my 901 with Jaunty.

---

### Post by kay_rus on 2009-04-14
> **ahbart said:**
> In the meantime you could have a look at this script: [Link](http://forum.eeeuser.com/viewtopic.php?id=65606). It works very well on my 901 with Jaunty.
bluetooth switch doesn't work there too.

---

### Post by ahbart on 2009-04-14
Yes it does with 2.6.29 kernel.

---

### Post by kay_rus on 2009-04-14
> **ahbart said:**
> Yes it does with 2.6.29 kernel.

where should I find the precompiled 2.6.29 kernel?

---

### Post by ahbart on 2009-04-14
Source Elmurato's: [link](http://www.informatik.uni-bremen.de/~elmurato/EeePC/)
You'll need the headers and the image.

---

### Post by kay_rus on 2009-04-14
> **ahbart said:**
> Source Elmurato's: [link](http://www.informatik.uni-bremen.de/~elmurato/EeePC/)
You'll need the headers and the image.

thanks

---

### Post by kay_rus on 2009-04-14
> **ahbart said:**
> Source Elmurato's: [link](http://www.informatik.uni-bremen.de/~elmurato/EeePC/)
You'll need the headers and the image.

is there an image source to install the dkms?

---

### Post by dawnlove on 2009-04-14
Did you turn bluetooth and camera on in the bios?

---

### Post by ahbart on 2009-04-14
I do not fully understand what you want with the dkms image source?
You have to install:
- [linux-headers](http://www.informatik.uni-bremen.de/~elmurato/EeePC/linux-headers-2.6.29.1-3e.deb)
- [linux-image](http://www.informatik.uni-bremen.de/~elmurato/EeePC/linux-image-2.6.29.1-3e.deb)
The asus_eee dkms package is part of the tar ball, but you can download it seperately: [here](http://www.informatik.uni-bremen.de/~elmurato/EeePC/asus-eee-dkms_3.0_all.deb)
all three are deb files.
If you download them in a separated directory/folder you can go to that folder in a terminal and type/paste:
```
sudo dpkg -i *.deb
```
After installing the [Elmurato script](http://forum.eeeuser.com/viewtopic.php?id=65606) it should work all (including bluetooth).

---

### Post by kay_rus on 2009-04-15
> **ahbart said:**
> I do not fully understand what you want with the dkms image source?
You have to install:
- [linux-headers](http://www.informatik.uni-bremen.de/~elmurato/EeePC/linux-headers-2.6.29.1-3e.deb)
- [linux-image](http://www.informatik.uni-bremen.de/~elmurato/EeePC/linux-image-2.6.29.1-3e.deb)
The asus_eee dkms package is part of the tar ball, but you can download it seperately: [here](http://www.informatik.uni-bremen.de/~elmurato/EeePC/asus-eee-dkms_3.0_all.deb)
all three are deb files.
If you download them in a separated directory/folder you can go to that folder in a terminal and type/paste:
```
sudo dpkg -i *.deb
```
After installing the [Elmurato script](http://forum.eeeuser.com/viewtopic.php?id=65606) it should work all (including bluetooth).

I mean, that when I have installed the 2.6.29.1-3e kernel, the dkms could not be installed, as it requires kernel source.

I have downloaded the kernel source from kernel.ubuntu.com, installed it, but it didn't help

---

### Post by kay_rus on 2009-04-15
> **dawnlove said:**
> Did you turn bluetooth and camera on in the bios?
actually I don't want to turn devices from bios, I would like to make it using user keys, as it worked in array.org kernel.

---

### Post by dirtylobster on 2009-04-15
What's your BIOS version? Bluetooth and Webcam work fine with the standard 9.04 kernel (2.6.28-11) on my 1000H.

---

### Post by ahbart on 2009-04-15
> **kay_rus said:**
> I mean, that when I have installed the 2.6.29.1-3e kernel, the dkms could not be installed, as it requires kernel source.

I have downloaded the kernel source from kernel.ubuntu.com, installed it, but it didn't help
Strange, because you do not actually require kernel source for it. The headers will do. Are you sure everything was installed? Did you do a reboot with this new kernel, because sometimes dkms does it's work at boot time with the new kernel.
If you booted your 2.6.28 kernel, and have no headers installed for that kernel, you will get a fail/error over there.

---

### Post by ahbart on 2009-04-15
> **dirtylobster said:**
> What's your BIOS version? Bluetooth and Webcam work fine with the standard 9.04 kernel (2.6.28-11) on my 1000H.
Well that's special, because most people are having trouble switching bluetooth off and on with that kernel. (Especially the on part).

---

### Post by dirtylobster on 2009-04-15
I probably can't shut them off but they work fine otherwise. OP's problem was not being able to shut them down IIRC.

---

### Post by kay_rus on 2009-04-15
> **dirtylobster said:**
> I probably can't shut them off but they work fine otherwise. OP's problem was not being able to shut them down IIRC.

I mean I can turn on/off them in BIOS, bu I can not turn on/off them in Linux using userkeys.

---

### Post by kay_rus on 2009-04-15
> **# file /usr/src/linux-headers-2.6.29.1-3e/**
/usr/src/linux-headers-2.6.29.1-3e/: directory
**# uname -a**
Linux kay-eee 2.6.29.1-3e #1 SMP Sun Apr 5 21:02:55 CEST 2009 i686 GNU/Linux
**# dpkg -i asus-eee-dkms_3.0_all.deb **
(Reading database ... 125549 files and directories currently installed.)
Preparing to replace asus-eee-dkms 3.0 (using asus-eee-dkms_3.0_all.deb) ...

-------- Uninstall Beginning --------
Module:  asus_eee
Version: 3.0
Kernel:  2.6.27-7-generic (i686)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod....(bad exit status: 1)

DKMS: uninstall Completed.

------------------------------
Deleting module version: 3.0
completely from the DKMS tree.
------------------------------
Done.
Unpacking replacement asus-eee-dkms ...
Removing old module source...
Setting up asus-eee-dkms (3.0) ...
Loading new asus_eee-3.0 DKMS files...

Loading tarball for module: asus_eee / version: 3.0

Loading /usr/src/asus_eee-3.0...
Loading /var/lib/dkms/asus_eee/3.0/2.6.27-7-generic/i686...
Creating /var/lib/dkms/asus_eee/3.0/source symlink...

DKMS: ldtarball Completed.
Installing prebuilt kernel module binaries (if any)
Trying kernel: 2.6.27-7-generic

Error! The directory /lib/modules/2.6.27-7-generic doesn't exist.
You cannot install a module onto a non-existant kernel.

Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.


The module is precompiled for 2.6.27 kernel. You can see it in deb package:
> find dkms
dkms
dkms/dkms_main_tree
dkms/dkms_main_tree/dkms_dbversion
dkms/dkms_main_tree/2.6.27-7-generic
dkms/dkms_main_tree/2.6.27-7-generic/i686
dkms/dkms_main_tree/2.6.27-7-generic/i686/log
dkms/dkms_main_tree/2.6.27-7-generic/i686/log/make.log
dkms/dkms_main_tree/2.6.27-7-generic/i686/module
dkms/dkms_main_tree/2.6.27-7-generic/i686/module/asus_eee.ko
dkms/dkms_source_tree
dkms/dkms_source_tree/dkms.conf
dkms/dkms_source_tree/Makefile
dkms/dkms_source_tree/asus_eee.c~
dkms/dkms_source_tree/asus_eee.c

and it can not be compiled for 2.6.29.1:
> make
make: nothing to be done for 'patch'.
make[1]: Entering directory `/root/Jaunty_Eeeasy-Scripts/dkms/dkms_source_tree'
cd /lib/modules/2.6.29.1-3e/build && make -C /lib/modules/2.6.29.1-3e/build M=/root/Jaunty_Eeeasy-Scripts/dkms/dkms_source_tree modules
make[2]: Entering directory `/lib/modules/2.6.29.1-3e/build'
make[2]: *** No rule to make target `modules'.  Stop.
make[2]: Leaving directory `/lib/modules/2.6.29.1-3e/build'
make[1]: *** [generic] Error 2
make[1]: Leaving directory `/root/Jaunty_Eeeasy-Scripts/dkms/dkms_source_tree'
make: *** [asus_eee.o] Error 2

---

### Post by ahbart on 2009-04-15
I'm not sure, but try to install 'build-essentials'

---

### Post by kay_rus on 2009-04-15
> **ahbart said:**
> I'm not sure, but try to install 'build-essentials'
I have installed it, but nothing changed. Same error:

> **# apt-get install build-essential**
bla-bla-bla
**dkms_source_tree# make**
make: nothing to be done for 'patch'.
make[1]: Entering directory `/root/Jaunty_Eeeasy-Scripts/dkms/dkms_source_tree'
cd /lib/modules/2.6.29.1-3e/build && make -C /lib/modules/2.6.29.1-3e/build M=/root/Jaunty_Eeeasy-Scripts/dkms/dkms_source_tree modules
make[2]: Entering directory `/lib/modules/2.6.29.1-3e/build'
make[2]: *** No rule to make target `modules'.  Stop.
make[2]: Leaving directory `/lib/modules/2.6.29.1-3e/build'
make[1]: *** [generic] Error 2
make[1]: Leaving directory `/root/Jaunty_Eeeasy-Scripts/dkms/dkms_source_tree'
make: *** [asus_eee.o] Error 2


---


---
title: "upgrade:   'sudo dpkg --configure  -a'?"
date: 2018-07-23
forum: Installation &amp; Upgrades
---

### Post by adisinambela on 2018-07-23
I got Dual boot mode in my laptop that is (Windows 10 and Ubuntu 18.04) I have a problem with my  terminal, where when I want to upgrade I see  "E: dpkg was interrupted,  you must manually run 'sudo dpkg --configure  -a' to correct the  problem." and when the command I have run I stop  in  "Building initial module for 4.15.0-24-generic" and not running again   just blinking, please help friends ...


```
adi_sinambela@adisinambela:~$ sudo apt update
[sudo] password for adi_sinambela: 
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease              
Hit:2 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic InRelease    
Hit:3 [http://packages.microsoft.com/repos/vscode](http://packages.microsoft.com/repos/vscode) stable InRelease              
Hit:4 [http://id.archive.ubuntu.com/ubuntu](http://id.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:5 [http://id.archive.ubuntu.com/ubuntu](http://id.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:6 [http://id.archive.ubuntu.com/ubuntu](http://id.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
3 packages can be upgraded. Run 'apt list --upgradable' to see them.
adi_sinambela@adisinambela:~$ sudo apt full-upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
adi_sinambela@adisinambela:~$ sudo dpkg --configure -a
Processing triggers for initramfs-tools (0.130ubuntu3.1) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-24-generic
Setting up nvidia-dkms-390 (390.77-0ubuntu0~gpu18.04.1) ...
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia
DEBUG:razz:arsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:razz:arsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:razz:arsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
Removing old nvidia-390.77 DKMS files...

-------- Uninstall Beginning --------
Module:  nvidia
Version: 390.77
Kernel:  4.15.0-24-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod...

DKMS: uninstall completed.

------------------------------
Deleting module version: 390.77
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-390.77 DKMS files...
Building for 4.15.0-24-generic
Building for architecture x86_64
Building initial module for 4.15.0-24-generic
```

'STUCK HERE

---

### Post by ubfan1 on 2018-07-23
I don't think you need the graphics-drivers ppa for the 390 nvidia driver.  Try removing that ,. do the update and try again.

---

### Post by adisinambela on 2018-07-23
> **ubfan1 said:**
> I don't think you need the graphics-drivers ppa for the 390 nvidia driver.  Try removing that ,. do the update and try again.

how to removing it bro ?

 i dont have idea, please give me a instruction ...

---

### Post by ubfan1 on 2018-07-23
Try the command in a terminal (see more details in the manual page with  the command   man ppa-purge):
sudo ppa-purge -o graphics-drivers
Or just edit the /etc/apt/sources.list file and either remove the graphics-drivers line(s), or comment them out with a #

---


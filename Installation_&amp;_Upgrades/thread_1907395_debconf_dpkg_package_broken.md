---
title: "debconf dpkg package broken"
date: 2012-01-11
forum: Installation &amp; Upgrades
---

### Post by candidoaramburu on 2012-01-11
Hi,



I dont know how to install debconf package on ubuntu LTS 10.04:

************FRAMEWORK*************
root@izar:/home/candido# uname -a
Linux izar 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011 i686 GNU/Linux


***********ERROR  MESSAGES:*****************
root@izar:/home/candido# aptitude install debconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  intltool-debian{u} libjiu-java{u} libjlibeps-java{u} libswt-cairo-gtk-3.5-jni{u} libswt-gnome-gtk-3.5-jni{u} libswt-gtk-3.5-java{u} libswt-gtk-3.5-jni{u} 
  libswt-mozilla-gtk-3.5-jni{u} nvidia-173-modaliases{u} nvidia-96-modaliases{u} nvidia-current-modaliases{u} po-debconf{u} 
The following partially installed packages will be configured:
  debconf 
0 packages upgraded, 0 newly installed, 12 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 4,411kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Setting up debconf (1.5.28ubuntu4) ...
**dpkg: error processing debconf (--configure):**
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 debconf
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up debconf (1.5.28ubuntu4) ...
dpkg: error processing debconf (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 debconf
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done


**************QUESTIONS**********
¿recursive installation?
¿debconf installation it is needed debconf?


thanks
Candido

---

### Post by cortman on 2012-01-11
```
sudo apt-get install -f
```

should fix broken packages.

---

### Post by candidoaramburu on 2012-01-11
when i try install or upgrade some package the error is about running some subprocess of debconf manager, so it is posible that other dependent package fail, i think that i need reinstall ESSENTIAL package but this action need total carefully, i suppose, because i can not remove debconf package

candido@izar:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  intltool-debian libswt-cairo-gtk-3.5-jni libswt-gtk-3.5-jni libswt-mozilla-gtk-3.5-jni po-debconf libjlibeps-java libjiu-java nvidia-current-modaliases
  nvidia-173-modaliases libswt-gnome-gtk-3.5-jni libswt-gtk-3.5-java nvidia-96-modaliases
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up debconf (1.5.28ubuntu4) ...
**dpkg: error processing debconf (--configure):**
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 debconf
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by candidoaramburu on 2012-01-11
A clue for REINSTALL dpkg low level manager :

[http://people.adams.edu/~cdmiller/posts/Ubuntu-dpkg-recovery/](http://people.adams.edu/~cdmiller/posts/Ubuntu-dpkg-recovery/)

.... it need understand and test it before field running  ... before panic warning

Somebody guarantee it?

Cándido

---

### Post by Buntumatic on 2012-01-11
Me thinks debconf is part of any .deb install, thus it is needed to install anything ... even debconf.
My advice is to unpack correct version of debconf deb by hand and manually copy the binary into system.

---

### Post by candidoaramburu on 2012-02-06
Hi, my system still broken. All begun, i think, with kernel update
2.6.32-36.79 version. I have tried recover the corrupted system first
with Synaptic manager and after manually and i dont get
success, i have remove /var/lib/dpkg/info/sysv-rc.* files and now i
can not recover it.

The prompt of different commands are:

0->$ uname -a ; dpkg --list  | grep linux-image
Linux izar 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux
ii  linux-image-2.6.32-36-generic                 2.6.32-36.79                                    Linux kernel image for version 2.6.32 on x86/x86_64
iF  linux-image-2.6.32-38-generic                 2.6.32-38.83                                    Linux kernel image for version 2.6.32 on x86/x86_64


1-> $dpkg --audit
The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 sysv-rc              System-V-like runlevel change mechanism
 linux-image-2.6.32-38-generic Linux kernel image for version 2.6.32 on x86/x86
 xserver-xorg         the X.Org X server
 linux-headers-2.6.32-38-generic Linux kernel headers for version 2.6.32 on x86


2-> $sudo dpkg --configure sysv-rc
[sudo] password for candido: 
Setting up sysv-rc (2.87dsf-4ubuntu17.5) ...
dpkg: error processing sysv-rc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 sysv-rc


3-> $sudo apt-get install --reinstall sysv-rc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dctrl-tools dlocate
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 3 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.32-38-generic (2.6.32-38.83) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-38-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: (hd0,2)/boot/grub/splashimages/debblue.xpm.gz

Found kernel: /boot/vmlinuz-2.6.32-38-generic
Found kernel: /boot/vmlinuz-2.6.32-36-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-38-generic /boot/vmlinuz-2.6.32-38-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-38-generic /boot/vmlinuz-2.6.32-38-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-38-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-38-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up sysv-rc (2.87dsf-4ubuntu17.5) ...
dpkg: error processing sysv-rc (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-headers-2.6.32-38-generic (2.6.32-38.83) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-38-generic /boot/vmlinuz-2.6.32-38-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-38-generic /boot/vmlinuz-2.6.32-38-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-38-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-38-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up xserver-xorg (1:7.5+5ubuntu1.1) ...
dpkg: error processing xserver-xorg (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.32-38-generic
 sysv-rc
 linux-headers-2.6.32-38-generic
 xserver-xorg
E: Sub-process /usr/bin/dpkg returned an error code (1)

---


---
title: "[xubuntu 11] Installation error - depmod error"
date: 2012-04-17
forum: Installation &amp; Upgrades
---

### Post by Fuhai_Modulo on 2012-04-17
hello I am still new to ubuntu and i need help because I am pretty sure that there are others that is having the same trouble on other Ubuntu Distrobutions. I did a fresh install of Xubuntu on my laptop. My laptop is a Dell Latutude d400. I ran the update manager that prompted me to do an update. Now @ the end of the up date i get an error code saying that it couldn't delet certain items. Then after hitting ok, I tried downloading and installing 'nmap' but I got this error code instead:

```
 username@computer_name:~$ sudo apt-get install nmap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nmap
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 1,623 kB of archives.
After this operation, 7,234 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric/main nmap i386 5.21-1.1 [1,623 kB]
Fetched 1,623 kB in 2s (580 kB/s) 
Selecting previously deselected package nmap.
(Reading database ... 159521 files and directories currently installed.)
Unpacking nmap (from .../nmap_5.21-1.1_i386.deb) ...
Processing triggers for man-db ...
Setting up linux-image-3.0.0-17-generic (3.0.0-17.30) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-3.0.0-17-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-17-generic; however:
  Package linux-image-3.0.0-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.0.0.17.20); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up nmap (5.21-1.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
      No apport report written because the error message indicates its a followup error from a previous failure.
            Errors were encountered while processing:
 linux-image-3.0.0-17-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
```

Now I have gotten suggetions to remove older kernel versions which they are present. here is my current: 
```
3.0.0-12-generic
```

and here is what i have under command dpkg:

```
 battlec@battlec-Latitude-D400:~$ dpkg -l linux-*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                Version             Description
+++-===================-===================-======================================================
un  linux-doc-3.0.0     <none>              (no description available)
ii  linux-firmware      1.60                Firmware for Linux kernel drivers
iU  linux-generic       3.0.0.17.20         Complete Generic Linux kernel
un  linux-headers       <none>              (no description available)
un  linux-headers-3     <none>              (no description available)
un  linux-headers-3.0   <none>              (no description available)
ii  linux-headers-3.0.0 3.0.0-12.20         Header files related to Linux kernel version 3.0.0
ii  linux-headers-3.0.0 3.0.0-12.20         Linux kernel headers for version 3.0.0 on x86/x86_64
ii  linux-headers-3.0.0 3.0.0-17.30         Header files related to Linux kernel version 3.0.0
ii  linux-headers-3.0.0 3.0.0-17.30         Linux kernel headers for version 3.0.0 on x86/x86_64
ii  linux-headers-gener 3.0.0.17.20         Generic Linux kernel headers
un  linux-image         <none>              (no description available)
un  linux-image-3.0     <none>              (no description available)
rc  linux-image-3.0.0-1 3.0.0-12.20         Linux kernel image for version 3.0.0 on x86/x86_64
iF  linux-image-3.0.0-1 3.0.0-17.30         Linux kernel image for version 3.0.0 on x86/x86_64
iU  linux-image-generic 3.0.0.17.20         Generic Linux kernel image
un  linux-initramfs-too <none>              (no description available)
un  linux-kernel-header <none>              (no description available)
un  linux-kernel-log-da <none>              (no description available)
ii  linux-libc-dev      3.0.0-17.30         Linux Kernel Headers for development
un  linux-restricted-co <none>              (no description available)
ii  linux-sound-base    1.0.24+dfsg-0ubuntu base package for ALSA and OSS sound systems
un  linux-source-3.0.0  <none>              (no description available)
un  linux-tools         <none>              (no description available) 
```

trying to run synaptic or apt-get there is no avail and i get the same error massage. May I please get some help on this matter please.

Much appriciated

---

### Post by Helge on 2012-04-17
I have the same problem. Installed Ubuntu 11.10 on an USB memory stick, running from the same. The problem appeared when I upgraded the system today. I did not try to install nmap, but I have the same problem with the linux-image-3.0.0-17-generic. 
Sorry that I can't help, only confirm.

---


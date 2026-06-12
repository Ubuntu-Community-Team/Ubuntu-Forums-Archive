---
title: "xserver-xorg-core DPKG errors after 18.10 update"
date: 2018-10-27
forum: Installation &amp; Upgrades
---

### Post by notone2 on 2018-10-27
Tried purging it then installing it again, started happening after 18.10 update. Also have problems missing ttf-mscorefonts-installer and can't install it, tried via terminal, also downloaded ttf-mscorefonts-installer_3.7_all, tried via ubuntu software but nothing. 

```
notone@fieldless:~$ sudo apt-get install xserver-xorg-core[sudo] password for notone: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  xfonts-100dpi | xfonts-75dpi xfonts-scalable
The following NEW packages will be installed:
  xserver-xorg-core
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
Need to get 0 B/1333 kB of archives.
After this operation, 3990 kB of additional disk space will be used.
(Reading database ... 297178 files and directories currently installed.)
Preparing to unpack .../xserver-xorg-core_2%3a1.20.1-3ubuntu2_amd64.deb ...
Unpacking xserver-xorg-core (2:1.20.1-3ubuntu2) ...
Setting up keyboard-configuration (1.178ubuntu9) ...
Error loading new keyboard description
/usr/bin/ckbcomp: Can not find file "symbols/srp" in any known directory
dpkg: error processing package keyboard-configuration (--configure):
 installed keyboard-configuration package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on keyboard-configuration; however:
  Package keyboard-configuration is not configured yet.


dpkg: error processing package xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for man-db (2.8.4-2) ...
dpkg: dependency problems prevent configuration of console-setup-linux:
 console-setup-linux depends on keyboard-configuration (= 1.178ubuntu9); however:
  Package keyboard-configuration is not configured yet.


dpkg: error processing package console-setup-linux (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of console-setup:
 console-setup depends on console-setup-linux | console-setup-freebsd | hurd; however:
  Package console-setup-linux is not configured yet.
  Package console-setup-freebsd is not installed.
  Package hurd is not installed.
 console-setup depends on keyboard-configuration (= 1.178ubuntu9); however:
  Package keyboard-configuration is not configured yet.


dpkg: error processing package console-setup (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on console-setup; however:
  Package console-setup is not configured yet.


No apport report written because MaxReports is reached already
                                                              dpkg: error processing package ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 keyboard-configuration
 xserver-xorg-core
 console-setup-linux
 console-setup
 ubuntu-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)
notone@fieldless:~$
```

---

### Post by notone2 on 2018-10-27
Also tried > sudo dpkg --configure -a  and > sudo apt upgrade -f and > sudo apt autoremove but no joy

---

### Post by notone2 on 2018-10-28
When I restarted my computer mouse and keyboard were not working, I started GRUB, advance boot options, enabled networking and continue as a root, nothing worked purging, installing, it gave me configuration errors, only thing I could do was ```
sudo apt purge keyboard-configuration
``` and then I sucsesfull installed ```
sudo apt install xserver-xorg-input-all
``` and it works now

---


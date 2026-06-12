---
title: "gtkboard"
date: 2005-03-21
forum: Installation &amp; Upgrades
---

### Post by scott_b on 2005-03-21
I followed the instructions on upgrading from warty to hoary (change sources, update, dist-upgrade, reboot), but i can't seem to get x-window-system-core because of some error with gtkboard. please help. (install -f doesn't fix my problem either).

> swb@cha:~ $ sudo apt-get dist-upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
Calculating Upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up gtkboard (0.11pre0-3) ...
error in control file: `Format' value not specified at /usr/sbin/install-docs line 715, <IN> line 17.
dpkg: error processing gtkboard (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 gtkboard
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by scott_b on 2005-03-21
here are the results from dpkg --configure -a, and apt-get install x-window-system-core

> 
swb@cha:~ $ sudo apt-get install x-window-system-core
Reading Package Lists... Done
Building Dependency Tree... Done
x-window-system-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gtkboard (0.11pre0-3) ...
error in control file: `Format' value not specified at /usr/sbin/install-docs line 715, <IN> line 17.
dpkg: error processing gtkboard (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 gtkboard
E: Sub-process /usr/bin/dpkg returned an error code (1)
> swb@cha:~ $ sudo dpkg --configure -a
Setting up gtkboard (0.11pre0-3) ...
error in control file: `Format' value not specified at /usr/sbin/install-docs line 715, <IN> line 17.
dpkg: error processing gtkboard (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 gtkboard

---

### Post by RickSGM on 2005-05-22
I have that same thing too.  Don't know what to do about it.  :-?

---

### Post by simple on 2005-05-23
[QUOTE=RickSGM]I have that same thing too.  Don't know what to do about it.  :-?[/QUOTE]
 i had it too, i just removed "gtkboard" from synaptic, i think i got it from trying to install pacman...and t was getting that erorr whenever it'd try to install anything afterward, so yeah, look for gtkboard in synaptic

---


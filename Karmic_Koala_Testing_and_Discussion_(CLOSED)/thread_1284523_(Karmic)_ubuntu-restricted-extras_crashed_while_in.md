---
title: "(Karmic) ubuntu-restricted-extras crashed while installing"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Silwenae on 2009-10-06
Hi all,

I was trying to install ubuntu-restricted-extras when my session crashed.

I now can't uninstall, re-install or remove completely in Synaptic ubuntu-restricted-extras or any of the individual packages without getting an error.

Using Synaptic, if I reinstall, I get the error, and Synaptic thinks it's installed.  If I uninstall, I get the same error and Synaptic thinks it's uninstalled.

The error: 

E: sun-java6-bin: subprocess installed post-installation script returned error exit status 2
E: sun-java6-plugin: dependency problems - leaving unconfigured
E: ttf-liberation: subprocess installed post-installation script returned error exit status 2
E: ttf-mscorefonts-installer: subprocess installed post-installation script returned error exit status 2
E: unrar: subprocess installed post-installation script returned error exit status 2

Trying to do it via dpkg with one of the specific packages results in the same thing:
pcutler@sandman:~$ sudo dpkg --purge unrar
(Reading database ... 140202 files and directories currently installed.)
Removing unrar ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing unrar (--purge):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 unrar


This is my first time using Ubuntu in a few years, and any help is appreciated.

Thanks.

Paul

---

### Post by tommcd on 2009-10-07
Try this. Open a terminal and run:
```

sudo apt-get update
sudo apt-get-install -f
sudo dpkg --configure -a
sudo apt-get update

```
Then see if you can use synaptic to uninstall or reinstall whatever you want.

---

### Post by Silwenae on 2009-10-07
Thanks, unfortunately it fails on sudo apt-get install -f

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 50 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up sun-java6-bin (6-15-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing sun-java6-bin (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-15-1); however:
  Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Setting up ttf-liberation (1.05.1.20090721-0ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing ttf-liberation (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up ttf-mscorefonts-installer (3.0) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up unrar (1:3.9.3-1) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing unrar (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 sun-java6-bin
 sun-java6-plugin
 ttf-liberation
 ttf-mscorefonts-installer
 unrar
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by tommcd on 2009-10-08
First clean out your package list:
```
sudo apt-get clean
```
Then see if you can purge the affected packages:
```
sudo apt-get remove --purge sun-java6-bin
```
If that works then continue with the other affected packages.

---

### Post by oliwek on 2009-10-28
I had the same issue with : 
ttf-mscorefonts-installer
unrar
E: Sub-process /usr/bin/dpkg returned an error code (1)

it was caused by a slow internet connection, you have to manually edit the installer script (modify time values in it before it times out and close download sessions with sourceforge, cycle between mirrors, announces finally checksum mismatch and error 1), or use a faster connection 

hope it helps

---


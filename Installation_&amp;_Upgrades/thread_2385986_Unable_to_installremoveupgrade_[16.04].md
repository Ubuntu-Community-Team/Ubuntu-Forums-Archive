---
title: "Unable to install/remove/upgrade [16.04]"
date: 2018-02-27
forum: Installation &amp; Upgrades
---

### Post by curious-ninja on 2018-02-27
When I try to install any software (e.g., sudo apt-get install sublime-text), the following error is thrown; for the same reason, I can't upgrade my system (Neither using *apt* or *Ubuntu Software*)

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  sublime-text
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
**12 not fully installed or removed**.
Need to get 9 670 B of archives.
After this operation, 51,2 kB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu xenial/main amd64 sublime-text all 2.0.2-1~webupd8~3 [9 670 B]
Fetched 9 670 B in 0s (147 kB/s)         
Preconfiguring packages ...
Setting up util-linux (2.27.1-6ubuntu3.3) ...
insserv: warning: script 'K01cups' missing LSB tags and overrides
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: There is a loop between service cups and grub-common if started
insserv:  loop involving service grub-common at depth 2
insserv:  loop involving service cups at depth 1
insserv:  loop involving service rsyslog at depth 1
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package util-linux (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 util-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

There are 12 packages that are either broken or half configured. So, when I run *"sudo dpkg --configure -a" *I get the following errors. The broken packages are listed at the end.

```
Setting up kmod (22-1ubuntu5) ...
insserv: warning: script 'K01cups' missing LSB tags and overrides
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: There is a loop between service cups and grub-common if started
insserv:  loop involving service grub-common at depth 2
insserv:  loop involving service cups at depth 1
insserv:  loop involving service rsyslog at depth 1
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package kmod (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of initramfs-tools-core:
 initramfs-tools-core depends on kmod | module-init-tools; however:
  Package kmod is not configured yet.
  Package module-init-tools is not installed.

dpkg: error processing package initramfs-tools-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-core (= 0.122ubuntu8.10); however:
  Package initramfs-tools-core is not configured yet.

dpkg: error processing package initramfs-tools (--configure):
 dependency problems - leaving unconfigured
Setting up rsync (3.1.1-3ubuntu1.1) ...
insserv: warning: script 'K01cups' missing LSB tags and overrides
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: There is a loop between service cups and grub-common if started
insserv:  loop involving service grub-common at depth 2
insserv:  loop involving service cups at depth 1
insserv:  loop involving service rsyslog at depth 1
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package rsync (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of udev:
 udev depends on util-linux (>= 2.27.1); however:
  Package util-linux is not configured yet.

dpkg: error processing package udev (--configure):
 dependency problems - leaving unconfigured
Setting up grub-common (2.02~beta2-36ubuntu3.15) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'K01cups' missing LSB tags and overrides
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: There is a loop between service cups and grub-common if started
insserv:  loop involving service grub-common at depth 2
insserv:  loop involving service cups at depth 1
insserv:  loop involving service rsyslog at depth 1
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package grub-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent processing triggers for systemd:
 systemd depends on util-linux (>= 2.27.1); however:
  Package util-linux is not configured yet.

dpkg: error processing package systemd (--configure):
 dependency problems - leaving triggers unprocessed
Setting up apport (2.20.1-0ubuntu2.15) ...
insserv: warning: script 'K01cups' missing LSB tags and overrides
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: There is a loop between service cups and grub-common if started
insserv:  loop involving service grub-common at depth 2
insserv:  loop involving service cups at depth 1
insserv:  loop involving service rsyslog at depth 1
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package apport (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bluez:
 bluez depends on kmod; however:
  Package kmod is not configured yet.
 bluez depends on udev (>= 170-1); however:
  Package udev is not configured yet.

dpkg: error processing package bluez (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-efi-amd64-bin:
 grub-efi-amd64-bin depends on grub-common (= 2.02~beta2-36ubuntu3.15); however:
  Package grub-common is not configured yet.

dpkg: error processing package grub-efi-amd64-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-efi-amd64:
 grub-efi-amd64 depends on grub-common (= 2.02~beta2-36ubuntu3.15); however:
  Package grub-common is not configured yet.
 grub-efi-amd64 depends on grub-efi-amd64-bin (= 2.02~beta2-36ubuntu3.15); however:
  Package grub-efi-amd64-bin is not configured yet.

dpkg: error processing package grub-efi-amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 2.02~beta2-36ubuntu3.15); however:
  Package grub-common is not configured yet.

dpkg: error processing package grub2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-efi-amd64-signed:
 grub-efi-amd64-signed depends on grub-efi-amd64 (= 2.02~beta2-36ubuntu3.15); however:
  Package grub-efi-amd64 is not configured yet.

dpkg: error processing package grub-efi-amd64-signed (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kmod
 initramfs-tools-core
 initramfs-tools
 rsync
 udev
 grub-common
 systemd
 apport
 bluez
 grub-efi-amd64-bin
 grub-efi-amd64
 grub2-common
 apport-gtk
 grub-efi-amd64-signed
```

I have tried many suggestions from other posts but all in vain. Neither can I forcefully remove those 12 packages  (since they have severe dependencies) nor could I forcefully reinstall (e.g., until.linux) from manually downloading the *.deb file.
 
The following commands output more or less the same errros as above:

```
sudo apt-get install -f

sudo apt-get remove <program>

sudo apt-get autoremove

sudo dpkg --remove --force-remove-reinstreq <package>

sudo apt-get update && sudo apt-get upgrade 
```

I also checked the file "*/var/lib/dpkg/status*" , where the status of all the 12 broken packages is either of the following:

> Status: deinstall ok half-configured
Status: deinstall ok unpacked
Status: deinstall ok config-files
Status: install ok unpacked 

For non-problematic packages, it is > Status: install ok installed

I have no clue why my system ended up being like this. Any suggestions to fix this would be highly appreciated!

---

### Post by kerry_s on 2018-02-27
sudo apt clean
sudo apt update && sudo apt full-upgrade

---

### Post by curious-ninja on 2018-02-27
As I have already mentioned before, install/upgrade throw the same error (1st code). I have tried all possible clean/purge operations. None are helping. Now I am almost certain that broken/half-configured packages are creating the problem. Any suggestions in that direction would be helpful.

---

### Post by QIII on 2018-02-27
How many other PPAs are you using?  Do you have any backport or proposed repos active?

---

### Post by curious-ninja on 2018-02-28
I have attached the screenshot of PPAs I am using. And also my backport is active. Moreover, when I try to update or upgrade (using terminal or software centre), all the packages are downloaded from repos. And the errors are thrown while installing. It's something to do with half-configured packages that are displayed as part of the error.

---

### Post by kc1di on 2018-02-28
try this command ```
sudo dpkg --configure -a
```
if that does not work try this : ```
sudo rm /var/lib/apt/lists/*
```
then do  ```
sudo apt update
```

---

### Post by curious-ninja on 2018-02-28
I have already posted the error for "sudo dpkg --configure -a" in my initial post (code snippet 2). "sudo rm /var/lib/apt/lists/*" and "sudo apt update" aren't doing any help. This is what I get (again) after the two commands.

```
Get:1 [http://ppa.launchpad.net/jfi/ppa/ubuntu](http://ppa.launchpad.net/jfi/ppa/ubuntu) xenial InRelease [17,5 kB]
Ign:2 [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) wily InRelease                                                                           
Get:3 [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) wily Release [6 596 B]                                                                   
Ign:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                   
Get:5 [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) wily Release.gpg [473 B]                                                                 
Get:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release [1 189 B]                                                           
Get:7 [http://ppa.launchpad.net/kasra-mp/ubuntu-indicator-weather/ubuntu](http://ppa.launchpad.net/kasra-mp/ubuntu-indicator-weather/ubuntu) xenial InRelease [18,1 kB]                             
Get:8 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release.gpg [819 B]                                                         
Get:9 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) xenial InRelease [17,5 kB]                                          
Get:10 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease [4 487 B]                                                                   
Get:11 [https://deb.nodesource.com/node_4.x](https://deb.nodesource.com/node_4.x) xenial InRelease [4 646 B]                            
Get:12 [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) xenial InRelease [17,5 kB]                                      
Get:13 [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) wily/main i386 Packages [1 104 B]                                                       
Get:14 [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) wily/main amd64 Packages [1 092 B]                                                      
Get:15 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease [11,5 kB]                                                          
Get:16 [http://ppa.launchpad.net/webupd8team/atom/ubuntu](http://ppa.launchpad.net/webupd8team/atom/ubuntu) xenial InRelease [17,5 kB]                                             
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease [247 kB]                                
Get:18 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial InRelease [17,5 kB]                 
Get:19 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable/main amd64 Packages [1 403 B]                                              
Get:20 [http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu](http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu) xenial InRelease [17,6 kB]                                   
Get:21 [http://ppa.launchpad.net/jfi/ppa/ubuntu](http://ppa.launchpad.net/jfi/ppa/ubuntu) xenial/main amd64 Packages [1 028 B]                             
Get:22 [http://ppa.launchpad.net/jfi/ppa/ubuntu](http://ppa.launchpad.net/jfi/ppa/ubuntu) xenial/main i386 Packages [1 028 B]                               
Get:23 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable/main amd64 Packages [2 261 B]                                                         
Get:24 [http://ppa.launchpad.net/jfi/ppa/ubuntu](http://ppa.launchpad.net/jfi/ppa/ubuntu) xenial/main Translation-en [756 B]                                        
Get:25 [http://ppa.launchpad.net/kasra-mp/ubuntu-indicator-weather/ubuntu](http://ppa.launchpad.net/kasra-mp/ubuntu-indicator-weather/ubuntu) xenial/main amd64 Packages [532 B]                    
Get:26 [https://deb.nodesource.com/node_4.x](https://deb.nodesource.com/node_4.x) xenial/main Sources [762 B]                                                         
Get:27 [http://ppa.launchpad.net/kasra-mp/ubuntu-indicator-weather/ubuntu](http://ppa.launchpad.net/kasra-mp/ubuntu-indicator-weather/ubuntu) xenial/main i386 Packages [532 B]          
Get:28 [https://deb.nodesource.com/node_4.x](https://deb.nodesource.com/node_4.x) xenial/main amd64 Packages [1 003 B]                                                
Get:29 [https://deb.nodesource.com/node_4.x](https://deb.nodesource.com/node_4.x) xenial/main i386 Packages [1 005 B]                                                 
Get:30 [http://ppa.launchpad.net/kasra-mp/ubuntu-indicator-weather/ubuntu](http://ppa.launchpad.net/kasra-mp/ubuntu-indicator-weather/ubuntu) xenial/main Translation-en [332 B]                    
Get:31 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) xenial/main amd64 Packages [42,7 kB]                               
Get:32 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) xenial/main i386 Packages [42,6 kB]                                
Get:33 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) xenial/main Translation-en [26,3 kB]                             
Get:34 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial/partner amd64 Packages [3 128 B]                   
Get:35 [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) xenial/main amd64 Packages [3 092 B]                            
Get:36 [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) xenial/main i386 Packages [3 092 B]                           
Get:37 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial/partner i386 Packages [3 124 B]                                            
Get:38 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial/partner Translation-en [1 616 B]                  
Get:39 [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) xenial/main Translation-en [1 828 B]
Get:40 [http://ppa.launchpad.net/webupd8team/atom/ubuntu](http://ppa.launchpad.net/webupd8team/atom/ubuntu) xenial/main amd64 Packages [624 B]                  
Get:41 [http://ppa.launchpad.net/webupd8team/atom/ubuntu](http://ppa.launchpad.net/webupd8team/atom/ubuntu) xenial/main i386 Packages [624 B]             
Get:42 [http://ppa.launchpad.net/webupd8team/atom/ubuntu](http://ppa.launchpad.net/webupd8team/atom/ubuntu) xenial/main Translation-en [332 B]        
Get:43 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial/main amd64 Packages [2 908 B]            
Get:44 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages [1 201 kB]
Get:45 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial/main i386 Packages [2 460 B]                       
Get:46 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial/main Translation-en [1 260 B]                  
Get:47 [http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu](http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu) xenial/main amd64 Packages [455 B]                
Get:48 [http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu](http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu) xenial/main i386 Packages [455 B]           
Get:49 [http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu](http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu) xenial/main Translation-en [224 B]          
Get:50 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 Packages [1 196 kB]       
Get:51 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main Translation-en [568 kB]
Get:52 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 DEP-11 Metadata [733 kB]
Get:53 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main DEP-11 64x64 Icons [409 kB]
Get:54 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages [7 532 kB]
Get:55 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe i386 Packages [7 512 kB]
Get:56 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe Translation-en [4 354 kB]
Get:57 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 DEP-11 Metadata [3 410 kB]
Get:58 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe DEP-11 64x64 Icons [7 448 kB]
Get:59 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/restricted amd64 Packages [8 344 B]
Get:60 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/restricted i386 Packages [8 684 B]
Get:61 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/restricted Translation-en [2 908 B]
Get:62 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/restricted amd64 DEP-11 Metadata [186 B]
Get:63 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/multiverse amd64 Packages [144 kB]
Get:64 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/multiverse i386 Packages [140 kB]
Get:65 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/multiverse Translation-en [106 kB]
Get:66 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/multiverse amd64 DEP-11 Metadata [63,8 kB]
Get:67 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/multiverse DEP-11 64x64 Icons [230 kB]
Fetched 35,6 MB in 4s (7 512 kB/s)                            
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  rlwrap
Use 'sudo apt autoremove' to remove it.
The following packages have been kept back:
  indicator-weather
The following packages will be upgraded:
  adobe-flash-properties-gtk adobe-flashplugin atom google-chrome-stable nodejs oracle-java8-installer
  oracle-java8-set-default skypeforlinux
8 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
12 not fully installed or removed.
Need to get 0 B/229 MB of archives.
After this operation, 1 891 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Preconfiguring packages ...
Setting up util-linux (2.27.1-6ubuntu3.3) ...
insserv: warning: script 'K01cups' missing LSB tags and overrides
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: There is a loop between service cups and grub-common if started
insserv:  loop involving service grub-common at depth 2
insserv:  loop involving service cups at depth 1
insserv:  loop involving service rsyslog at depth 1
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package util-linux (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 util-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by vasa1 on 2018-02-28
When posting terminal output or config files or system files, please use code tags instead of quote tags.

---

### Post by kc1di on 2018-02-28
one thing that stands out in your update list as a listing for a wily release, What is that?
please give us a look at your regular repository list as well as the ppa's .

first I would go to all my ppa's and uncheck them then try to do an update if that works go reintroduce the ppa's one at a time until one breaks the update process 
if it does that's the culprit remove it.

---

### Post by vasa1 on 2018-02-28
Do you have *aptitude* installed? There's a chance *aptitude* can fix things for you.

---

### Post by curious-ninja on 2018-02-28
Actually, the "sudo apt-get update" works fine with the below output.

```
Ign:1 http://linux.dropbox.com/ubuntu wily InRelease
Hit:2 http://archive.canonical.com/ubuntu xenial InRelease                                                                    
Hit:3 http://linux.dropbox.com/ubuntu wily Release                                                                             
Ign:4 http://dl.google.com/linux/chrome/deb stable InRelease                                                                   
Hit:5 http://ppa.launchpad.net/jfi/ppa/ubuntu xenial InRelease                                                                 
Hit:6 http://dl.google.com/linux/chrome/deb stable Release                                                                     
Hit:7 http://ppa.launchpad.net/kasra-mp/ubuntu-indicator-weather/ubuntu xenial InRelease                                       
Hit:8 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial InRelease                                                    
Hit:9 https://repo.skype.com/deb stable InRelease                                                                              
Hit:10 https://deb.nodesource.com/node_4.x xenial InRelease                                         
Hit:12 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu xenial InRelease                     
Hit:13 http://ppa.launchpad.net/webupd8team/atom/ubuntu xenial InRelease                            
Hit:14 http://us.archive.ubuntu.com/ubuntu xenial InRelease                                         
Hit:15 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease
Hit:16 http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu xenial InRelease
Reading package lists... Done 
```

The problem is when I do "sudo apt-get upgrade" or "sudo apt-get install <program>", the errors listed before appear. As i have been mentioning,  it could be a problem with broken packages, as you can see in any of the error output. I have a strong feeling it is related to "12 not fully installed or removed " error message.

---

### Post by curious-ninja on 2018-02-28
No, i don't have aptitude installed.

---

### Post by kc1di on 2018-02-28
do you have synaptic installed?
if so go there and see if you can fix broken packages via edit >fix broken packages.
if your using wayland you can't use synaptic.

---

### Post by curious-ninja on 2018-02-28
No, I don't have synaptic installed. I have Ubuntu Software and it provides no means to deal with broken packages.

---

### Post by curious-ninja on 2018-02-28
I found this post on the forum [https://askubuntu.com/questions/881218/16-04-lts-update-fails-errors-were-encountered-while-processing-util-linux](https://askubuntu.com/questions/881218/16-04-lts-update-fails-errors-were-encountered-while-processing-util-linux)

I am facing a very similar problem. However, their solution is not specific to my case.

---

### Post by vasa1 on 2018-02-28
I came across```
apt-get remove insserv
```suggested here: [https://help.directadmin.com/item.php?id=379](https://help.directadmin.com/item.php?id=379)

Did you already try that? You mentioned running```
sudo apt-get remove <program>
``` :???:

---

### Post by kc1di on 2018-02-28
Ok, lets try this command: ```
sudo apt update –fix-missing
```

---

### Post by kc1di on 2018-02-28
if the above does not work you'll have to remove the broken packages manually by editing the /var/lib/dpkg/status  file.
you can use nano or gedit but must be root to do so.```
sudo nano /var/lib/dpkg/status
```

Locate the corrupt package, and remove the whole block of information about it and save the file.
good luck.

---

### Post by curious-ninja on 2018-02-28
I had already tried to alter the broken packages manually from ```
sudo nano /var/lib/dpkg/status
```. All the 12 broken packages have heavy dependencies and some packages were really basic like "util-linux". I didn't dare to force remove them. Today I tried it again with more aggressiveness; but the system is complaining that some dependencies are unavailable.  

Since I am having this problem for a while (and I really need my system upright), I went on to reinstall the OS. 

Thank you all for your suggestions.

---

### Post by kc1di on 2018-02-28
Glad you'll have it working for you :)

---


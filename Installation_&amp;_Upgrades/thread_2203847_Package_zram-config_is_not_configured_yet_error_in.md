---
title: "Package zram-config is not configured yet error in lubuntu 13.10 installation"
date: 2014-02-05
forum: Installation &amp; Upgrades
---

### Post by risva on 2014-02-05
Hello,

i have recently installed lubuntu 13.10 on a non pae(celeron M) processor Pressario 2200 using help from _[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)_.

i´ve been able to upgrade my system from lubuntu 12.04 core ver to 13.10 lubuntu-desktop; everything seems to be working fine except that installing any new package(vlc media player) gives following error:

```
#
installArchives() failed:  ...................................
....................................
.................................... 
Selecting previously unselected package qdbus. 
Unpacking qdbus (from .../qdbus_4%%3a4.8.4+dfsg-0ubuntu18.1_i386.deb) ... 
Selecting previously unselected package qtchooser. 
Unpacking qtchooser (from .../qtchooser_26-3ubuntu2_i386.deb) ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for man-db ... 
Processing triggers for mime-support ... 
Processing triggers for gnome-menus ... 
Processing triggers for desktop-file-utils ... 
Setting up zram-config (0.1) ... 
start: Job failed to start 
invoke-rc.d: initscript zram-config, action "start" failed. 
dpkg: error processing zram-config (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of lubuntu-desktop: 
 lubuntu-desktop depends on zram-config; however: 
  Package zram-config is not configured yet. 
 
dpkg: error processing lubuntu-desktop (--configure): 
 dependency problems - leaving unconfigured 
Setting up libaudio2:i386 (1.9.3-6) ... 
No apport report written because MaxReports is reached already
Setting up libcrystalhd3:i386 (1:0.0~git20110715.fdd2f19-9ubuntu1) ... 
Setting up libdirac-encoder0:i386 (1.0.2-6ubuntu1) ... 
Setting up libdvbpsi8:i386 (1.0.0-3) ... 
Setting up libebml3:i386 (1.2.2-2) ... 
Setting up liblcms1:i386 (1.19.dfsg-1.2ubuntu3) ... 
Setting up liblua5.1-0:i386 (5.1.5-5) ... 
Setting up libmad0:i386 (0.15.1b-7ubuntu2) ... 
Setting up libmatroska5:i386 (1.3.0-2) ... 
Setting up libmng1:i386 (1.0.10-3build1) ... 
Setting up libmpeg2-4:i386 (0.5.1-5) ... 
Setting up mysql-common (5.5.35-0ubuntu0.13.10.2) ... 
Setting up libmysqlclient18:i386 (5.5.35-0ubuntu0.13.10.2) ... 
Setting up libopus0 (1.0.1-0ubuntu2) ... 
Setting up libqtcore4:i386 (4:4.8.4+dfsg-0ubuntu18.1) ... 
Setting up libqt4-xml:i386 (4:4.8.4+dfsg-0ubuntu18.1) ... 
Setting up libqt4-dbus:i386 (4:4.8.4+dfsg-0ubuntu18.1) ... 
Setting up libqt4-network:i386 (4:4.8.4+dfsg-0ubuntu18.1) ... 
Setting up libqt4-script:i386 (4:4.8.4+dfsg-0ubuntu18.1) ... 
Setting up libqt4-sql:i386 (4:4.8.4+dfsg-0ubuntu18.1) ... 
Setting up libqt4-xmlpatterns:i386 (4:4.8.4+dfsg-0ubuntu18.1) ... 
Setting up libqt4-sql-mysql:i386 (4:4.8.4+dfsg-0ubuntu18.1) ... 
Setting up libwebp4:i386 (0.3.0-3) ... 
Setting up libsdl-image1.2:i386 (1.2.12-4ubuntu1) ... 
Setting up libssh2-1:i386 (1.4.3-1) ... 
Setting up libva-x11-1:i386 (1.1.1-3) ... 
Setting up vlc-data (2.0.8-1) ... 
Setting up libvlccore5 (2.0.8-1) ... 
Setting up libvlc5 (2.0.8-1) ... 
Setting up libx264-123:i386 (2:0.123.2189+git35cf912-1ubuntu1.1) ... 
Setting up libxcb-composite0:i386 (1.9.1-3ubuntu1) ... 
Setting up libxcb-randr0:i386 (1.9.1-3ubuntu1) ... 
Setting up libxcb-xv0:i386 (1.9.1-3ubuntu1) ... 
Setting up libzvbi-common (0.2.33-7) ... 
Setting up libzvbi0:i386 (0.2.33-7) ... 
Setting up liba52-0.7.4 (0.7.4-16build1) ... 
Setting up libdc1394-22:i386 (2.2.1-1ubuntu1) ... 
Setting up libkate1 (0.4.1-1) ... 
Setting up libmpcdec6 (2:0.1~r459-1ubuntu1) ... 
Setting up libresid-builder0c2a (2.1.1-14) ... 
Setting up libsidplay2 (2.1.1-14) ... 
Setting up libtwolame0 (0.3.13-1build1) ... 
Setting up libupnp6 (1:1.6.17-1.2) ... 
Setting up libiso9660-8 (0.83-4ubuntu1) ... 
Setting up libvcdinfo0 (0.7.24+dfsg-0.1) ... 
Setting up vlc-nox (2.0.8-1) ... 
Setting up libtar0 (1.2.19-1) ... 
Setting up libxcb-keysyms1:i386 (0.3.9-1) ... 
Setting up vlc-plugin-notify (2.0.8-1) ... 
Setting up vlc-plugin-pulse (2.0.8-1) ... 
Setting up qdbus (4:4.8.4+dfsg-0ubuntu18.1) ... 
Setting up qtchooser (26-3ubuntu2) ... 
Setting up libqt4-declarative:i386 (4:4.8.4+dfsg-0ubuntu18.1) ... 
Setting up libqtgui4:i386 (4:4.8.4+dfsg-0ubuntu18.1) ... 
Setting up vlc (2.0.8-1) ... 
Processing triggers for libc-bin ... 
Errors were encountered while processing: 
 zram-config 
 lubuntu-desktop 
Setting up zram-config (0.1) ... 
start: Job failed to start 
invoke-rc.d: initscript zram-config, action "start" failed. 
dpkg: error processing zram-config (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of lubuntu-desktop: 
 lubuntu-desktop depends on zram-config; however: 
  Package zram-config is not configured yet. 
 
dpkg: error processing lubuntu-desktop (--configure): 

##
```

please help me resolve the issue.

......thanx for help.

---

### Post by mörgæs on 2014-02-05
First, please boot and after that post the output from
```
sudo apt-get update
sudo apt-get dist-upgrade
```
in CODE tags.

---

### Post by risva on 2014-02-06
Dear Morgaes,

output of the code was as under:

```
##

saesha@dhcppc3:~$ sudo apt-get update
[sudo] password for saesha: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease                        
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg [933 B]            
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release [49.6 kB]    
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources [28.3 kB]   
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources [14 B]      
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources [8,372 B]     
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources [691 B]     
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages [78.7 kB]   
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages [14 B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages [31.6 kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages [1,385 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports InRelease
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy Release.gpg                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en        
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates Release.gpg [933 B]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports Release.gpg                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en        
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates Release [49.6 kB]            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main i386 Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Translation-en                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_US     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en                 
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Sources [69.7 kB]       
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Sources [14 B]    
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Sources [45.9 kB]   
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Sources [1,360 B] 
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main i386 Packages [197 kB]  
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted i386 Packages [14 B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe i386 Packages [135 kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse i386 Packages [1,777 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en_US
Fetched 701 kB in 45s (15.5 kB/s)
Reading package lists... Done
saesha@dhcppc3:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up zram-config (0.1) ...
start: Job failed to start
invoke-rc.d: initscript zram-config, action "start" failed.
dpkg: error processing zram-config (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of lubuntu-desktop:
 lubuntu-desktop depends on zram-config; however:
  Package zram-config is not configured yet.

dpkg: error processing lubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 zram-config
 lubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
saesha@dhcppc3:~$ 


##
```

...

---

### Post by mörgæs on 2014-02-06
And 
```
sudo apt-get install -f
sudo dpkg --configure -a

```
?

---

### Post by risva on 2014-02-06
the output is.

##
saesha@dhcppc3:~$ sudo apt-get install -f
[sudo] password for saesha: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up zram-config (0.1) ...
start: Job failed to start
invoke-rc.d: initscript zram-config, action "start" failed.
dpkg: error processing zram-config (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of lubuntu-desktop:
 lubuntu-desktop depends on zram-config; however:
  Package zram-config is not configured yet.

dpkg: error processing lubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 zram-config
 lubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
saesha@dhcppc3:~$ sudo dpkg --configure -a
Setting up zram-config (0.1) ...
start: Job failed to start
invoke-rc.d: initscript zram-config, action "start" failed.
dpkg: error processing zram-config (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of lubuntu-desktop:
 lubuntu-desktop depends on zram-config; however:
  Package zram-config is not configured yet.

dpkg: error processing lubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 zram-config
 lubuntu-desktop
saesha@dhcppc3:~$ 


##
..

---

### Post by risva on 2014-02-07
Dear Morgaes,

does it look like very messed up ??

is there any way to solve this...

---

### Post by risva on 2014-02-07
i´m unable install flsh plugin etc....totally stuck up ....please help!

---

### Post by mörgæs on 2014-02-07
Please stop bumping your thread.
I am out of ideas, sorry.

---

### Post by howefield on 2014-02-07
Could be this bug...

[https://bugs.launchpad.net/ubuntu/+source/zram-config/+bug/996535](https://bugs.launchpad.net/ubuntu/+source/zram-config/+bug/996535)

---

### Post by mörgæs on 2014-02-07
Thanks for posting the bug report.

Risva, did the suggestions in post 7 and 8 (in the Launchpad report) help?

---

### Post by risva on 2014-02-08
thanx for the support by the forum moderator and admin himself....

but sorry the ans is negative...repeating #7, gives same error and repeating #8 says no such service installed.

if it is not feasible to resolve this bug ...would xubuntu 12.04 likely to help me(non pae celeron M proc, unable to run ubuntu unity...) (till now i was using ubuntu 10.10.....) since the support for 10.10 has discontinued, please suggest me some OS and version which is likely to run with ubuntu community support.

thanx a lot.

---

### Post by mörgæs on 2014-02-08
Yes, Xubuntu 12.04 or Bodhi Linux are options. 
When Lubuntu 14.04 comes out it will be possible to upgrade in one step from 12.04 (with Fake-PAE). Hopefully the zram problem is solved at that time.

---

### Post by risva on 2014-02-09
Thank you Morgaes and Howefield for your kind help....
i have atleast reached a conclusion with sufficient authority behind it...
i really appreciate your help.

---

### Post by risva on 2014-04-26
Thanks Morgaes,

ubuntu 14.04 has indeed taken care of non pae machines. i'm now running lubuntu on my machine and very satisfied to have the old man running.

---


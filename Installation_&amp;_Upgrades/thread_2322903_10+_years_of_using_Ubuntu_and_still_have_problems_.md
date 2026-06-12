---
title: "10+ years of using Ubuntu and still have problems from time to time..."
date: 2016-05-01
forum: Installation &amp; Upgrades
---

### Post by djsroknrol on 2016-05-01
Yea me!!....Still in love with this distro after all these years....BUT every once in a while, I run into problems. Sometimes easy ones, sometime baffling ones; like this one:

Update-manager came up with a wierd one the other day. I'm still on 14.04 LTS, not trying to upgrade to 16.04 yet, but it's a 108MB update and it keeps asking for the 16.04LTS CD/DVD. It will not move further than that. 

Has anyone else experienced this and what are my options? I'm content in waiting until stable to stable in July so upgrading is not an option right now.

---

### Post by vasa1 on 2016-05-01
What's the output of *sudo apt-get update* and *sudo apt-get upgrade* and even *sudo apt-get dist-upgrade*? You can press 'n' if you don't want the last one to execute, but the output may help someone diagnose the issue.

---

### Post by djsroknrol on 2016-05-01
This is the output from the first 2 commands....
```
rjberger@Bob:~$ sudo apt-get update
[sudo] password for rjberger: 
Ign cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1) xenial InRelease
Ign cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1) xenial/main Translation-en_US
Ign cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1) xenial/main Translation-en
Ign cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1) xenial/restricted Translation-en_US
Ign cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1) xenial/restricted Translation-en
Hit http://security.ubuntu.com trusty-security InRelease                       
Ign http://us.archive.ubuntu.com trusty InRelease                              
Hit http://us.archive.ubuntu.com trusty-updates InRelease               
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://us.archive.ubuntu.com trusty-backports InRelease
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://us.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources 
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages             
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages         
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/main Sources      
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources  
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages  
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en     
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-en_US                
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en 
Hit http://us.archive.ubuntu.com trusty Release                           
Ign http://extras.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/main Sources                
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Reading package lists... Done                                                  
rjberger@Bob:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libmpdec2 libntdb1 libquvi-scripts libquvi7 linux-headers-3.13.0-55
  linux-headers-3.13.0-55-generic linux-image-3.13.0-55-generic
  linux-image-extra-3.13.0-55-generic python-ntdb
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  bcmwl-kernel-source dkms dpkg firefox firefox-globalmenu firefox-locale-en
  gir1.2-gtk-3.0 gir1.2-soup-2.4 libdpkg-perl libgail-3-0 libgtk-3-0
  libgtk-3-bin libgtk-3-common libmm-glib0 libnautilus-extension1a
  liboxideqt-qmlplugin liboxideqtcore0 liboxideqtquick0 libsoup-gnome2.4-1
  libsoup2.4-1 modemmanager nautilus nautilus-data oneconf oneconf-common
  oxideqt-codecs-extra python-oneconf python3-oneconf thunderbird
  thunderbird-globalmenu thunderbird-gnome-support thunderbird-locale-en
  thunderbird-locale-en-gb thunderbird-locale-en-us tzdata tzdata-java
36 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 32.6 MB/116 MB of archives.
After this operation, 6,347 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Media change: please insert the disc labeled
 'Ubuntu 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1)'
in the drive '/media/cdrom/' and press enter

Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libgtk-3-common all 3.10.8-0ubuntu1.6 [167 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libgail-3-0 i386 3.10.8-0ubuntu1.6 [20.1 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libgtk-3-0 i386 3.10.8-0ubuntu1.6 [1,923 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libmm-glib0 i386 1.0.0-2ubuntu1.1 [127 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main gir1.2-gtk-3.0 i386 3.10.8-0ubuntu1.6 [174 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libgtk-3-bin i386 3.10.8-0ubuntu1.6 [18.0 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libnautilus-extension1a i386 1:3.10.1-0ubuntu9.11 [51.9 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main modemmanager i386 1.0.0-2ubuntu1.1 [473 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main nautilus-data all 1:3.10.1-0ubuntu9.11 [50.7 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main nautilus i386 1:3.10.1-0ubuntu9.11 [485 kB]
Media change: please insert the disc labeled                
 'Ubuntu 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1)'
in the drive '/media/cdrom/' and press enter

Get:11 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main liboxideqtcore0 i386 1.14.7-0ubuntu0.14.04.1 [28.2 MB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main oxideqt-codecs-extra i386 1.14.7-0ubuntu0.14.04.1 [902 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main oneconf-common all 0.3.7.14.04.1 [6,042 B]
Get:14 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-oneconf all 0.3.7.14.04.1 [19.5 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main oneconf all 0.3.7.14.04.1 [5,458 B]
Get:16 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python-oneconf all 0.3.7.14.04.1 [19.7 kB]
Media change: please insert the disc labeled                                   
 'Ubuntu 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1)'
in the drive '/media/cdrom/' and press enter

```

---

### Post by vasa1 on 2016-05-01
I guess you'll need to post your */etc/apt/sources.list* as well.

---

### Post by kansasnoob on 2016-05-01
Sounds like you somehow enabled it in Software Settings > Installable from CD-ROM/DVD:

[ATTACH=CONFIG]268750[/ATTACH]

Maybe you were playing with the DVD and clicked on "open with ............?????????????????????". If it's enabled there just untick the box and try again.

---

### Post by djsroknrol on 2016-05-01
> **kansasnoob said:**
> Sounds like you somehow enabled it in Software Settings > Installable from CD-ROM/DVD:

[ATTACH=CONFIG]268750[/ATTACH]

Maybe you were playing with the DVD and clicked on "open with ............?????????????????????". If it's enabled there just untick the box and try again.

Well kansasnoob, that did the trick.....but I found the check box under the "other software" tab....Many thanks :)

---


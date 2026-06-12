---
title: "Error installing anything"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by Lambbear on 2010-09-23
When i try installing anything i get errors, for example when i try to install somthing from ubuntu software center i get this.

```
installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
Selecting previously deselected package ttf-symbol-replacement. 
(Reading database ...  
dpkg: warning: files list file for package `libsdl-image1.2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `liblzo2-2' missing, assuming package has no files currently installed. 
 (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95%dpkg: unrecoverable fatal error, aborting: 
 files list file for package `tasksel-data' contains empty filename
```when I try to update my system I get the error found in my attachment

Please Help

---

### Post by mörgæs on 2010-09-23
Try to boot the machine and run

```
sudo apt-get update
sudo apt-get upgrade
```

Which messages do you get?

---

### Post by Lambbear on 2010-09-23
Heres what i got after trying that


```
bunny@Bunny-desktop:~$ sudo apt-get update
[sudo] password for bunny: 
Hit http://packages.medibuntu.org lucid Release.gpg
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US
Get:1 http://security.ubuntu.com lucid-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US  
Hit http://us.archive.ubuntu.com lucid Release.gpg                            
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US
Hit http://packages.medibuntu.org lucid Release
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:2 http://security.ubuntu.com lucid-security Release [38.5kB]     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com lucid-updates Release.gpg [198B]        
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release                             
Hit http://packages.medibuntu.org lucid/free Packages                          
Get:4 http://us.archive.ubuntu.com lucid-updates Release [44.7kB]            
Hit http://packages.medibuntu.org lucid/non-free Packages                      
Get:5 http://security.ubuntu.com lucid-security/main Packages [81.3kB]         
Hit http://us.archive.ubuntu.com lucid/main Packages           
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources     
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Get:6 http://us.archive.ubuntu.com lucid-updates/main Packages [309kB]
Get:7 http://security.ubuntu.com lucid-security/restricted Packages [14B]   
Get:8 http://security.ubuntu.com lucid-security/main Sources [29.3kB]
Get:9 http://security.ubuntu.com lucid-security/restricted Sources [14B]       
Get:10 http://security.ubuntu.com lucid-security/universe Packages [39.7kB] 
Get:11 http://security.ubuntu.com lucid-security/universe Sources [9,810B]
Get:12 http://security.ubuntu.com lucid-security/multiverse Packages [1,869B]  
Get:13 http://security.ubuntu.com lucid-security/multiverse Sources [656B]     
Get:14 http://us.archive.ubuntu.com lucid-updates/restricted Packages [3,267B] 
Get:15 http://us.archive.ubuntu.com lucid-updates/main Sources [122kB]
Get:16 http://us.archive.ubuntu.com lucid-updates/restricted Sources [1,443B]
Get:17 http://us.archive.ubuntu.com lucid-updates/universe Packages [121kB]
Get:18 http://us.archive.ubuntu.com lucid-updates/universe Sources [48.2kB]
Get:19 http://us.archive.ubuntu.com lucid-updates/multiverse Packages [3,651B]
Get:20 http://us.archive.ubuntu.com lucid-updates/multiverse Sources [1,739B]
Fetched 856kB in 2s (297kB/s)                               
Reading package lists... Done
bunny@Bunny-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  bzip2 dpkg fglrx-modaliases flashplugin-installer gnome-terminal
  gnome-terminal-data lib32bz2-1.0 libbz2-1.0 libphonon4 libqt4-assistant
  libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl
  libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql
  libqt4-sql-mysql libqt4-svg libqt4-test libqt4-webkit libqt4-xml
  libqt4-xmlpatterns libqtcore4 libqtgui4 libssl0.9.8 openssl phonon
30 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/23.8MB of archives.
After this operation, 172kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 
dpkg: warning: files list file for package `libsdl-image1.2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblzo2-2' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `tasksel-data' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
bunny@Bunny-desktop:~$ 
```

---

### Post by mörgæs on 2010-09-23
Does this help?
[http://ubuntuforums.org/showthread.php?t=1437692](http://ubuntuforums.org/showthread.php?t=1437692)

---

### Post by Lambbear on 2010-09-24
No those didn't work :(.

I got a crash report saying this after trying to update again.

---


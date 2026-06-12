---
title: "GPG error"
date: 2013-05-17
forum: Installation &amp; Upgrades
---

### Post by suresh muniswamy on 2013-05-17
Hi All,

I am trying to do install build-essential  and update command, i do i get gpg error. could any one tll me how to solve this issues .
I am using ubutu 12.04 version 64 bit operating sys.

[COLOR=#ff0000]ERROR 1:[/COLOR]
 
suresh@PC0007103:~$ sudo apt-get build-essentials
E: Invalid operation build-essentials
suresh@PC0007103:~$ sudo dpkg --configure -a
dpkg: error: failed to open package info file `/usr/local/var/lib/dpkg/status' for reading: No such file or directory

[COLOR=#ff0000]ERROR 2:[/COLOR]

suresh@PC0007103:/var/lib/apt$ sudo apt-get clean
suresh@PC0007103:/var/lib/apt$ sudo apt-get update
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) dists/precise/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) dists/precise/restricted/binary-i386/ Release
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) dists/precise/restricted/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) dists/precise/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) dists/precise/restricted/binary-i386/ Translation-en
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]                 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Get:4 [http://www.emdebian.org](http://www.emdebian.org) squeeze Release.gpg [198 B]                      
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]                   
Get:6 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [1,940 B]                   
Get:7 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                 
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Get:9 [http://www.emdebian.org](http://www.emdebian.org) squeeze Release [4,785 B]                        
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]         
Get:11 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7,078 B]                  
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]        
Get:13 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release [1,942 B]                      
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
E: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: NODATA 1 NODATA 2


Regards 
SureshM

---

### Post by plucky on 2013-05-18
> suresh@PC0007103:~$ sudo apt-get build-essentials
E: Invalid operation build-essentials

The command is ```
sudo apt-get install build-essential
```

Can you post the output for ```
cat /etc/apt/sources.list
```

You don't seem to have the main,restricted,universe and multiverse repositories enabled.

> Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) dists/precise/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) dists/precise/restricted/binary-i386/ Release
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) dists/precise/restricted/binary-i386/ Packages
Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) dists/precise/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) dists/precise/restricted/binary-i386/ Translation-en

Disable the CD rom as a source in Software Sources.

> E: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

Try selecting a different server in Software Sources.

Good Luck

---


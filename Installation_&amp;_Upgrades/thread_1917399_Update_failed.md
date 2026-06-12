---
title: "Update failed"
date: 2012-01-30
forum: Installation &amp; Upgrades
---

### Post by dhammikai on 2012-01-30
Hi,
I installed Ubantu 10.10 version through windows XP. Then I set-up my office network settings through "Auto eth0" and also I set up system-->preferances-->network proxy settings. Then I update some of packages thorugh synaptic package manager, it also succeeded. Then I try to update my ubantu release through system-->preferances-->update manager, and I check for updates but it says "check your internet connection" message. My Internet connection is OK. Please help me to find how I update my Ubantu software through internet.

Thanks 
Dhammika

NB: I tried to use 
sudo apt-get update 
cmd, then I received a msg "some index files failed to download they have been ignored...."

here this is the out put of upate 
                     p { margin-bottom: 0.08in; }  W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/main/i18n/Translation-en.bz2   
 , W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/restricted/i18n/Translation-en.bz2   
 , W:Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Alpha i386 (20111206)/dists/precise/Release.gpg   
 , W:Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Alpha i386 (20111206)/dists/precise/main/i18n/Translation-en.bz2   
 , W:Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Alpha i386 (20111206)/dists/precise/restricted/i18n/Translation-en.bz2   
 , W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/Release   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.bz2)   
 , E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by cortman on 2012-01-30
If you can't update at all, change your server mirrors (open Synaptic, select Settings>Repositories, and change the "Download from...".

Otherwise, be sure you have your proxy settings right and that you can get online.
Also, it's Ub**[SIZE="2"]u[/SIZE]**ntu, not Ub**[SIZE="2"]a[/SIZE]**ntu.

---

### Post by raja.genupula on 2012-01-30
> **dhammikai said:**
> Hi,
I installed Ubantu 10.10 version through windows XP. Then I set-up my office network settings through "Auto eth0" and also I set up system-->preferances-->network proxy settings. Then I update some of packages thorugh synaptic package manager, it also succeeded. Then I try to update my ubantu release through system-->preferances-->update manager, and I check for updates but it says "check your internet connection" message. My Internet connection is OK. Please help me to find how I update my Ubantu software through internet.

Thanks 
Dhammika

NB: I tried to use 
sudo apt-get update 
cmd, then I received a msg "some index files failed to download they have been ignored...."

here this is the out put of upate 
                     p { margin-bottom: 0.08in; }  W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/main/i18n/Translation-en.bz2   
 , W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/restricted/i18n/Translation-en.bz2   
 , W:Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Alpha i386 (20111206)/dists/precise/Release.gpg   
 , W:Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Alpha i386 (20111206)/dists/precise/main/i18n/Translation-en.bz2   
 , W:Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Alpha i386 (20111206)/dists/precise/restricted/i18n/Translation-en.bz2   
 , W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/Release   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.bz2)   
 , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.bz2)   
 , E:Some index files failed to download, they have been ignored, or old ones used instead.

open update manager -> settings and at first TAB uncheck the CD-ROM option .

---


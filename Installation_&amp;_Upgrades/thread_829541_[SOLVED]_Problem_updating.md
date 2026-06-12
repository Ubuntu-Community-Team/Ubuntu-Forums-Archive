---
title: "[SOLVED] Problem updating"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by goathunter on 2008-06-14
Hello I seem to be having a problem updating. When I try to install updates or use synaptic this is what i get. (see screenshot) I am using 8.04. I have been though my sources.list and there is no sign of 'web' which seem to be the cause of this on other peoples computers. Here is my sources.list

Quote:
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://hydr0g3n.free.fr/qbittorrent/gutsy/](http://hydr0g3n.free.fr/qbittorrent/gutsy/) ./
deb-src [http://hydr0g3n.free.fr/qbittorrent/gutsy/](http://hydr0g3n.free.fr/qbittorrent/gutsy/) ./


Thankyou for your time

---

### Post by Partyboi2 on 2008-06-14
I would suggest # out all the gusty entries from your sources.list and running
```
sudo apt-get update
```

---

### Post by goathunter on 2008-06-14
Hello Thankyou for you reply. However I did this and still no luck. Still getting failed in buffer read error.

---

### Post by PmDematagoda on 2008-06-15
Do:-
```
sudo apt-get clean
```
and see if that fixes it.

---

### Post by goathunter on 2008-06-15
Hello. Nah no luck still failing to update.Cheers anyway.

---

### Post by PmDematagoda on 2008-06-15
Post the output of:-
```
ls /var/cache/apt/archives
```
also post the output of:-
```
sudo apt-get update
```

---

### Post by goathunter on 2008-06-15
> **PmDematagoda said:**
> Post the output of:-
```
ls /var/cache/apt/archives
```
also post the output of:-
```
sudo apt-get update
```
  
Hello here it is.

> marcus@marcus-laptop:~$ ls /var/cache/apt/archives
cpp_4%3a4.2.3-1ubuntu6_i386.deb
deskbar-applet_2.22.2.1-0ubuntu1_i386.deb
evolution-exchange_2.22.2-0ubuntu1_i386.deb
firefox-3.0_3.0~rc1+nobinonly-0ubuntu0.8.04.1_i386.deb
firefox-3.0-gnome-support_3.0~rc1+nobinonly-0ubuntu0.8.04.1_i386.deb
firefox_3.0~rc1+nobinonly-0ubuntu0.8.04.1_all.deb
firefox-gnome-support_3.0~rc1+nobinonly-0ubuntu0.8.04.1_all.deb
gcc_4%3a4.2.3-1ubuntu6_i386.deb
gij_4%3a4.2.3-1ubuntu6_i386.deb
gnome-cards-data_1%3a2.22.2.1-0ubuntu1_all.deb
gnome-games_1%3a2.22.2.1-0ubuntu1_i386.deb
gnome-games-data_1%3a2.22.2.1-0ubuntu1_all.deb
language-pack-en_1%3a8.04+20080527_all.deb
language-pack-en-base_1%3a8.04+20080527_all.deb
language-pack-gnome-en_1%3a8.04+20080527_all.deb
language-pack-gnome-en-base_1%3a8.04+20080527_all.deb
libgcj-bc_4.2.3-1ubuntu6_i386.deb
libgcj-common_1%3a4.2.3-1ubuntu6_i386.deb
libldap-2.4-2_2.4.7-6ubuntu4.2_i386.deb
liblircclient0_0.8.3~pre1-0ubuntu7.1_i386.deb
libnspr4-0d_4.7.1+1.9-0ubuntu0.8.04.1_i386.deb
libnss3-0d_3.12.0.2+1.9-0ubuntu0.8.04.1_i386.deb
libnss3-1d_3.12.0.2+1.9-0ubuntu0.8.04.1_i386.deb
libntfs-3g23_1%3a1.2216-1ubuntu2_i386.deb
libparted1.7-1_1.7.1-5.1ubuntu9.1_i386.deb
lock
ntfs-3g_1%3a1.2216-1ubuntu2_i386.deb
openssl-blacklist_0.3.3+0.4-0ubuntu0.8.04.1_all.deb
parted_1.7.1-5.1ubuntu9.1_i386.deb
partial
pciutils_1%3a2.2.4-1.1ubuntu4_i386.deb
pm-utils_0.99.2-3ubuntu10_all.deb
xserver-xorg-core_2%3a1.4.1~git20080131-1ubuntu9.2_i386.deb
xserver-xorg-video-intel_2%3a2.2.1-1ubuntu13.4_i386.deb
xulrunner-1.9_1.9~rc1+nobinonly-0ubuntu1~8.04.2_i386.deb
xulrunner-1.9-gnome-support_1.9~rc1+nobinonly-0ubuntu1~8.04.2_i386.deb
yelp_2.22.1-0ubuntu2.8.04.1_i386.deb
marcus@marcus-laptop:~$ 




> marcus@marcus-laptop:~$ sudo apt-get update
[sudo] password for marcus: 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy Release.gpg
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy/main Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy/universe Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy/multiverse Translation-en_NZ
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates Release.gpg   
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates/main Translation-en_NZ       
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates/restricted Translation-en_NZ 
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates/universe Translation-en_NZ   
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates/multiverse Translation-en_NZ 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) gutsy-backports Release.gpg
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) gutsy-backports/main Translation-en_NZ     
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) gutsy-backports/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) gutsy-backports/universe Translation-en_NZ 
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_NZ
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy Release                              
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates Release                      
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) gutsy-backports Release                       
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy/main Packages                           
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy/restricted Packages                  
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy/main Sources                         
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy/restricted Sources                   
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy/universe Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_NZ
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) gutsy-backports/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) gutsy-backports/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) gutsy-backports/universe Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) gutsy-backports/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_NZ
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_NZ
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_NZ
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Reading package lists... Done
marcus@marcus-laptop:~$ 


Thankyou for taking the time to checke this out for me

---

### Post by PmDematagoda on 2008-06-15
Do:-
```
sudo rm /var/cache/apt/archives/libntfs-3g23_1%3a1.2216-1ubuntu2_i386.deb
```

Also try:-
```
sudo apt-get autoclean
```
and see if those commands fixes the problem.

---

### Post by upchucky on 2008-06-15
there are many here that know a lot more than I do, but someone helped me yesterday when i could not get mine to update.

they had me change my sources from download from main server to download from server for united states.

after that all was well

---

### Post by goathunter on 2008-06-16
> **PmDematagoda said:**
> Do:-
```
sudo rm /var/cache/apt/archives/libntfs-3g23_1%3a1.2216-1ubuntu2_i386.deb
```

Also try:-
```
sudo apt-get autoclean
```
and see if those commands fixes the problem.

Hello. Nah did both the commands and am still getting the  'E: /var/cache/apt/archives/libntfs-3g23_1%3a1.2216-1ubuntu2_i386.deb: failed in buffer_read(fd)' error.  Thanks anyway. 

> there are many here that know a lot more than I do, but someone helped me yesterday when i could not get mine to update.

they had me change my sources from download from main server to download from server for united states.

after that all was well 


Hello. How did you do this?

---

### Post by goathunter on 2008-06-20
Bump

---

### Post by goathunter on 2008-07-01
Problem solved. I just did a complete reinstall from disc.

---


---
title: "upgrading from cd"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by archivenz on 2005-10-13
Gidday

I'm trying to upgrade from 5.04 to 5.10 using the iso image rather than getting the packages of the internet (1gb cap). I have added 5.10 to my source list using

apt-cdrom add

and changed hoary to breezy etc also in sources.list

i apt-get update without a problem, now when i dist-upgrade, i keep on getting this

1058 upgraded, 394 newly installed, 58 to remove and 0 not upgraded.
Need to get 323MB/770MB of archives.
After unpacking 455MB of additional disk space will be used.
Do you want to continue [Y/n]? n

How do i stop it from trying to use the internet? My flatmates would kill me if i used the entire month's cap in one go 

cheers.

---

### Post by Tomy on 2005-10-13
There is a line at the top of /etc/apt/sources.list that uses the cd repository. Here it is from an old sources.list file on my hard drive.

deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted

You might try to comment out all the other sources and then run:
$ sudo apt-get update
$ sudo apt-get upgrade

The key is to run apt-get update with only the cd as a repository.

This way you won't get anything off the internet. I have no idea if this will work. good luck

---

### Post by archivenz on 2005-10-13
Yip, i have

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

at the top from the apt-cdrom add, i imagine

yeah, going to try hashing out the internet based sources soon i think

cheers

---

### Post by archivenz on 2005-10-13
hrm that didnt work either

it said that i didnt need to download any packages
but then said this for all the packages

Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/pool/main/p/pilot-link/python-pisock_0.11.8-10ubuntu3_i386.deb  File not found
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/pool/main/p/pycurl/python2.4-pycurl_7.14.0-1ubuntu1_i386.deb  File not found

etc etc

the cd is in the cdrom drive too :p
cheers

---

### Post by archivenz on 2005-10-14
still no go..

anyone else got some suggestions?

cheers

---


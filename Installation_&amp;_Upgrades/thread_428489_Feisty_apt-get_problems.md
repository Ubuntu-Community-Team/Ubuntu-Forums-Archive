---
title: "Feisty apt-get problems"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by tonys102 on 2007-04-30
Hi All,

Sadly I have limited bandwidth in my office, so I downloaded the kubuntu CD and ubuntu CD from home and wanted to mount them as ISO's to assist in the update. However, I believe that I followed the instructions correctly in that I could get apt-cdrom to recognise the ISO's, but when I perform a apt-get install kubuntu-desktop it goes straight to the net!!! 

My sources.list includes the following: -
deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb cdrom:[Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)]/ feisty main restricted

But it always asks me to insert into /cdrom, and not mount the ISO! My /etc/fstab shows: -

/home/ukdata/Data/Linux/ubuntu-7.04-server-i386.iso /mnt/ubuntu-server  udf,iso9660     user,noauto,loop        0       0
/home/ukdata/Data/Linux/kubuntu-7.04-desktop-i386.iso /mnt/kubuntu      udf,iso9660     user,noauto,loop        0       0

Any ideas???

---

### Post by aysiu on 2007-04-30
Can you try changing these lines in your /etc/apt/sources.list from ```
deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb cdrom:[Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)]/ feisty main restricted
``` to ```
#deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
#deb cdrom:[Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)]/ feisty main restricted
deb file:/mnt/kubuntu feisty main restricted
``` and then doing this? ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---


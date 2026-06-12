---
title: "Portable installation vs Full installation vs VMWare Image"
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by inteman2 on 2012-07-04
Hi, 
I'm a beginner with linux and i require it for setting up my beagleboard ([www.beagleboard.org](www.beagleboard.org)). My question is that should I install
- ubuntu as full OS on my harddisk
- as a portable OS on my flash drive
- or as a VMWare image

I want to keep the impact of installing Ubuntu on my system to a minimum. Here are the specs of my system:

- AMD Turion ZM-82 (2.2 GHz)
- 2 GB RAM
- Windows 7

Thanks

---

### Post by msammels on 2012-07-04
It all depends. I generally don't like Ubuntu on a flash drive as you don't always get strong numbers in regards to persistent storage - I find it tends to fill up fast because of the required updates.

As a VMWare image, or a full install is your personal choice. Personally, I went full install as running anything virtual limits everything it can use from processor speed, to RAM.

---

### Post by inteman2 on 2012-07-04
Thank you for your reply.

Will a full installation partition my already existing hard drive? (It said something like that when I tried to install 12.04)

---

### Post by msammels on 2012-07-04
Sadly, Ubuntu lost the option to install alongside, so unless you delve into manual partitioning, then yes, it will erase your hard drive.

---

### Post by inteman2 on 2012-07-04
So there is no way i can have Windows 7 and Ubuntu on a same partition?

---

### Post by msammels on 2012-07-04
On the same partition? Yes - install [Wubi](http://www.ubuntu.com/download/desktop/windows-installer).

---

### Post by Frogs Hair on 2012-07-04
Wubi has a 30 GB maximum  space limit at installation and It won't hibernate. As long as you are ok with that use it , but it is meant to be for trial use and would not suggest long term installation.

---


---
title: "When installing I get some messages that I don't think are supposed to be there"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by crazyants on 2007-06-18
My comp is at 350 some ram and a 10G HDD. My computer can run the live cd of 6.06 LTS just fine, but I have nothing on the hard drive so I want to install Ubuntu, but as I go through the install option I get to the part where its about to install and right in the beginning it say's "failed to create swap space" and then keeps going until 15%, where it stops making any progress at all.

help. I love you all.

---

### Post by crazyants on 2007-06-18
I also tried a Alternate CD, but When I got to the part where it tole me to partition the drive it wouldn't let me go any where, it also said that it found no disc drive and showed me a list of drivers.

---

### Post by dannyboy79 on 2007-06-18
sounds to me like it doesn't know what your hard drive's chipset controller is so it can't see it. can you see the hard drive when you're using the live cd?

---

### Post by crazyants on 2007-06-18
Well, when I go into computer area, it says file system, cd-rom and floppy drive.  so I'm guessing no.

---

### Post by dannyboy79 on 2007-06-18
you need to mount the drive from the livecd. What appears when you enter
sudo fdisk -l

---

### Post by crazyants on 2007-06-19
Ummm, how do I get to sudo from the live CD?

---

### Post by dannyboy79 on 2007-06-20
you simply use it, what do you mean? When it asks you for the password, it's blank, so just hit enter. It's been a very long time since I used the livecd but I am pretty sure that'll do it for ya.

---

### Post by crazyants on 2007-06-20
Never mind, I figured it out. anyway, It says it finds /dev/hda which is what I'm guessing it is but the installer won't let me partition it properly. 

In the alternate CD install, It asked me to pick a driver and I've figured that only two on the list work. One makes the installer think that I have 15 HDD with 2.2TB's each, while the other makes it so it see's one but it only says it has 8.7MB of space on it.

I is unhappy, please ubuntu just install.

---

### Post by crazyants on 2007-06-22
So I did the sudo fdisk and here is the results:

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...

I'm really confused

---


---
title: "Backing up &quot;/&quot; onto a DVD"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by patrick1314 on 2007-03-18
I'm sorry to be a pain, but I really need help here. I need a little 'walkthrough' on how to use Partimage.

Here's my setup:

On my Dell laptop I have partitioned the hard-drive thus:

1: 15GB NTFS partition with Windows MCE 2005
2: 15GB ext3 partition with Ubuntu Linux 6.10 (root "/")
3: Large ext3 partition mounting "/home"
4: Large(ish) FAT32 partition for sharing between Win and Linux 
+ SWAP

Migration from Windows to Linux is going smoothly (one day, I'll remove Windows from it altogether :P ).

Now, here's what I want to do!

I want to make an image of my root "/" partition only (containing purely the OS, system files and all programmes I have installed  - I don't want to back up my personal files in /home or elsewhere at the moment) and put it on a DVD so that if I want to reinstall I can use this DVD (with everything I need all ready and installed!) instead of the Ubuntu installation disk and then reinstalling all I need... This image would need to be able to install on a single particular partition without interfering with the others (ie. it must install on partition 2 where the OS resides).

Obviously I would need to be able to use it from a bootable CD/DVD.

I suspect I would need Partimage but I am completely unable to grasp the method of its use... can someone explain how I am to achieve my desired root "/" image?
Also, I downloaded, burned to CD (as an image) and tried the Linux SystemRescueCD containg Partimage - but when I try to boot it it starts loading up fine til it comes to the part about 'Skipping ALSA...' where it freezes and stops working. So... my first brush with Partimage didn't go too well.

Thanks!

---

### Post by patrick1314 on 2007-03-18
Bump! :)

---

### Post by zvacet on 2007-03-18
I don´t know is this helpfull,but have a look
[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

---


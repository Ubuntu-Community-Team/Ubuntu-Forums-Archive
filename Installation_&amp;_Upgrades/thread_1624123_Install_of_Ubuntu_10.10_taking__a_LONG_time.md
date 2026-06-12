---
title: "Install of Ubuntu 10.10 taking  a LONG time"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by perrojam on 2010-11-17
I have 10.10 on a USB stick, accessed it on boot, and decided to try it first. I then wanted to install it so went ahead and clicked the link on the desktop for installing. 

However 3 hours later it's still installing! Looking on the web I saw reports of between 15 minutes and an hour...

It's  been doing this for ages: "Creating ext4 file system for /in partition #5 of SCSl1 (0,0,0)(sda)..."


I couldn't seem to copy the text output of what it was doing to show, but it seems to only be giving out messages about "NetworkManager" and "supplicant connection state: completed -> group handshake" and "Group rekeying completed"

A while ago it was saying things like pulseaudio: ratelimit.c:76 events suppressed


Has something gone wrong or do I just have to wait it out?

My computer isn't normally very slow, desktop, with something like 4 gig ram and maybe a 2gighz processor? I don't know how to view the specs in ubuntu.

I've not installed an OS before... please any help, thanks!

---

### Post by perrojam on 2010-11-17
Ok.. so sticking "Creating ext4 file system for /in partition #5 of SCSl1 (0,0,0)(sda)..." into google as I should have done reveals that there is some problem in the partitioning...

I don't really know what to do concerning this. The install is still going but hasn't output anything for an hour (and then it was just a handshake).

I'd like to just cancel it now... I think I need to make a partition for it manually perhaps? How do I cancel it? I still want to install Ubuntu, don't want to leave it in a mess

---

### Post by Rubi1200 on 2010-11-17
Hi and welcome to the forums :)

The important thing right now is to stay calm and not do anything rash.

Since you are on the LiveUSB, go to Applications > Accessories > Terminal and post the output of this command:

```
sudo fdisk -lu
```

Thanks.

---

### Post by ravi2010 on 2010-12-09
i m installing ubuntu 10.04 along side window7 now.....i m having a ubuntu cd in my cd rom ....its been 1 and half hour ...still not moving from here......i m having good config fr laptop.....  it is not moving forward from.........."ready when you are"........i m getting irritated....but i love ubuntu........ can any one pls help me fast............

---

### Post by ravi2010 on 2010-12-09
hello rubi......i have ttyped the command wht u said in terminal and got this plz help me......




Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002eced

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   499800063   249796608    7  HPFS/NTFS
/dev/sda3       499800064   738284543   119242240    7  HPFS/NTFS
/dev/sda4       738285566   976771071   119242753    5  Extended
/dev/sda5       738285568   966995967   114355200   83  Linux
/dev/sda6       966998016   976771071     4886528   82  Linux swap / Solaris

---


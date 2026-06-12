---
title: "Installation issues"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by FullMetalPanic on 2011-01-30
Hello

I got a new Eeepc (Asus 1005PX Intel Atom N450,1GB Ram, 250GB HD) and wanted to install Ubuntu 10.10 netbook edition to go alongside Windows 7 starter.
After some hassle to get the netbook to actually launch ubuntu (I used Universal USB installer to install Ubuntu on a pendrive)  I tried installing it but for some reason the Ubuntu installer is not giving me the "Install alongside other operating system" option and only gives the "Erase and use entire disk." and "Specify partition manually (advanced)." options.
I don't want to erase my entire disk (want to keep Windows 7 handy in case I need it/my schools software does not work on Ubuntu) and I took a look at the Specify partition option but didn't get very far with it. 

Currently my Harddisk was already partitioned by Asus in C:\ which is prox 90 gig in size and houses windows and D:\ which is approx 120 gig in size and houses nothing at the moment.

In case of the partion screen it is set down as following:
Device---------------Type-------------Size------------Used
dev/sda1               NTSF                107374MB       28319MB
dev/sda2               FAT32                                          (This is the USB flashdrive I recon)
dev/sda3               NTSF                126556MB         3221MB
dev/sda4                                       21MB              unknown

I've looked for a guide on partitioning with Ubuntu but the guide seemed to be using an older Ubuntu installer and the PC in question already had a lot more partitions to I did not dare use it.

I hope I gave you the info you need to help.

Cheers

---

### Post by FullMetalPanic on 2011-01-30
Well I found myself another method. When I runned Wubi from the USB stick it did not give me the install inside windows option. Instead I formatted the USB flashdrive and put the .ISO on there and used Daemon tools to mount it. Runned Wubi again and there it was the Install Inside Windows option. Ubuntu is updating some programs etc as we speak so very soon I'm gonna go enjoy Ubuntu.

For the ones that took a look thnx for your time. But I got it resolved. 

(dunno how to change te topic to resolved tho)

---

### Post by kansasnoob on 2011-01-30
Stuff you should know about Wubi before updating Ubuntu:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by FullMetalPanic on 2011-01-30
Ah jeez....well back to finding a guide on partitioning I guess.

Am also getting a few issues with Ubuntu I need to take a look at. The sound does not work and I can't access my harddrives within Ubuntu.

Case...not closed.

Anyone know any noob friendly partitioning guides?

---

### Post by dino99 on 2011-01-30
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by FullMetalPanic on 2011-01-30
Thank you I'll take a look, hope it will somewhat explain itself a bit more as I jump in Gparted or parted magic.
To be honest it still looks a little bit like giberish to me so I hope some will explain itself.
Doing this for the first time so still gotta learn.

---

### Post by kansasnoob on 2011-01-30
> **FullMetalPanic said:**
> Thank you I'll take a look, hope it will somewhat explain itself a bit more as I jump in Gparted or parted magic.
To be honest it still looks a little bit like giberish to me so I hope some will explain itself.
Doing this for the first time so still gotta learn.

Wubi is fine if you follow that guide.

Your assumption here is wrong:

> In case of the partion screen it is set down as following:
Device---------------Type-------------Size------------Used
dev/sda1 NTSF 107374MB 28319MB
**dev/sda2 FAT32 (This is the USB flashdrive I recon)**
dev/sda3 NTSF 126556MB 3221MB
dev/sda4 21MB unknown

The dev part just means device!

The sd part just means hard drive!

The letter following sd indicates if it's drive #1, #2, etc.

The number following that indicates the partition number.

So sda = drive #1, and sda1 = drive #1, partition #1. Whereas sdb = drive #2, and sdb3 = drive #2, partition #3. Clear as mud?

But it appears that you have four primary partitions so we'd need to see the output of the Boot Info Script and a screenshot of Gparted before recommending an installation procedure:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

The screenshot of Gparted would tell us how much of each partition is used and how much is free.

---

### Post by FullMetalPanic on 2011-01-30
I've watched some video's guides on youtube and I think I'm gonna do the following:
1) Make a bootable USB with Ubuntu
2) Start Ubuntu and select Specify partition manually
3) I will then shrink down SDA3 down to get some free space
4) Select free space and choose New partition > Select Primary make it 12 gig large use Ext 4 file system and make the mount point /
5) Click new partition again select Logical make it 2 gig in size and then select use as Swap area
6) I have to make the /home one then but I'm not sure whats best at this point to be honest.

I would prefer to have access to all my diskspace and files in both Windows 7 and Ubuntu (if thats possible that is)

---

### Post by FullMetalPanic on 2011-01-30
Well small update
The space I freed for Ubuntu is put down as unusable in the installer so...thats a no go.

I'll just try the Wubi thing again and try and figure out how to access the harddisk in ubuntu.

I've been at this the whole freaking day and getting a bit tired now.

I'll do another atempt later on with this and just see how Ubuntu fares with the Wubi install. Thanks for the help so far guys.

---

### Post by FullMetalPanic on 2011-02-06
Been busy getting the sound to work. I used this guide:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Unfortunately I'm not getting very far with creating all the applications and such (accept for the ossxmix app and the GNOME/gstreamer bit): The stuff in this part:
[https://help.ubuntu.com/community/OpenSound#Configuring%20Applications%20to%20Use%20OSS](https://help.ubuntu.com/community/OpenSound#Configuring%20Applications%20to%20Use%20OSS)

I am getting sound now with on youtube (al be it not as loud as the volume should be even tho the slides in ossxmix are full opened)

Whats also annoying is that a few of my applications have vanished like:
Ubuntu Software Center
Empathy Internet Messaging
Rythmbox Music Player
Cheese Webcam Boot

If I could get the sofware center back I could probably find those others but...I have searched around a bit and did not find a way to install it again. 

So still got some problems to take care off.

---


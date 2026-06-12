---
title: "Installing Ubuntu into an existing partition"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by Barrier Reef on 2008-08-18
Hi there.  I'm a total Ubuntu newb, in fact I've never installed an OS before.  But my Windows is pretty messed up, and I'm making the switch.

What I'm trying to do is install Ubuntu in the partition of my main hard drive where Windows currently is.  (It's 4.6 GB, is that plenty of room for Ubuntu?)  I basically want to format the partition (I've heard exp3 is the best file system to use) and put all my Ubuntu stuff there.  I've tried to use the "guided" install, but it doesn't seem to recognize the partition that already exists on that drive.  It wants to use the whole drive.

I've also tried to use the manual install.  It recognizes the partition when I do it this way, but I don't know how to partition within that to set up a swap drive.  How big does my swap drive need to be?  And also, what should I use as my "mount point"?

I welcome all helpful comments to tell me how to install Ubuntu on the 4.6 GB partition on my main hard drive.  Thanks in advance!

---

### Post by falcon61102 on 2008-08-18
To set up Ubuntu, it is highly recommended that your establish 3 partitions.  One for Ubuntu system files, one for the SWAP and one for your Home directory which will contain all your personal information.

Your Ubuntu install is going to need at least 3 gig depending on how much you plan on installing, but I recommend from 4-10gig.  It's mount point needs to be "/" which signifies your root folder.

Your SWAP partition is typically twice the size of your RAM but if you have a really large amount of RAM, say 4 gig or more, you don't need to double it.  I have 4 gig and have never used my SWAP.  To establish your SWAP partition, create the size and then select SWAP as the type.

Your home partition is normally the rest of your entire drive unless you need the space for other things like other installs.  If you are planning on maintaining a rather small Ubuntu install, you can choose not to use a HOME partition but they are recommended in case something goes wrong with your install, it is easier to backup.  The mount point for the Home partition if you choose to use it is /Home. 

Hope that helps.

---

### Post by overdrank on 2008-08-18
> **Barrier Reef said:**
> Hi there.  I'm a total Ubuntu newb, in fact I've never installed an OS before.  But my Windows is pretty messed up, and I'm making the switch.

What I'm trying to do is install Ubuntu in the partition of my main hard drive where Windows currently is.  (It's 4.6 GB, is that plenty of room for Ubuntu?)  I basically want to format the partition (I've heard exp3 is the best file system to use) and put all my Ubuntu stuff there.  I've tried to use the "guided" install, but it doesn't seem to recognize the partition that already exists on that drive.  It wants to use the whole drive.

I've also tried to use the manual install.  It recognizes the partition when I do it this way, but I don't know how to partition within that to set up a swap drive.  How big does my swap drive need to be?  And also, what should I use as my "mount point"?

I welcome all helpful comments to tell me how to install Ubuntu on the 4.6 GB partition on my main hard drive.  Thanks in advance!

Hi and welcome, the minimum specs for ubuntu are 
System Requirements

Ubuntu is available for PC, 64-Bit PC and Intel based Mac architectures. At least 256 MB of RAM is required to run the alternate install CD (384MB of RAM is required to use the live CD based installer). Install requires at least 4 GB of disk space. 
So 4.6 gb might be enough. Your swap is usually twice the amount of memory, ie 256mb = 512mb swap. As for your mount point, that will be "/" for root. 
You may look at the mini edition
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Barrier Reef on 2008-08-18
Okay, cool.  So I think I should go ahead and create another partition for SWAP, then use the rest of my drive as my Home.  Will that interfere with the things already on the rest of my drive?

---

### Post by falcon61102 on 2008-08-18
If you already have other partitions established and wish to continue to use those partitions, then no, don't use an additional partition for your Home directory.  Creating a new partition to use the remainder of your drive would erase all of the existing ones and the data on them.

---


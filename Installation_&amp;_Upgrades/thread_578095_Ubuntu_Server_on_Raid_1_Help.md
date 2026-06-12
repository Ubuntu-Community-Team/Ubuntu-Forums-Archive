---
title: "Ubuntu Server on Raid 1 Help"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by xjrockx on 2007-10-16
Ok, well for starters I am completely new to the Ubuntu World.  I have tried doing some google/forum searches for help but no luck.  I have found a few posts with some info but none of it which seems to help.

Moving on, I am trying to setup Ubuntu Server (7.04) on a Raid1 Array.  I followed this guide [Here]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/").

Two problems I am having.

1.) It says I should install GRUB on both drives in the event Drive1 fails.  Following the directions on the page I get an error at step 1 (mount /dev/md0 /mnt) claiming that it is not possible.

2.) The rather larger problem, when I remove the Ubuntu CD from the drive and reboot I get an error message stating: Error loading operating system.

One thing I did find while searching made a claim to having to create a /boot partition.  If you look over the guide I followed, it doesn't mention having to create one (although it would seem obvious that I need to).

I am currently running 2xMaxtor SATA Drives (300GB).  Each disk is partitioned like so.
#1 Primary 297GB *Bootable*
#2 Primary 3.01GB

If I do need to create a /boot partition how should I re-partition my disks? How much space is needed? Do I need to create a /boot partition on both drives? Then do I need to create a MultiDisk Session for it? Any help is greatly appreciated, I am currently at a loss.  Thank you in advance.

---

### Post by xjrockx on 2007-10-16
Ok, for safe measure I went ahead and tried to install Ubuntu Server normally (no raid).  Come to find out that I am still getting the same:  Error loading operating system.  So now I am really stuck :confused:

---

### Post by xjrockx on 2007-10-17
Ok, so I don't feel very smart now.  It turns out that I forgot to disable the motherboards raid config.  It was still setup from a previous Win2K3 install.  Problem solved.

---


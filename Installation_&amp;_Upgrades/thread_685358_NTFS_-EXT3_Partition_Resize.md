---
title: "NTFS -EXT3 Partition Resize"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by infonote on 2008-02-02
Hi,

I have Ubuntu and Windows XP dual-boot on my laptop.
I want to increase my NTFS partition and obviously in the process decrease the Ext3 partition.

How can this be done?

Thanks in advance.

---

### Post by forestpixie on 2008-02-02
there is a version of gparted on the gutsy livecd which you could use if you have it, get  gparted livecd and boot with it or systemrescue has a gparted on it as well

once you're in - resize the ext3 partition and apply then resize the ntfs to take up the slack, if the partitions are not next to each other then you'll be needing to move partitions and get into reinstalling grub for obvious reasons

---

### Post by infonote on 2008-02-02
Thanks for the fast reply.

I made a mistake in the installation. I wanted to allocate 10GB for Ubuntu (first time installing it).

Instead I did the opposite. I gave 10GB to NTFS drive.
So I basically put in the Ubuntu CD and resize from there?

Thanks

---

### Post by forestpixie on 2008-02-02
yea you should be able to like that - but I do tend myself to use gparted as a livecd

[COLOR="Red"]make sure you have suitable backups[/COLOR] - if you lose power half way through you could have problems

it might take a long time - don't stop it half way through 

see you on the other side, good luck with the power fairies :D

---


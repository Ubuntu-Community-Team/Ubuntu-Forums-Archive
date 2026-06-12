---
title: "Resizing Partition for Ubuntu"
date: 2013-03-12
forum: Installation &amp; Upgrades
---

### Post by mayank2013 on 2013-03-12
Hi I am fairly new user to Ubuntu and recently installed 12.10
But during installation, i was checking the partition space and it by default kept 930 GB to Ubuntu partition

Can you guys suggest how do i go about fixing it and what should be the ideal partition...

So now the current status is :

Partition     File System   mount point             Size                      Used            Flags
/dev/sda1    ext4                  /                       923.5 GB               20 GB             Boot
        sda2     extended                                  8 GB
        sda 5    Linux Swap                              8 GB

Please help out, after this i need to create a new virtual box for Windows 7 , bcoz lot of my ollege work is in wondows

---

### Post by Bucky Ball on 2013-03-12
Boot from the install CD, 'Try Ubuntu' so you get to a desktop, launch Gparted, shrink sda1 to about 20Gb, create whatever other partitions you want/need.

As for your virtualisation, please post a thread in the Virtualisation sub-forum once you have resized your partition. Good luck.

PS: When installing you can choose 'Something Else' at the partitioning section and manually create partitions rather than let the install do it for you. You might want to reinstall and try that instead if you are not too far down the track with this install re customisation.

---

### Post by mayank2013 on 2013-03-12
Hi thanks,
Yes, i did install it just 2 days back, so not much important stuff there.
So, when you suggest reinstall, i did mine initially using a USB, so you suggest should i try it once more in same fashion ?

---

### Post by Bucky Ball on 2013-03-13
Yep. When you get to the partitioning section choose 'Something Else' and partition manually. Make a plan. Many people go for a separate /home partition as well. All normal mount points are selectable by default but you can create mount points named whatever you want.

/swap really only needs to be about 2Gb at the end of the drive unless you intend hibernating regularly. Then the size of your ram is normal for /swap.

/ = 20Gb
/home = large as you like
/swap = 2Gb (see above for hibernating)

One thing to remember is that Windows doesn't use EXT partitions and won't recognise them. That needs NTFS or FAT so you might want to create /share as an NTFS partition (Ubuntu handles NTFS and FAT no problem). 

Good luck.

---


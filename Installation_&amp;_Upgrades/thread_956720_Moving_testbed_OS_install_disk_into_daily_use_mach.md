---
title: "Moving testbed OS install disk into daily use machine"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by jboehm on 2008-10-23
Hi,

I've been building a new OS disk on a testbed machine.  I would like to now move the OS disk on to my daily use machine and start booting from it while preserving my old install in case I need to revert.  Here are the steps I think I need to take.

* Install the testbed disk
* Merge the testbed disk grub entries into the daily use grub menu.lst entries.  Is there anything special about this or is it basically copy and paste?
* Once I'm booting into the new version of the OS, edit fstab to mount the old OS volumes during the transition period.  One of the old volumes is a LVM how do I mount it?

I have a sneaky suspicion that it won't be this easy.

Thanks,
Jon

---

### Post by cariboo on 2008-10-23
If you can boot from your testbed disk, just hook it up to you computer and away you go. This is assuming that it is Linux or some other Unix like operating system. All the drivers that you need are included in a stock kernel. 

Make sure you have lvm2 installed on your test installation.

Have a look here regarding detecting and mounting LVM's

[http://www.knoppix.net/forum/viewtopic.php?p=114862](http://www.knoppix.net/forum/viewtopic.php?p=114862)

This is a knoppix web site but the commands will work just as well on Ubuntu.

Jim

---

### Post by jboehm on 2008-10-23
Yes, but how do I get my current grub to boot from the new testbed disk.  It won't know anything about it.

FYI: the new testbed OS is just the latest and greatest Ubuntu.  My issue is that this machine CAN'T have any functional down time.  So a transition and revert plan is needed.

Jon

---

### Post by jboehm on 2008-10-25
Here is a grub setup that I found works.  I may have to watch it closely as new kernels get installed.  It chainloads 2 grub installs.  The first is my stable OS install on disk0.  The second is my testbed OS install.

title           Mythbuntu
root            (hd1,0)
setup           (hd1,0)
map             (hd1) (hd0)
chainloader     +1
boot

This grub stanza was added to my stable OS /boot/grub/menu.lst.  When this entry is selected from the grub menu on boot from the stable OS disk, it then runs the grub install on the new testbed disk and boots.

Thanks,
Jon

---


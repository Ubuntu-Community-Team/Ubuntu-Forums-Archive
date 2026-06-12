---
title: "&quot;volume group name already in use&quot;"
date: 2006-09-09
forum: Installation &amp; Upgrades
---

### Post by kpm on 2006-09-09
"volume group name already in use"

This is the error(?) during an install of Ubuntu Server when I select to delete the entire hard disk and partition with LVM.  There was an installation of Dapper desktop on this machine.  Anyone know why this is??

Thanks

---

### Post by tatster on 2007-03-26
Hi,

I'm afraid I don't know why this is - but I do know that I've hit the same error and am now browsing for a solution!!!!

Tat.

---

### Post by jwinks on 2007-12-20
I am a complete Ubuntu *n00b* but I like the distro more than any other I've tried in 12 years of dabbling off-and-on with Linux. I had the same problem as I was setting up a Gutsy box to do home iSCSI chores. I have figured it out now. The problem is that even if you go into rescue and destroy the extended partition that contains the LVM volume, if you don't destroy the LVM volume inside it first, it's still there and as soon as the partitioner creates a new extended partition of the same geometry to hold a new LVM volume, lo and behold, it finds the old one already there. Go into rescue and use 

fdisk /dev/sda (or whatever your particular /dev node happens to be)

and start deleting partitions from the bottom up until there are none left. I kept trying to delete them top down and when fdisk was showing 3 partitions but I kept only being able to delete the first 2 and then it was empty; that set me off. Reading the LVM howto didn't hurt either.

Hope this helps somebody.

---


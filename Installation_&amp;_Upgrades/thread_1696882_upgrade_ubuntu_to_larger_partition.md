---
title: "upgrade ubuntu to larger partition"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by jkoval on 2011-02-28
I am running ubuntu 9.04 on a dual boot machine along with Windows XP
I have no room on the ubuntu partition to save any files.
I want to upgrade to ubuntu 9.10 or 10.10, but need a larger partition
for ubuntu
My plan is the following
1. uninstall 9.04
2. use Windows to defrag the disk and remove files, leaving more free space
3. install 9.10 (or 10.10) on a  partition larger than currently reserved for ubuntu

Is there any easier way to do this,
eg, do a fresh install of ubuntu 9.10, get a larger partition,
hopefully overwriting the current ubuntu partition.

---

### Post by yoneal on 2011-02-28
Yeah, you can do that. You can just delete files, defrag, resize partitions using gparted, then install a 10.10 over the 9.04. I think its faster than doing an upgrade from 9.04 to 10.10. Make sure your files are properly backed up first. :)

---

### Post by brallan on 2011-02-28
and if you save ALL of the files in your /home/YOURUSERNAME/ folder on an external drive (or even inside your windows partition), you can then still have all of your settings, desktop and info be the same by copying them over after install. Make sure to make all of the invisible files visible when you do this (in the nautilus file manager) by pressing Control + h, then when you are done with the install, copy them back into your home directory.

---

### Post by Dutch70 on 2011-02-28
I think I would go with 10.04 LTS, supported for 3 years, or 10.10, which you can upgrade directly to 11.04 in April. You can only upgrade from 1 distro to the next. 

Having a separate /home partition is a really good idea. 
check out this site, old, but good info, just ignore the FAT32 and use NTFS if you go that route. 

[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

---

### Post by jkoval on 2011-02-28
Thanks for the quick responses;
I will probably try this next weekend,
and get back to you then.
John Koval

---


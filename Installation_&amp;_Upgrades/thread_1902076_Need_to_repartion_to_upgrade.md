---
title: "Need to repartion to upgrade"
date: 2011-12-29
forum: Installation &amp; Upgrades
---

### Post by klemencic on 2011-12-29
I am, currently running Ubuntu 10.04 and wish to upgrade to 10.11 but upon starting the upgrade I am told that there is not enough free space on /
My current partition table is as follows
/dev/sdb/1 NTFS 97.66GB
/dev/sdb2  extended
/dev/sdb5 EXT4 158.32GB /home
/dev/sdb6 ext4 158.32GB /usr
/dev/sdb7 ext4 3.72GB /
/dev/sdb8 swap 3.72gb
/dev/sdb9 ext3 44GB /virtual

I run Gparted to try and shrink /home and /usr and grow / and the new partition table will be
/dev/sdb/1 NTFS 97.66GB
/dev/sdb2  extended
/dev/sdb5 EXT4 151.37GB /home
Unallocated 6.96GB
/dev/sdb6 ext4 151.37GB /usr
Unallocated 6.96GB
/dev/sdb7 ext4 3.72GB /
/dev/sdb8 swap 3.72gb
/dev/sdb9 ext3 44GB /virtual

The problem is when I try to grow / I receive a warning that by moving this partition I could cause problems with booting 

My question is if I go ahead and make these changes to the partition table will it cause problems with grub and booting the system

---

### Post by fantab on 2011-12-30
To solve and manage the "not enough space" issue read **[HERE]("http://ubuntuforums.org/showthread.php?t=898573")**.
 
However, your '/' partitons is too small, it should be minimum 10gb and no less. I have 15GB.
 
Your typo with Ubuntu version makes me assume that you want to upgrade to either 10.10 or 11.10. IMO internal upgrades are nearly always messy, I suggest you **do a clean install** of whatever version you want to upgrade to. 
 
Remember to** back up your data**. If you are upgrading to 11.10 is also suggest that you format /home partition too. The older configuration files and folders in /home MIGHT cause issues in 11.10. 
 
Personally, I don't think you need /usr and /home seperately one is enough. I use neither, just a 15GB / and a DATA partition. That is all. 
 
I hope this will solve your concern.

---


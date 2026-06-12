---
title: "How to make partition for sharing files Windows and Ubuntu"
date: 2015-07-06
forum: Installation &amp; Upgrades
---

### Post by evilanir on 2015-07-06
Hi,
I have Windows 7 and Ubuntu on my computer. I want to have partition for shared files on Windows and ubuntu, but I have just 4 primary partition and I can't do this.
I'm beginner in Ubuntu

In attachments is screenshot of GParted.

---

### Post by oldfred on 2015-07-06
You cannot make changes to mounted partitions.
So use the live installer which has gparted installed in it. If you had swap you would have to swap off. You may want to have a small swap partition of 2GB also.

You can then expand extended partition into the unallocated space and make as many logical partitions as you want inside the extended.

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by James_Ryan_Stortz on 2015-07-07
*post deleted by author.*

---


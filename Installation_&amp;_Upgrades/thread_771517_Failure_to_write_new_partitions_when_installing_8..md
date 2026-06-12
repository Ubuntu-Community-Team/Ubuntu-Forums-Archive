---
title: "Failure to write new partitions when installing 8.04"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by kf6swk on 2008-04-27
P400 computer, 17GB hard drive previously partitioned for Win2K.
Installing Ubuntu 8.04 proceeds normally up to partitioning.  The instaqller recognizes the drive as sda1, not hda 1.  Following set-up of partitions, installer refuses to write the new partitions.  Installation fails at that point.

Help/comments/further questions welcom.
Thanks  --  dwf

---

### Post by unutbu on 2008-04-27
Perhaps boot from the Live CD, run gparted. Set up your partitions as you would like them. Then try installing Ubuntu. If 8.04 installer is like 7.10, you  will be asked if you want a Guided or Manual partition installation. Choose manual and you should be able to set which partition you wish to install Ubuntu in.

Hope this helps. You might want to wait a bit, as others here might know of a better/easier way.

---


---
title: "Help with increasing user space on partition"
date: 2011-09-14
forum: Installation &amp; Upgrades
---

### Post by freakontour on 2011-09-14
So lm really new to ubuntu (as everyone posting seems to be) and what lm finding is l don't have enough space on the drive what a surprise seems a lot of people have the same issue so l have booted from the livecd and used gparted to increase the ntfs partition. Rebooted and still says only 5.0GB free!! yet there is still plenty of space on the drive. 

So l have dual installation with windows xp. I have installed ubuntu 11.04 using wubi. So on most the folders l open it says at the bottom no. files and 5.0GB Free apart from when l go into the host file which says 38.0GB free or something along those lines. So my questions are: 

Is ubuntu restricting the user here to around 5.0GB? if so is there anyway l can increase the users allocated space? As l don't really get the feeling this is a partition issue l could be wrong but if that was the case why wouldn't the host folder be restricted to 5.0GB also?

Please help this is doing my head right in!

---

### Post by fdrake on 2011-09-14
> **freakontour said:**
> So lm really new to ubuntu (as everyone posting seems to be) and what lm finding is l don't have enough space on the drive what a surprise seems a lot of people have the same issue so l have booted from the livecd and used gparted to increase the ntfs partition. Rebooted and still says only 5.0GB free!! yet there is still plenty of space on the drive. 

So l have dual installation with windows xp. I have installed ubuntu 11.04 using wubi. So on most the folders l open it says at the bottom no. files and 5.0GB Free apart from when l go into the host file which says 38.0GB free or something along those lines. So my questions are: 

Is ubuntu restricting the user here to around 5.0GB? if so is there anyway l can increase the users allocated space? As l don't really get the feeling this is a partition issue l could be wrong but if that was the case why wouldn't the host folder be restricted to 5.0GB also?

Please help this is doing my head right in!

wubi does not use partitions it's basically a program that uses a defined space (usually during install) from the original win partition (ntfs in your case) tecnically you have only 5 gb left in the os but parctically you have 38 (counting the whole win system). it's not really a big deal bacuase you can move your media and data to the host folder.

to increase the size of the wubi install follow the directions in this link or google around : [http://ubuntuforums.org/showpost.php?p=8858775&postcount=10](http://ubuntuforums.org/showpost.php?p=8858775&postcount=10), but keep in mind that you can still use all the space of the disk no matter what.

---

### Post by bcbc on 2011-09-14
Avoid LVPM - unfortunately it lists grub (legacy) as a dependent so will uninstall grub-pc (Grub2).

In addition to the wubi-add-virtual-disk mentioned in fdrake's link you can resize the virtual disk using this: [http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

Or best just to refer to the Wubi Guide as it contains the latest information: [https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F)

PS or it might be time to [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") to a direct install. (Wubi isn't really intended to use long-term.)

---

### Post by freakontour on 2011-09-14
Cheers for your help with this I'm beginning to understand this a bit more now.

> PS or it might be time to migrate to a direct install. (Wubi isn't really intended to use long-term.)

bcbc if l do migrate to a direct install will l have to give up windows xp also? or can l keep a dual boot?

---

### Post by bcbc on 2011-09-14
> **freakontour said:**
> Cheers for your help with this I'm beginning to understand this a bit more now.



bcbc if l do migrate to a direct install will l have to give up windows xp also? or can l keep a dual boot?

You can keep dual booting. You have to set up the partitions yourself prior to migrating though. 
If you follow that link to the Migration Howto I have included a link to a decent guide that shows how to partition.

---


---
title: "partition ruined hard disk"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by pangil on 2007-10-26
hi, i have 2 PCs at home that were previously running windows. i installed ubuntu on one PC, liking ubuntu, i tried installing it on the other PC. when i did a manual partition on the other PC with these
preferences:
#1 -  primary - 4GB - /
#2 - logical - 1GB - swap
#3 - logical - 15GB - /usr
#4 - logical - 20GB - /home

the installation went ok. but after restarting i got this error: 
GRUB loading stage1.5 Read Error

i tried repeating the installation this time using guided partition and using the entire disk but i still got
the same error. 
thinking that it there was probably something wrong with my installer, i installed debian. and i got the
very same error.
frustrated at having spent hours trying to get it to work, i went back to windows. when windows restarted during the installation i had a read error. 
so now i got 1 useless computer because it looks like the hard disk is ruined. 
could the partitioner have ruined my hard disk? is there still a way to fix it?

---

### Post by najeer on 2007-10-26
You have format the Master Boot Record because Windows desktop or Server does not like to share once you install it.  Get a copy of gparted now you are going to have to complete clean the drive and then do an installation of ubuntu.  Whatever version you have decided upon.

Second, I was looking for info on manually sizing partitions using ubuntu gusty gibbons any suggestions for an url?

---

### Post by rjs82vette on 2007-10-26
here are three way to fix it

boot into the windows recovery console, run fdisk and delete all the partitions.....and maybe do a mbrfix command

boot using the Ubuntu live cd, run gparted and delete all of the partitions....

boot using the hard drive manufacturers diagnostic cd and erase the entire drive

hope this helps.....

---

### Post by forestpixie on 2007-10-26
ytou could try using [supergrub]("http://supergrub.forjamari.linex.org/?section=download") to fix the start problem - then see if you're win is actually stiil present - or as suggested boot with the live cd and have a look in terminal at your partitions -

```
sudo fdisk -l
```

from hermanzone - this on grub stage 1.5 

```

This problem is more likely to occur when trying to boot up a newly installed system or after an internet update.
It can be caused by corrupted files in the /boot/grub directory.

You'll need to boot with Super Grub Disk, use the feature '[COLOR="Red"]direct boot[/COLOR]'
```

---

### Post by forestpixie on 2007-10-26
> **najeer said:**
> Second, I was looking for info on manually sizing partitions using ubuntu gusty gibbons any suggestions for an url?

what sort of info are you looking for? Why don't you use gparted as you've suggested to the op - I believe that the gparted on gutsy is a newer version than that on feisty

---

### Post by pangil on 2007-10-26
hi, i ran gparted to completely remove all of the partitions and started a fresh install using the
default settings. 
i still got the same error:
GRUB loading stage1.5 read error

unfortunately my hard drive did not come with a diagnostic CD. 
i'm really new to linux and i really don't know how to run super grub. can i get some help
concerning this? are there any other methods that i can try to fix my problem?

---


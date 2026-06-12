---
title: "How to uninstall ubuntu?  Don't have Windows XP disc"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by viciousdave on 2008-07-22
How do I uninstall Ubuntu?  Remove it, and than give all of my Windows XP back all of the space?  I do not have an original install disc of Windows XP as Dell never gave me one when I bought the computer.  So, how do I remove Ubuntu and only have XP and use all of my HDD again?

---

### Post by adelahunty on 2008-07-22
Can I just clarify - you have at least two partitions, one of which is Windows XP.  And you want to give the entire drive back to Windows?

---

### Post by rsambuca on 2008-07-22
Just use ms-sys to erase grub from your mbr, then you can use any program you want to delete the Ubuntu partition or perhaps just reformat it as ntfs and use it as a data/storage/media partition for your beloved Windows.  You can get ms-sys from the standard repos, so either use Synaptic Package Manager or ```
sudo apt-get install ms-sys
```

---

### Post by adelahunty on 2008-07-22
It is actually a very good idea to have a separate partition for files as rsambuca says: if you ever need to reinstall the OS, you can do so without touching your personal files.  So just formatting that partition as NTFS or VFAT within Windows or the live CD of Ubuntu is fine.

Failing that, and you want one, big partition instead....  Bit trickier.  You need a partition manager that will resize in place.  I'm not too sure about Windows - I only use it once in a while, or World Of Warcraft! - but Partition Magic will do it for you (at a price).  I have a feeling there's a program called BootIt Next Generation (or something like that) which is also worth a look, as it has a free trial period.  So I'm told....

In Vista, there's a wizard to help you do this anyway, which would make life easier.  Perhaps Microsoft is counting on lots of people getting disillusioned with Linux...? ;)

---

### Post by rsambuca on 2008-07-22
gParted will also resize existing partitions, but on the odd occassion, errors can occur (as with any partitioning program).  I strongly suggest just keeping it as a separate partition.

---


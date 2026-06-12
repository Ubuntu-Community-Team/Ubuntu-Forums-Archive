---
title: "Go from no RAID to RAID1?"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by yatzr on 2008-05-28
I installed Ubuntu 8.04 without any RAID.  I just didn't see any options for it while I was installing.  I have two hard drives in the machine and I partitioned each the same.  Disk1 has partitions "/boot", "/swap", and "/".  Disk 2 has partitions "/boot2", "/swap", and "/disk2".  The install all went onto Disk1.  Now, I want to setup a RAID1 without having to reinstall.  Is this possible?

Note: I'm very new to Ubuntu and Linux in general, so please try to explain things in detail.  Thanks :)

---

### Post by dstew on 2008-05-28
It seems possible in theory. RAID1 is mirrored. If you don't have anything on disk 2, I think you could create the RAID1 using mdadm. But I am not sure about that.

Did you use the Alternate Install CD? I think only the Alternate Install has the steps to configure and install to a software RAID. If you can't get your RAID assembled (or destroy your installation in the process!) then use the Alternate Install CD to reinstall, and you should be OK from the start. I used it to install a small RAID1 array with a /boot partition, and a larger RAID5 for everything else. You need a RAID1 for booting, because the boot loader grub does not have built-in software RAID capability. It just thinks the first disk of the RAID1 is a regular disk, so it can load the kernel from there. But, grub cannot boot from striped RAID.

---

### Post by yatzr on 2008-05-29
I'm not sure if I used the alternate cd as I got it from someone else.  Good to know for the future though.

I searched around for mdadm stuff and ran across a guide to do this very thing.
[http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch)
I followed it exactly and it worked perfectly!  Now I just need to figure out how to get it to alert me if something happens.

---


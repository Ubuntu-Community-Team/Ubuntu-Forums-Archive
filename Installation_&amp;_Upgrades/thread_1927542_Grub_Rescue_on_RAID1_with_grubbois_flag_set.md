---
title: "Grub Rescue on RAID1 with grubbois flag set"
date: 2012-02-18
forum: Installation &amp; Upgrades
---

### Post by vncoder on 2012-02-18
Hello all,
   I have 2 x 2T HDDs that I want to RAID1 on all the partitions with Ubuntu 11.10 using the Alternative disk image. After many failed attempts with "grub failed to install on /dev/sdb", I found that I need to go back to MSDOS partition table or need a small partition on each disk with grub_bios flag set. When I chose to use MSDOS partition, the installation installed grub to both /dev/sda and /dev/sdb without any problem but boot into GRUB prompt. 
So, Irecreated the partition table using GPT with 1MB partition set grub_bios flag on on each disk (not raided) and other partitions raid1. Again, grub installed on /dev/sdb without any error messages. However, when I boot up I got grub rescue prompt instead.
I need any pointers I can get to install Ubuntu with RAID1 using GPT. However, I am nearing to the point of giving up on RAID1 altogether.
Please help.

---

### Post by darkod on 2012-02-18
Is this software raid we are talking about or fakeraid?

---

### Post by vncoder on 2012-02-18
This is software raid. 

Initially, I tried to be "smart" and put the small bios_grub partition onto the raid1 as well but doesn't boot either (I can not remember what I got now...tried so many different ways to remember exact result of each one). 

Now, I have recreated the partition table but only get the grub rescue prompt.

I managed to installed 10.04 from the alternative disk image but after I do a release upgrade to the latest version, I got a grub rescue prompt as well.

---


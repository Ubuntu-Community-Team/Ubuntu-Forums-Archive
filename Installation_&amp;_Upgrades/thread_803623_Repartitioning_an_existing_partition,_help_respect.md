---
title: "Repartitioning an existing partition, help respectfully requested"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by wilc on 2008-05-22
I have a 250g hdd with windows xp installed on it.  It has 2 ntfs partitions currently, one is 8g of free space, the other is the rest of the drive, about 240gigs of which I currently have about 80 gigs used.

My questions, can I safely repartition the approximately 240 gigs that windows is now on, or do I need to wipe the system, repartition, and reinstall both operating systems from scratch?  If it is in fact safe to repartition the partition that windows inhabits a portion of, how do it do it?  Do I do it from windows or from the Ubuntu cd or with some other program?

---

### Post by dccrens on 2008-05-22
You can use GPARTED. I dl'ed it and created a bootable CD to boot from and then you can resize your existing partitions to create new ones for linux. No need to reinstall  windows. Then you can install Ubuntu and Grub as the boot loader. It will allow you to select which OS to run on bootup.

---

### Post by wilc on 2008-05-22
Thank you very much, I have just one clarification question.

I thought I saw gparted in the list of applications when I booted to the livecd, can I use that from within Ubuntu to make the partitions or should I download it and do it from outside the OS?

Thank you again for your help.

---

### Post by wilc on 2008-05-22
Thank you very much, I have just one clarification question.

I thought I saw gparted in the list of applications when I booted to the livecd, can I use that from within Ubuntu to make the partitions or should I download it and do it from outside the OS?

Thank you again for your help.

---

### Post by forestpixie on 2008-05-22
You can use the version on the livecd, but some will say use a gparted livecd, I use partedmagic as a livecd.

If it works with livecd that's enough, if you have problems get a partition editor as a livecd and use that.

---

### Post by wilc on 2008-05-22
Thank you

---


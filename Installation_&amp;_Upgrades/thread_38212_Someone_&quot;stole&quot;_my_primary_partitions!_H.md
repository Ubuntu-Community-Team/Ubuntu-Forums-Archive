---
title: "Someone &quot;stole&quot; my primary partitions! Help"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by saintsel on 2005-05-30
I'm going to install Ubuntu and have a dual-boot with XP. I was thinking about having one partition for XP, one for Ubuntu, one for swap and one FAT32 for datasharing. But, I noticed that Dell (I have a Dell Inspiron 2200 Laptop) have "stole" two of my primary partitions for PC Resotre and some other things, which I don't think it's smart to delete. 

This leaves me with two primary (or one primary and many logical) partisions for XP, Ubuntu, swap and the datasharing. I read in the dualboot-howto that all these should be primary. But I can't se how I could make this happen. I guess I could drop the datashare partition, but what do I with the swap?

Hope somebody got any ideas !  :)

---

### Post by tread on 2005-05-30
Read up about the dell partition .. it is my belief that you can remove these (they arent useful unless you backup using some software regularly). But I don't have a Dell, so I could be wrong :) A friend of mine owns one though and he deleted the partition (there was only one on his machine)

---

### Post by saintsel on 2005-05-31
[QUOTE=tread]Read up about the dell partition .. it is my belief that you can remove these (they arent useful unless you backup using some software regularly). But I don't have a Dell, so I could be wrong :) A friend of mine owns one though and he deleted the partition (there was only one on his machine)[/QUOTE]
 You are absolutely right! I found out that I can burn a recovery CD from that partition (instead of having a recovery partition), and then delete both of the dell partitions.

---

### Post by BeeZ on 2005-05-31
lol

---

### Post by saintsel on 2005-05-31
I have deleted only one of the partitions so far, because the last one could be useful. So I'm wondering, are there any problems with having the swap and datashare on logical partitions?

---

### Post by mingus on 2005-05-31
Hmm . . . I would double-check re that last partition.  I don't have experience with Dell specifically, but with a bunch of other laptops.  

Are you sure it's not a hibernate partition?  The recovery partition is a no-brainer.  It just holds i386 because M$ won't let Dell give you install media like in the old days.  This partition allows you to restore the laptop to its original state or install new programs which may require uninstalled libraries, etc.  It's good that you created a CD copy.  (BTW, there is a technique by which you could make that recovery CD bootable, which might be handy.)

The hibernate partition is a different animal altogether.  If that is what it is, I suggest you check Dell docm because you will probably need to disable this in the BIOS, etc.  One of my Omnibooks got very upset about deleting this partition.  Also check to make sure that your kernel is not trying to enable this feature.

As far as your initial question, unless there is something unique to this laptop, shouldn't be a problem.  I looked in the dualboot howto and saw the ref to only using primaries, but I missed the explanation why?  If memory serves, IDE can handle up to 63 partitions.  On the box I'm typing on here are 14 with 6 distros plus XP and 2 shared vfat so I can read/write from either Windows or Linux.  I use grub to multi-boot, it just does a chain-loader to boot Windows.

One other token of unsolicited advice:  When you install Ubuntu, if you have a bootable floppy drive, consider initially putting grub on a floppy.  **Many** users are getting their MBR hosed and don't have the recovery media or know-how to restore the Windows MBR.  Putting grub on the floppy safely allows you to make sure everything is working as you wish and that in a jam you can still get into Windows.  After you're settled, you can then install grub to the MBR or install it to / and use the XP boot loader.

---


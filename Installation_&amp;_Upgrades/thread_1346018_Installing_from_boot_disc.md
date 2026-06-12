---
title: "Installing from boot disc"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by WeaponsTheyFear on 2009-12-04
I am having a bit of trouble.  I recently upgraded to 9.10 and now upon booting things get crazy, and half the time I can't get into Ubuntu.  If I press ESC when Grub is loading, I can select one of the options and that usually works, but I want to start fresh.

When booting, if I choose to boot from disc it just continues to load the grub.  I want to install fresh with 9.10 and am having trouble figuring out how to do that once UBuntu loads ( if its possible ).

---

### Post by darkod on 2009-12-04
Did you burn the image on the CD correctly? If you tell it to boot from cd you should not see grub or the computer should not boot from the hdd.

---

### Post by presence1960 on 2009-12-04
> **WeaponsTheyFear said:**
> I am having a bit of trouble.  I recently upgraded to 9.10 and now upon booting things get crazy, and half the time I can't get into Ubuntu.  If I press ESC when Grub is loading, I can select one of the options and that usually works, but I want to start fresh.

When booting, if I choose to boot from disc it just continues to load the grub.  I want to install fresh with 9.10 and am having trouble figuring out how to do that once UBuntu loads ( if its possible ).

I would start from the beginning:

You have downloaded the iso. Did you MD5SUM the iso?
Did you burn the iso as an image to CD at 4x-8x speed? Speed is critical when burning an iso as an image to create a bootable medium. Fast speeds are OK for data files, but with an image if one piece of info has an error the CD will not work properly or not install the OS properly if at all. If your CD burning software does not give the option of choosing burn speeds between 4x-8x see here for Infra Recorder.

When you boot the CD make sure the CD/DVD drive is set to boot first in BIOS. When the CD loads and you get to the menu choose "check disk for defects" prior to doing anything else. If the disk checks out OK then install Ubuntu.

---

### Post by WeaponsTheyFear on 2009-12-04
Yes, I am fairly sure it burned correctly, I've made many other Ubuntu discs before that all turned out fine.  Whole computer has been acting weird lately since the upgrade.

For example, sometimes it will boot telling me that it has to use limited display or something, and whether I should exit to login, continue for just this session, and so on.

I will try reburning and see if that helps at all.

---


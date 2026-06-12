---
title: "Ubuntu Lucid Hardware RAID (3ware controller issue)"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by DeaconBlues on 2010-05-03
Hi there,

I just shrank (shrunk?) my Windows 7 partition on my 3ware RAID card to allow space for the latest Ubuntu so that I could have dual boot.

I've got 2 drives in RAID 0 going through a 3ware 9500SE controller, so Windows sees them as a single drive.

During past experimentation with Ubuntu it always saw them as 2 drives, despite the hardware controller. The new version lets you specify the controller when manually creating partitions though.

Great! I thought, they've simplified the partition manager.

However after formatting and installing (which took the longest time for any version of Ubuntu I've tried since Gibbon) my MBR is buggered.

I've tried all the options on the Super Grub Disk and I'm back into Windows 7 as I type this but I can't access my fresh installation of Lucid Lynx.

Any ideas??

---

### Post by DeaconBlues on 2010-05-03
I solved it using this post:

[http://ubuntuforums.org/showpost.php?p=9096940&postcount=1](http://ubuntuforums.org/showpost.php?p=9096940&postcount=1)

Although I found out my RAID setup was on sdb4, so wherever Saraslife used sda5 I substituted.

Now I've got 7 and Ubuntu dual boot.

:D

Edit: Interestingly /media/sdb4 no longer exists after rebooting, so maybe that was a temporary directory just to force the bootloader onto the drive. Someone more techy than me will know why.

---


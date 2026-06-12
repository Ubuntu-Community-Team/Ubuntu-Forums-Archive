---
title: "Major issue with dual-booting when Windows recovery partition exists"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by lexpython on 2010-06-11
I have encountered this on several new laptops recently, dug around a bit, and found nothing.

So: Newer laptops shipping with Windows 7 almost always have a recovery partition in front of the "C" drive.  On two laptops I've tried to dual-boot, Windows seems to overwrite and/or corrupt GRUB so that it won't boot into either OS.  I then have to boot from a Live disk & edit the boot to make it temporarily work.

On both computers, I've had to install EasyBCD into Windows to get it to boot consistently to Windows, but it knocks out GRUB and will not boot to Ubuntu.

I feel that if I am having this trouble, a lot of people must be.  Most of them probably just give up without checking here first.

I do not want to do an install inside Windows.  I want to use a separate true partition (EXT4) so when Windows dies I can access data. 

This manufacturer decision to use recovery partitions that seem to overwrite GRUB could be a major blow to Ubuntu, and linux in general.  Most people are just going to quit in frustration.

---

### Post by darkod on 2010-06-11
I don't think it's specifically because of the recovery partition. But I hate that kind of setup too, purely because it doesn't offer any real recovery at all. Even if using only windows, if you make second ntfs partition so you can format and reinstall if you want without losing the data, you can't because they never give you install media and the recovery partition usually wipes the whole disk (including your second ntfs partition with your data on it). Awful way to treat your customers paying for license.

Back to the topic. Most often losing grub after booting windows is related to some crappy software running in the background that they don't even tell you about. Dell and HP/Compaq are known to do this.

This is one post for Dell, it seems it's called DataSafe:
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

I have definitely heard HP doing something similar, but I have no idea if removing it is easy as it sounds for Dell DataSafe.

Also, this "problem" relates only to grub2 because it's larger in size than grub1. Usually grub1 on the MBR would be fine even with this software running. But grub2 on the MBR has a part of it chopped off every time you boot windows and it can't function.

---

### Post by lexpython on 2010-06-11
Ahhh, the issue was on a Dell, both times, both running Data-safe.

My girlfriend (yes geeks can have girlfriends too) just got a Toshiba E505 and I've been worried about dual-booting for the GRUB reason - it took several hours each time and then ended up as Windows 7 only anyway.

If I can get her computer to boot off a Live CD (no luck so far with 10.04 NBR, 10.04 standard or 9.10 NBR), I'm going to give it a try.

Thanks for the info on Dell "DataSafe".  That seems kind of rotten to me, and exclusive of Ubuntu.

---


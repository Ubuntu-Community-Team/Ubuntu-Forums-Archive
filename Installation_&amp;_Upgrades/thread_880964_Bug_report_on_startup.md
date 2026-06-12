---
title: "Bug report on startup?"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by IronLionZion87 on 2008-08-05
So I was having troubles installing but after using the alternate install it worked just fine.  But after the point where it tells you to remove the disk and let it reboot everything goes wrong

I remove the disk and select reboot.  and after the loading screen I get what appears to be a bug report.


Bug: soft lockup - CPU#1 stuck for 11s! [rc:4927]

The next time I try I get a segmentation Fault.

It just seems like every time I try to boot up I get a different error



before this second attempt at an install I formatted the disk ext3, through advice from other forums.  Any ideas?

---

### Post by Kevbert on 2008-08-05
Please try running the memory test (it's a menu item on the CD).

---

### Post by Qchan on 2008-08-05
> **IronLionZion87 said:**
> So I was having troubles installing but after using the alternate install it worked just fine.  But after the point where it tells you to remove the disk and let it reboot everything goes wrong

I remove the disk and select reboot.  and after the loading screen I get what appears to be a bug report.


Bug: soft lockup - CPU#1 stuck for 11s! [rc:4927]

The next time I try I get a segmentation Fault.

It just seems like every time I try to boot up I get a different error



before this second attempt at an install I formatted the disk ext3, through advice from other forums.  Any ideas?

[b][color=darkred]
Sounds like a HDD corruption issue. You may need to run fsck -a.

To do that, boot Ubuntu through to the CD. Once you get to the desktop, click Applications --> Accessories --> Terminal. In terminal, type sudo fdisk -l   This will help us identify which HDD it is we need to run fsck on. It may look like this:

> 
/dev/hda1


...Or something similar. Once you find that, you want to type

fsck -a /dev/hda1

If you get an error about it being mounted (you shouldn't), then make sure the drive isn't showing on the desktop. If it is, right click on the drive icon and click "Unmount volume". After that, try the command again in terminal.
[/b][/color]

---

### Post by IronLionZion87 on 2008-08-05
well no I try booting from both versions of the desktop disks and neither will let me even boot right in from the CD.  I get many of the same errors.


I made sure to check the integrity of each Iso before I burned. I formatted as ext3, and once as ext2.
I've checked my hardware and chipeset...everything is compatible



I'm running Memtest86 atm and so far I've had 10 pass / 0 error.  clocking like 3 and a half hours so far.

---

### Post by Kevbert on 2008-08-06
Looks more and more like a bug.  It may be worth asking a question in Launchpad (where bugs are filed and where the Ubuntu programmers can be contacted).  You'll need to register on the [[COLOR="Red"]website[/COLOR]]("https://launchpad.net/").  Then hit the Answer Tab and enter your problem.

---


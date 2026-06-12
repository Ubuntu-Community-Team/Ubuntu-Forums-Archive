---
title: "error 18"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by zoelindamain on 2007-05-23
I installed Ubuntu on an older computer (Win 98 ) in order to  basically update it. It will run from the disc, but after I install, and it says to remove the disc and reboot, the only screen I get is the MS-DOS black screen with white letters that says:
[B]GRUB loading stage1.5.
GRUB loading, please wait...
Error 18[/B]
Please HELP!!!! SOON!!! This is a computer that was given to us and I had planned on using it for my home business.
thank you

---

### Post by apunc1 on 2007-05-23
from [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

> You could check at your motherboard manufacturer's website, (find it with google), to see if there is a newer update for your machine's BIOS available. If so, you can download it and try 'flashing the BIOS'.  That has been reported to have solved this problem.

If you don't think that could be your problem, or there is no more modern BIOS flash avialable for your BIOS, then just make sure your hard disk is being correctly detected and set up in the BIOS.
Quote:
" I had the same problem. Error 18 and After GRUB. The solution is in the bios.
Put the hard disk detection on auto and not on user. It did the trick for me."
The old 8.0 GB limit was overcome when the old CHS (Cylinder, Heads, Sectors) method for dealing with hard disk addressing (disk geometry) was replaced by LBA (Logical Block Addressing). (Numbering each sector of the hard disk starting with the MBR and counting upwards).  Make sure LBA is enabled in your BIOS. If LBA is already enabled, try switching to 'normal' mode and see if that helps.

Yet another way of coping this problem which is reported to have worked for several people is to just try reducing the size of the Linux partition. (So it will be inside the limit).
I have participated in one web forum thread where this solved the problem.
I have read of three separate instances where users claimed that installing Linux '/' (root) on a logical partition instead of a primary partition cleared this problem up for them.

A famous Linux method for fixing this problem in the old days when they had the 8.0 GB limit was to create a separate /boot partition within the 8.0 GB limit, and install Grub in that. Then they could boot a Linux partition which was outside the limit, enabling Linux users to use larger disks with Windows installed within the 8.0 GB limit and Linux's root filesystem outside  the limit. 

The use of 'Disk Manager' software is another possibility. It be installed (usually to the first track of the hard disk) to help the BIOS read a larger hard disk than it can normally support. For example 'OnTrack Disk Manager'. That might be worth looking into, although I have not read any reports yet from anyone who has tested it.


---


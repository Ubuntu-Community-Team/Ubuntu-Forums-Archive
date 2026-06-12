---
title: "Reinstalling Grub - Dual Boot Dual Drive Windows XP and Ubuntu Gutsy"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by morning_napalm on 2008-06-08
I have a Dell Dimension 2400 that I have 2 hard drives installed.  I had Windows XP on one drive and Ubuntu Gutsy on the other drive and everything was fine.  Then my Windows drive crashed and I had to replace it and reinstall (Dell recovery disk) Windows XP.  I now have Windows XP reinstalled and have the previous installation of Gutsy on the other drive.

The problem is that my Grub is gone.  If I understand how this works, the previous Grub setup was somehow attached to the drive that crashed (where the Windows MBR was).  So now I have no way to boot into my Ubuntu drive.  I can only get to Windows XP.

I have looked for fixes, but have not quite found a solution.  I did try the Quick Start instructions here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

and it looks like it created a Grub menu, but it is in the /boot directory on the  Linux drive and it doesn't do anything.

I also tried reinstalling from the Live CD, selecting my /, /home, and swap partitions and not formatting (from some other posts), but the installer won't continue without reformating the / partition.

I would appreciate any help on how to fix this.

Thanks.

---

### Post by mikewhatever on 2008-06-08
Reinstalling grub as shown in the guide you linked too, should also put it to the MBR of the first HDD with 'grub> setup (hd0)'. You should be able to boot Ubuntu after running the setup. If you haven't done it yet, backup the old menu.lst first.

---

### Post by Driver on 2008-06-08
New Thread Started

---

### Post by meierfra. on 2008-06-09
Driver:  Please start your own thread, use  the regular font size  and get rid of the colors.

---


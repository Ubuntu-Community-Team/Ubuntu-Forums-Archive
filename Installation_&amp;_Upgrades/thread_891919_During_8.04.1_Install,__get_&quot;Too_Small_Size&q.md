---
title: "During 8.04.1 Install,  get &quot;Too Small Size&quot; msg"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by kn4hh on 2008-08-16
I am attempting to install release 8.04.1 on a laptop with Windows XP currently residing on it.  I defragged the drive and booted from the CD image.  When I get to the "Prepare Disk Space" part of the installation, it gives me a suggested partition of 14.5 gb for Ubuntu which should be more than adequate.  However, when I select the Guided-resize option of 22.8gb for XP and 14.5gb for Ub, I get an error message "Too small size".  I tried to manually partition the hard drive and I receive the same error no matter what the partition size I use.

Suggestions, please.

Many thanks, Bob

---

### Post by crogers45 on 2008-08-25
I have the exact same issue.  I installed Ubuntu with no issues on my newer notebook with Vista but I get the error mentioned here when I try the same thing on my wife's which has XP.  Output from fdisk is as follows :
quote -
Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        8939    71762355    7  HPFS/NTFS
/dev/sda3            8940        9545     4867695   db  CP/M / CTOS / ...
endquote

When in XP it tells me that 40% of the disk is free.

Any ideas?

---

### Post by jaredjd on 2008-09-06
I am having the same problem as well. Any ideas?

---

### Post by ernieball on 2008-09-19
Consider this a bump... I have a 47GB partition with XP on the other partition and get the same error. Peculiar enough I recently installed Ubuntu on another HP-machine w/XP, where I remember getting a co-exist with XP-option (which I didn't use). Now I wanna install on an Acer Aspire and cannot find this option... Is this a hardware-issue..?

---

### Post by jerome1232 on 2008-09-19
> **kn4hh said:**
> I am attempting to install release 8.04.1 on a laptop with Windows XP currently residing on it.  I defragged the drive and booted from the CD image.  When I get to the "Prepare Disk Space" part of the installation, it gives me a suggested partition of 14.5 gb for Ubuntu which should be more than adequate.  However, when I select the Guided-resize option of 22.8gb for XP and 14.5gb for Ub, I get an error message "Too small size".  I tried to manually partition the hard drive and I receive the same error no matter what the partition size I use.

Suggestions, please.

Many thanks, Bob

How full is that NTFS partition, Gparted won't resize it to a point where your going to lose data because the partition is now to small to fit the data it previously contained

---

### Post by ernieball on 2008-09-19
Quick answer !! :)
Well, I have a completely empy 47GB newly NTFS-formatted partition. Is the NTFS the problem. How do I work around this...?
Answers highly appreciated..:)

---

### Post by Somekindofsuperhacker? on 2008-10-23
I think the reason this error pops up is because you are trying to proceed with a Windows partition smaller than the amount of space you currently have allocated for Windows + files.

If you're doing the Guided partitioning, click+drag the area between the Windows partition and the proposed Ubuntu partition and give Windows a few more gigs of free space so you're not at 0% disk free next time you boot into Windows.

I hope that is the solution for you.  Appologies if you already knew that.

---


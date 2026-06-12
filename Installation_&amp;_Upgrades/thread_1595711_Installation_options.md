---
title: "Installation options"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by Torqumada286 on 2010-10-13
My upgrade form 10.4 to 10.10 messed my system up so it won't go beyond the log in screen, so I figured I will probably just do a wipe and start fresh.  Currently my system is a triple boot system with Ubuntu/XP64/Win7RC, though I hardly use that anymore.  Ubuntu is on a 300gb drive, XP64 is on an 80gb and Win7RC is on a 500gb.  Now, if using the LiveCD version I determine that my home folder data is still good on the Ubuntu drive, even if I can't currently boot into it, is the following a good option for me?

To begin with, using the LiveCD, I mount the 300gb drive and backup my home folder to an external drive. Reboot, install 10.10 on the 300gb or 500gb drive with the LiveCD, wipe the drive Ubuntu wasn't installed on and adjust GRUB to keep the XP drive current until I eventually swap over to a full version of Windows7.  It will be easy to copy the backup home directory over to the newly blank drive, but I am a bit confused on how to get Ubutnu to recognise it.  I have read [this](https://help.ubuntu.com/community/Partitioning/Home/Moving) tutorial, but I am still not quite sure what to do.  Some clarification would be great as well as a critique of my plan.

Thank you in advance for the help.

Torqumada

---

### Post by aromo on 2010-10-13
If you plan to wipe out the Win7RC disk (500gb).  You can do so with gparted and format it (NTFS, ext3 or ext4).  Then when you boot from the live CD, you can use the disk management tool to mount your Ubuntu disk (300gb the one with the data) and the formatted disk (500gb), transfer your data and install the OS on your 300gb disk.

While installing it you might want to consider creating a separate partition for your data, that way you just have to wipe out the system partition(s) should you run into trouble again.

My 2 cents.

---

### Post by Torqumada286 on 2010-10-13
> **aromo said:**
> 
While installing it you might want to consider creating a separate partition for your data, that way you just have to wipe out the system partition(s) should you run into trouble again.


Isn't that what I am doing by backing up the home directory and placing it on a different drive?

Torqumada

---

### Post by Torqumada286 on 2010-10-14
When I try to move or backup my old home file under the LiveCD, I am told that I don't have permission to do so.  I can look at it and all the data is safe there.  If I just leave it on the 300gb drive and install 10.10 on the 500gb drive, I can make Ubuntu point to my old home directory and not lose my settings?

Torqumada

---


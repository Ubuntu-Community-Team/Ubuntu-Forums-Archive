---
title: "Ubuntu already on IDE. Want to Install Windows XP on SATA."
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by capricon on 2008-08-15
My knowledge: Heard about GRUB etc but know almost nothing about it :-)

I have Ubuntu (7.04) installed on my PC's current single HDD (IDE).

Now i have a new SATA HDD and i want to install Windows XP Professional in it and dual boot preferably with Ubuntu as default boot.

Could someone give me some details as to how?

Thanks a lot.

---

### Post by louieb on 2008-08-15
Can't give a specific how to - its hardware and BIOS dependent.

What I would do is is unplug the Ubuntu drive, plug in the sata drive, install xp, plug the IDE drive with Ubuntu back in. Boot it up and see what happens (does Grub or XP boot)?

Do you know how boot order is set on that PC? On some PCs it can be set in the BIOS setup. On some the there is a different key you can press to tell it what device to boot to.   

Anyway with a little tweaking it can be set up just the way you want.

---

### Post by oldos2er on 2008-08-15
After you've installed WinXP, you'll need to restore grub. See 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---


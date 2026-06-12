---
title: "Vista...won't load after uninstalling 7.10"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by DeadToad on 2007-10-25
I have Windows Vista on one partition, Ubuntu 7.10 on another.
I ran KillDisk to remove Ubuntu 7.10
Now, when I reboot, GRUB comes up with Error 17, and I cannot boot into Vista.
How do I remove GRUB completely to boot back into Vista?
Thank you for your help.
DeadToad

---

### Post by MaximusTG on 2007-10-25
The reason it won't boot is because the portion of grub that is in your MBR (master boot record) points to /boot/grub/menu.lst in your Ubuntu installation (which you deleted) to fix this:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Put in your vista disc, load the recovery environment, then run

bootrec.exe /FixMbr

---

### Post by DeadToad on 2007-10-25
Maximus TG, thanks for the help.
I do not have a Vista CD or DVD.
I have a HP laptop with Vista preinstalled.  I had to make a recovery DVD, which includes Vista and all software and hardware drivers.
How do I get to Vista Recovery to fix my MBR if I can't boot into Recovery mode?
Thanks again.
DeadToad

---

### Post by peabody on 2007-10-25
Are you sure you didn't get a CD???  I find that very odd, while most laptops don't come with CDs for the software installed on them these days, I've yet to see a retail laptop not come with system software CD.  My Compaq Presario C571NR came with a Vista CD.  I'd highly doubt that a Vista CD wouldn't come with an HP laptop.  If you bought it used, you should have insisted on getting a system software CD.

---

### Post by kellemes on 2007-10-25
Download/Burn/Boot from [Super grub Disk]("http://supergrub.forjamari.linex.org/")

1-  Boot SuperGrubDisk.
2-  Select language
3-  Select Windows
4-  Select Fix Boot of Windows

Good luck.

---

### Post by DeadToad on 2007-10-25
peabody,
No, most computers come today requiring you to make "restoration" CD/DVDs. You do not get an OS CD/DVD separately.  You were lucky.  My HP Pavilion dv9000z did not come with a Vista DVD.  I had to burn the "restoration" DVDs (2).
It is new, not used.

kellemes, I had already downloaded SuperGrub, and can boot into Windows if I have the CD inserted, but if I remove it, I cannot boot to Windows.
I will follow your instructions as listed.

Thank both of you for your help.
DeadToad.

---

### Post by DeadToad on 2007-10-25
kellemes,
After following your instructions using SuperGrubDisk, and 6 more attempts at fixing the MBR, and after 8 reboots, I am now able to boot to Vista again.
Thanks for everyone's help.
DeadToad

---


---
title: "Replacing Vista in Triple boot system"
date: 2011-12-30
forum: Installation &amp; Upgrades
---

### Post by BLaZuRE on 2011-12-30
My drive currently looks like this:

Windows XP - PRIMARY
Windows Vista - PRIMARY
Ubuntu - PRIMARY
EXTENDED:
     *Linux swap
     *NTFS - Files and such
     *(Corrupted?) FAT , long story, unneeded

Anyway, I built a new system with a new motherboard.  Thus, Neither Windows will boot but Ubuntu can.  I am looking to replace the Windows Vista partition with Windows 7.  If I format that partition and replace will I have any trouble?  Will the Windows 7 bootloader work properly and play nicely with GRUB?  Will there be any trouble with my extended partition?  Any high risk of losing files in Files partition?

---

### Post by 73ckn797 on 2011-12-30
Did you use the old hard drive? Windows does not like being moved around, so to speak. You would have to boot from the Windows disk and repair the Windows installation. You could corrupt the Windows install by trying to use it. The Windows system is configured to the prior MB and other hardware. Ubuntu is a little more forgiving and is more easily moved between hardware. At least from my experience.

---

### Post by 2F4U on 2011-12-31
Windows tends to kill grub and place its own boot loader into the mbr. There is nice documentation on the net on how to fix this. This link is just one of them

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by BLaZuRE on 2011-12-31
Yes, I used my old hard drive and moved it in with a new motherboard and CPU, so the chipset driver needs to be changed.  I'll try repairing XP and reformat Vista.  I don't need the Windows installs.  I just need my Files partition to be preserved under the extended partition.

Yeah, I supposed I would have to fix Grub2 in Linux, but that's simple.  I was more worried if Win 7 will not recognize XP or something and it won't have an option for it or if it had a different installation process.

---

### Post by alphacrucis2 on 2011-12-31
> **BLaZuRE said:**
> Yes, I used my old hard drive and moved it in with a new motherboard and CPU, so the chipset driver needs to be changed.  I'll try repairing XP and reformat Vista.  I don't need the Windows installs.  I just need my Files partition to be preserved under the extended partition.

Yeah, I supposed I would have to fix Grub2 in Linux, but that's simple.  I was more worried if Win 7 will not recognize XP or something and it won't have an option for it or if it had a different installation process.

If you plan to upgrade xp to win7 you may want to read this:

[http://windows.microsoft.com/en-US/windows7/help/upgrading-from-windows-xp-to-windows-7](http://windows.microsoft.com/en-US/windows7/help/upgrading-from-windows-xp-to-windows-7)

Sounds like the process blows away your files so you will need to back up.

---

### Post by BLaZuRE on 2012-04-24
Sorry for the bump, just went back and marked this as solved for anyone that may find this in a search.

I simply put in the Windows 7 disc, removed the Vista partition, reformatted that free space as an NTFS partition for Windows 7.  No major hiccups besides Grub.

---


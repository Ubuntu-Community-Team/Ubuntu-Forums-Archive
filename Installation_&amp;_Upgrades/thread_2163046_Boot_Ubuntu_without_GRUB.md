---
title: "Boot Ubuntu without GRUB"
date: 2013-07-16
forum: Installation &amp; Upgrades
---

### Post by gavins38 on 2013-07-16
My wife has a Stone MR052 laptop that she currently uses Windows 7 on. She's getting fed up with the 'quirks' that are developing on her install and since playing with my laptop has decided that Ubuntu is the way to go for her. However, for some strange reason her laptop will not boot any Linux installation. It doesn't even attempt to load GRUB, instead just giving a 'no operating system found' error message. I've been looking into this and I've discovered that lots of other people with the same model laptop have encountered the same problems installing Linux. It does appear to be a BIOS issue but the laptop is a rebranded Fujitsu and neither Stone nor Fujitsu offer any BIOS updates.

I've tried several different distros; Ubuntu, PCLinuxOS, Linux Mint, ROSA, and others; but they all have the same problem booting. They will all boot from a live CD, will all install quite happily, but once you try to boot from the harddrive nothing happens. I'm guessing that it's an issue between the BIOS and GRUB so my question is, is there any way to boot Ubuntu without using GRUB; either by using the Windows bootloader or another Linux based bootloader? 

This laptop quite happily boots Windows so I know it's compatible with the Windows bootloader. Everything I've read online suggests pointing the Windows bootloader at a partition based GRUB, but my concern is that if it is an issue between the BIOS and GRUB then that workaround is just going to point me back at a blank screen again.

Does anyone have any ideas that could help? I'd really hate to miss out on the opportunity to convert my wife from her Windows dependence while she's interested, just because I can't get her laptop to get over its fixation on Windows either. :D

---

### Post by cybrsaylr on 2013-07-16
That is strange.
I dual boot all my PCs with Ubuntu and GRUB always installs with whatever Ubuntu version selected with no issues. Doesn't matter if it is a desktop or a laptop. Did this with XP, Vista and Win7 with no problems. Have no idea why your laptop won't install GRUB.

---

### Post by oldfred on 2013-07-16
Some, mostly Intel motherboards had to have a primary partition with the boot flag or they gave a system not found boot error. Or they seem to expect Windows.
But grub does not need boot flag, but you can still add one to any primary partition and see if that is the issue.

Some very new UEFI systems have modified UEFI to only look for the Windows efi file to boot, but I have not seen that will older BIOS systems. Some BIOS have a way to lock MBR and that setting has to be turned off. And some of those are not obvious as to the name used. May be boot sector virus protection or locked hard drive?

---

### Post by gavins38 on 2013-07-18
Thanks for your suggestions but sadly I checked the drive partition using gparted and it already has a boot flag enabled. I'll have another look through the BIOS settings but they are pretty restricted.

---

### Post by Clive_Rixson on 2014-05-10
I have had exactly the same problem with the Stone MR052. Like you I have also installed many flavours of Linux on many machines without problems before.  In this case, I was asked by my son's school to rescue 3 of these laptops on which WinXP had begun to run very slowly.  I had the same problem as you when I tried a clean install of Lubuntu 1404. After many nights of experimentation, and using many boot repair tools without success, I found that installing Lubuntu side by side with the original WinXP resulted in a machine that would boot from the hard drive. (I used Lubuntu as RAM was only 0.5 GB, and the school wanted me to install the Edubuntu packages.).  Even my faithful friend Parted Magic let me down - I had to use an ancient copy of Norton Partition Magic to shrink the Windows partition before installing Lubuntu.  Fortunately I still had the original Windows install on one of the machines, which I could clone with Clonezilla before starting again.
If you would like a copy of the final "successful" Clonezilla image (for an 80GB HDD) it is 18GB with bzip2 compression.  I could put it on a cloud service if you want, or if you are in the EU I could post DVDs to you (5 discs).
God alone knows what Fujitsu did to the BIOS to cause this mayhem...

---


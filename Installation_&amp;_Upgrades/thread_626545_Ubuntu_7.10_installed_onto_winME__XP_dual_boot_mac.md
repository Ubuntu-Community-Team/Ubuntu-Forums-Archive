---
title: "Ubuntu 7.10 installed onto winME / XP dual boot machine..now Win ME cannot boot."
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by ldauvin on 2007-11-29
I have recently installed Ubuntu 7.10 onto a PC already dual booting WinME and WinXP. I allowed the Ubuntu install to take space from the WinME partition, and it moved data and installed OK. I think I opted for GRUB to write to the MBR. This allowed for the option of choosing WinXP, but once the NTLDR fired up, WinME was listed as an option still, but returned the error message "Non-system disk" which presumably means that the partition is now unbootable. Is this correctable with "fdisk/mbr" on the WinME boot floppy? I am worried that doing this will mess up GRUB. WinXP works just fine still, but I still need WinME for a number of my daughter's games that XP will not run properly, otherwise I would abandon WinME altogether. I can see the WinME partition from both Ubuntu and XP, but cannot get into it! Any advice gratefully received. Thanks, in advance.

---

### Post by Sef on 2007-11-29
Download [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/").  It hopefully will do the trick.

---

### Post by ldauvin on 2007-11-30
Thanks Sef, I'll try that this weekend.

---

### Post by ldauvin on 2007-12-03
An Update: The Super Grub disc is really useful, but was not able to correct the problem, as the partition had been rendered unbootable by the Ubuntu install. I should have separated some space for Ubuntu before installing. By a mixture of Win 98 boot CD and ME boot floppy, I was able to repair the WinME partition so that it was bootable once again.

---


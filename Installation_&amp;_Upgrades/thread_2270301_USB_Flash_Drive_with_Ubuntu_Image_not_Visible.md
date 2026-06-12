---
title: "USB Flash Drive with Ubuntu Image not Visible"
date: 2015-03-21
forum: Installation &amp; Upgrades
---

### Post by klundermann on 2015-03-21
I'm following  in an attempt to install 14.10 on an ASUS Q550LF laptop with EFI.  I think I'm doing something right in that when I boot up, I get an EFI screen:

[ATTACH=CONFIG]260810[/ATTACH]

I can boot to Windows 8 from here without difficulty.  I see no sign, however, of an option to boot to the 14.10 ISO file that I have burned to a USB flash drive that is plugged in.  Any suggestions on what I should do?

When I look at the BIOS, the boot options are:

[ATTACH=CONFIG]260811[/ATTACH]

I'm not sure why the Windows Boot Manager appears twice.  I gather the third option is the DVD drive, but my USB flash drive does not seem to appear.

Any ideas, guys?  I'm really stuck.

---

### Post by Vladlenin5000 on 2015-03-22
How did you "burn" the ISO to the USB flash drive?

---

### Post by klundermann on 2015-03-22
I guess "burn" was the wrong word.  I downloaded the ISO to my Windows machine, verified the MD5 hash, and created a bootable USB using Pen Drive Linux's USB installer.

---

### Post by Vladlenin5000 on 2015-03-22
OK. That should work.
Now, at your UEFI settings you need to select then ENTER in the first boot option and select the correct one from the list. No need to change the others because they'll change accordingly. Provided your USB flash drive is inserted at the boot time it must appear in that list. If not then you have a compatibility problem. Not all USB flash drives can be used for that purpose.

---

### Post by ubfan1 on 2015-03-22
In the UEFI settings, try turning off secure boot.  On an Asus x200, that was necessary to make the USB bootable.  Also be aware, booting the machine without the USB may reset the boot order to hard disk first.

---

### Post by klundermann on 2015-03-23
> **Vladlenin5000 said:**
> OK. That should work.
Now, at your UEFI settings you need to select then ENTER in the first boot option and select the correct one from the list. No need to change the others because they'll change accordingly. Provided your USB flash drive is inserted at the boot time it must appear in that list. If not then you have a compatibility problem. Not all USB flash drives can be used for that purpose.

It is with the greatest of pleasure that I type this reply from Ubuntu rather than from Windows:  using a different flash drive solved the problem!

Thanks very much, Vladlenin5000!  I had begun to have nightmares about having to use Windows for an extended period.  Thank you ubfan1 too for your helpful reply.

---


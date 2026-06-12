---
title: "Installing Vista. How do I repair GRUB after?"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by MegaSvensk on 2007-09-11
I just bought a copy of Windows Vista and I'm going to install it, but I guess when I do it'll overwrite GRUB. How do I repair GRUB afterwards so I'll be able to boot Vista, XP and Ubuntu? Because I guess I won't get an option for Ubuntu in Vista's boot manager, or am I wrong?
As long as I can boot all three I don't really care what boot manager does it.

---

### Post by rsambuca on 2007-09-11
After you install Vista it will take over the bootloader and give you an option to boot Vista or "an earlier version of Windows".  Then just use an old ubuntu LiveCD to re-install grub and it will detect the Vista loader.

---

### Post by MegaSvensk on 2007-09-11
> **rsambuca said:**
> After you install Vista it will take over the bootloader and give you an option to boot Vista or "an earlier version of Windows".  Then just use an old ubuntu LiveCD to re-install grub and it will detect the Vista loader.
Okay, thanks. But is there any way to just repair Grub? Because I don't want to lose all my settings in Ubuntu. Currently, XP and Ubuntu are installed in two different physical disks and depending on which I choose as the first boot disk, I can either use Grub or XP's bootloader. If I install Vista on the same disk as XP, then Grub will still remain on the other disk right?

EDIT:
Oh, sorry, I misread your post. How exactly do I reinstall Grub? I'm kind of a Linux noob.

---

### Post by rsambuca on 2007-09-11
Hold on a second here.  Before we start doing more, something you wrote sounds a little strange to me.  How are you able to chose bootloaders?  Do you chose your OS's by accessing your BIOS everytime?  If so, did you install ubuntu by removing the XP drive?

---

### Post by MegaSvensk on 2007-09-11
No, when I first installed Ubuntu, it just booted straight into XP. Then I discovered that Grub was installed on the disk that was second in the boot order. So I changed the order and then Grub started and it let me boot both Windows and Ubuntu, which is the way I want it.

---

### Post by rsambuca on 2007-09-11
Ah, I gotcha.  Well, after installing Vista, in will overwrite your mbr, however, we can't be positive which drive's mbr it will overwrite.  If it overwrites the grub, don't worry, just boot from the live cd, open a terminal, and type "sudo grub-install"

---

### Post by MegaSvensk on 2007-09-11
Okay, thanks for your help. I will do that.

---

### Post by merlinus on 2007-09-11
> **rsambuca said:**
> Ah, If it overwrites the grub, don't worry, just boot from the live cd, open a terminal, and type "sudo grub-install"

Hi.  Will this work in most cases?  If so, it is a heck of a lot easier than sudo grub, find, etc.

Thanks!

---

### Post by dcstar on 2007-09-12
> **MegaSvensk said:**
> I just bought a copy of Windows Vista and I'm going to install it, but I guess when I do it'll overwrite GRUB. How do I repair GRUB afterwards so I'll be able to boot Vista, XP and Ubuntu? Because I guess I won't get an option for Ubuntu in Vista's boot manager, or am I wrong?
As long as I can boot all three I don't really care what boot manager does it.
You can save the current (Ubuntu) contents of your boot block, and then restore it after the Windows install.

Here is the command to save the MBR data (assuming your boot disk is /dev/hda):
```
dd if=/dev/hda of=/mbr-backup bs=446 count=1
```Restoring would be just changing the "if" and "of" around (after you boot a Linux system that has the "dd" command and the saved file available).

The first 446 bytes do not contain any partition data, so you won't affect any new Windows partition. I have used this method myself after a Windows install, it was a bit quicker than reinstalling Grub etc.

---


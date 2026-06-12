---
title: "Dual Boot problem (Win 8.1 and Ubuntu), grub 2 doesn't load, used Boot-repair"
date: 2014-03-17
forum: Installation &amp; Upgrades
---

### Post by tom63 on 2014-03-17
Hi everyone,


I am a new user of Linux distro - Ubuntu 13.10. I started use it only one week ago. 


My problem is:
I have preinstalled Windows 8.1 and Ubuntu that I installed a week ago. After my first installation of my Ubuntu 13.10 as Dual Boot, I could not to log in to Windows again, only Ubuntu.


Today I decided to fix this problem with Boot-repair. I used a bootable version of my Ubuntu on my USB to log in, then I downloaded the Boot-repair via Terminal. Then in Boot-repair I choosed the Recommended repair and followed all the instructions, including confirmation of the removing my Grub 2. After that, when I restart the computer, everything what I see now is black screen with error message: 


> 
error: file '/boot/grub/i386-pc/normal.mod' not found.


Entering rescue mode...
grub rescue>


Now I cant log in to any operating system. Probably the Grub doesn't load.

My Boot-repair log is **[here]("http://paste.ubuntu.com/7107561/")**: [http://paste.ubuntu.com/7107561/](http://paste.ubuntu.com/7107561/)




Can anyone give me some advice?




Thank you.

---

### Post by oldfred on 2014-03-17
It looks like you originally install Ubuntu in BIOS/CSM boot mode as you have grub in protective MBR.
But now you show UEFI boot as grub files are in efi partition and mount of efi partition in fstab.

With Ubuntu in BIOS mode and Windows in UEFI mode you can only dual boot from UEFI/BIOS menu as UEFI and BIOS are not compatible and you cannot change once started. Or from grub menu if booted in BIOS mode cannot boot a Windows in UEFI mode.

But now you have also run the 'buggy' UEFI fix. That is for those UEFI where vendor modify UEFI to only boot Windows from UEFI menu. If you can start ubuntu from UEFI menu you do not want the rename.
With rename you boot Windows from UEFI menu but should get grub menu. And then can only boot the renamed Windows file from grub. The rename adds bkp at beginning of name.
       menuentry "Windows UEFI [COLOR=#ff0000]bkp[/COLOR]bootmgfw.efi"

      
 Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.
And a Windows update may rewrite the bootmgfw.efi file overwriting the shim version, so then if you can only boot the Windows version you have to rerun boot repair. If you can boot Ubuntu entry in UEFI menu, undo the rename.

You then should be able to boot Windows from UEFI menu.

With Windows 8.1 you must have fastboot or always on hibernation off. You also need secure boot off as grub will not boot Windows 8.1 with secure boot on.

You also are showing dual video. Which video mode does it boot in? Can you set in BIOS a video mode. Some let you fix one or the other, others are muxless and auto switch.
Review what others have offered in the way of links on dual video in the links in my signature.

---

### Post by tom63 on 2014-03-18
It really works. Thanks a lot.

---


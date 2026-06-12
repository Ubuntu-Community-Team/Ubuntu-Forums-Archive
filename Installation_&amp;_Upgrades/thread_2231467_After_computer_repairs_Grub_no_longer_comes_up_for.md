---
title: "After computer repairs Grub no longer comes up for dual boot win 8.1"
date: 2014-06-25
forum: Installation &amp; Upgrades
---

### Post by mmcl26554 on 2014-06-25
HP came to my home and installed a new "Click Pad" (Click pad is a newer version of touch pad where the buttons are built into the pad) and also a keyboard, in my laptop.   To do this because of the way this laptop is made you have to drill down from the bottom and remove the motherboard to get to the click pad and keyboard. Really a poor design!   Anyway now the grub boot menu is gone and the computer boots directly into win 8.1.   I can still get to Ubuntu 14.04 by pressing the F9 key which will bring an alternative boot device menu and Ubuntu is there.   I have run Windows boot repair, then in Ubuntu run boot repair the result number is 7703133. I then went into Windows and run [COLOR=#000000]bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi.   This should have restored the grub menu but it didn't.   So I'm out of options.
I don't understand why the repairs done on the computer would have affected the boot loader and grub in the first place.  If I don't find an answer my plan "B" is to save my programs as such with Aptik and reinstall Ubuntu this should work.  But there should be a way to fix this but I'm a beginner with Ubuntu and don't know what to do next.
Michael[/COLOR]

---

### Post by grahammechanical on 2014-06-25
My guess is that the HP engineer decided he/she needed to test the working of the new click pad and noticed the Grub boot menu and so without, or may be with, an additional charge fixed the windows boot menu for you. You most probably do not have Grub installed. Boot Repair would have showed that. We cannot confirm it because you have not provided a pastebin link to the boot repair report. What did boot repair suggest as the way of fixing this? Did you accept the offer from boot repair to fix things?

Regards.

---

### Post by mmcl26554 on 2014-06-25
First off I did supply the boot repair number in my post it is 7703133. paste.ubuntu.com/7703133/ 
I was present and watched him do the repairs.   I booted the computer after he finished it and it went directly to windows no grub menu showed up.
Michael

---

### Post by oldfred on 2014-06-26
This is a clicky link that makes it easy for us to see your file. I had to manually key it in.

[http://paste.ubuntu.com/7703133/](http://paste.ubuntu.com/7703133/)

Boot-Repair cannot parse Windows BCD as it is a hive. But your entry should work.

Did secure boot also get turned back on. And is fast boot or the always on hibernation back on. I think just about any Windows maintenance resets those to the Windows default.

---

### Post by Bucky Ball on 2014-06-26
In hindsight, posted in error. ;)

---

### Post by mmcl26554 on 2014-06-26
Fred,
Sorry about not posting the link properly,  I just didn't remember that is the correct way to do it on this forum, I'll try to do better next time.   Memory is not like wine it doesn't improve with age (you'll find out!)
Anyway I did check both secure boot and fast boot both were off.   There must be a fix for this because I know if I reinstall Ubuntu, run boot repair and then point windows to boot from the correct file it will all work again.    So if that would fix it then there must be a simple change in either Ubuntu or win8.1 to make the grub menu reappear.    It's like it's almost there as when I press F9 before the boot process starts and select Ubuntu from the alternate boot device menu then the grub menu shows up and Ubuntu will boot.   The 2 mysteries here are why did the grub menu go away and what does it take to get it back?   I can easily do the reinstall as aptik works well to restore my programs and applications and there is no data to save, but I'd like to get it to work and learn the fix.
Michael

---

### Post by oldfred on 2014-06-26
I do not know anything about Windows 8, but someone posted that with Windows 8 and booting another system even Windows 7, it resets UEFI for one time boot and then shuts down and forces a new reboot.

And others with HP have discussed issues as its UEFI seems to be really configured for only Windows and various work arounds are required.

You used alternative c:, I often suggest a: but change shim to be bootx64.efi and boot hard drive or install rEFInd which seems to work around many of the issues.

 [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
**Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files either  efi\Microsoft\Boot\bootmgfw.efi and/or /EFI/BOOT/BOOTX64.EFI to be grub or shim
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find renaming  /EFI/Boot/bootx64.efi  to be shimx64.efi or grubx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu 
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:** If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

### Post by mmcl26554 on 2014-08-05
Solved with reFInd, nice program to boot your computer.

---


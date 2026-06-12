---
title: "Unable to boot ubuntu or windows | Dell inspiron 15r"
date: 2014-05-20
forum: Installation &amp; Upgrades
---

### Post by mmonge on 2014-05-20
I have a Dell inspiron 15r and am trying to have dual booting with windows 8 and Ubuntu 12.04.

After installing ubuntu it did not show me grub, it booted directly into windows. Tried with Boot Repair after that and now I'm not able to boot in none of them.

Here's the output i had running Boot Repair a **second **time, selecting the following option:
[LIST]
[*]Backup and Rename EFI files (solves the [hard-coded-EFI] error)
[/LIST]
[http://paste.ubuntu.com/7493754/](http://paste.ubuntu.com/7493754/)


Any help is much appreciated

---

### Post by oldfred on 2014-05-21
I do not think Dell's need the rename. That is for UEFI where vendor has modified it to only boot Windows. So Boot-Repair renames the Windows file to really be shim/grub and boot Ubuntu. But then you can only boot Windows renamed file from the new Boot-Repair entry in the grub menu.

 Boot_Repair - Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

Did script go berserk or do you actually have all those copies of grub & shim in your efi partition? You should only have one of each. 

Better to use 14.04, as Intel has added many fixes to kernel, support software and video drivers. Grub & UEFI are improved. The 12.04.4 is about the same as 13.10, so updated from original 12.04 but not as current as 14.04 which also is a long term release.

Dell's seem to be pretty common across models with just different options.

 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)
[http://ubuntuforums.org/showthread.php?t=2204287](http://ubuntuforums.org/showthread.php?t=2204287)
Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)
Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)


 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

---


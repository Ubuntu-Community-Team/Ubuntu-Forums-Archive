---
title: "Multiple OS install - Reinstalling GRUB didn't solve"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by DMurray on 2010-02-21
Hi, everybody.

It's not the common "how to reinstall GRUB" question, don't worry. :-)
My HD partitioning is as follows:

- NTFS (primary): Windows XP 64bit
- EXT3 (extended): Ubuntu 9.10
- NTFS (extended): Windows XP 32bit

There are a few more partitions to make the use of extended partitions necessary. I have WinXP32 to run a few programs that won't run on 64.
Everything coexisted together for a few years, than I upgraded the XP64 to Win7. As usual, it had GRUB overwritten, and I recovered it with a Live-USB GParted.
When the GRUB menu was presented, I could select between Ubuntu and Win64/Win32. If this option was selected, another menu would be presented, this time letting me properly select Windows 64 or 32, but after this upgrade, I can't get this menu anymore. All I can boot is Ubuntu or Windows 7, but not WinXP32 anymore.
Any way I could recover its boot via GRUB?

Thanks in advance!

---

### Post by oldfred on 2010-02-22
Windows always combines its boot files into one, that was why you had a second menu for windows. When it combines them it also moves essential boot files into the version of windows that has the boot flag. You also have your win32 in an extended partition which makes it more difficult but not impossible to repair. You will need to copy boot files and update your win7 to see the XP install.

The easiest is to reinstall XP to a primary partition.

A few on this site can suggest which files to move where but will need the info from this script:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Repairs and extended partitions:
Major windows repair with dual boot and logical partition
[http://ubuntuforums.org/showthread.php?t=1411495](http://ubuntuforums.org/showthread.php?t=1411495)
You mean ntdetect and ntldr can't be on a logical partition, that is right. Yes the boot is via sda1. sda1 is there only for that purpose.
But it still needs a primary to boot from.
[http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition](http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition)
[http://support.microsoft.com/kb/306559#f1Boot](http://support.microsoft.com/kb/306559#f1Boot) WinXP from extended partition - Herman 
[http://ubuntuforums.org/showthread.php?t=1192147](http://ubuntuforums.org/showthread.php?t=1192147)
and from the author of the Boot Info script.
How to fix XP when the boot files are missing - Ubuntu Forums
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

---

### Post by DMurray on 2010-02-22
Thanks for this clear explanation, Oldfred.
I will try all your suggestions and let you know if it worked or not, though I will probably not extend the conversation here since it seems much more of a Windows problem.
GRUB and Linux are just fine.
Cheers.

---


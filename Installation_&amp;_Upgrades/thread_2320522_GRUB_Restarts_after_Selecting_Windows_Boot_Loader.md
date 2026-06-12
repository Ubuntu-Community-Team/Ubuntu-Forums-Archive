---
title: "GRUB Restarts after Selecting Windows Boot Loader"
date: 2016-04-14
forum: Installation &amp; Upgrades
---

### Post by allenkim95 on 2016-04-14
Hi all,

I was installing Ubuntu onto my laptop alongside Windows 10, and everything seemed to be going well until I got to the GRUB loader.

I see 
[LIST]
[*]Ubuntu
[*]Advanced Options for Ubuntu
[*]Windows UEFI bootmgfw.efi
[*]Windows Boot UEFI loader
[*]EFI/ubuntu/MokManager.efi
[*]Windows Boot Manager (on /dev/sda1)
[*]System setup
[/LIST]

These options came up after I tried running boot-repair. However, when I try running Windows, the computer just restarts and it goes back to the GRUB loader. I suspect I must have messed up my partitions or something, but I can't be sure. I got the pastebin below.

[http://pastebin.ubuntu.com/15840776/](http://pastebin.ubuntu.com/15840776/)

Any help would be awesome! Thanks!

---

### Post by yancek on 2016-04-14
Near the top of the boot repair output, just below sda4 you will see a large paragraph with some red font indicating your ntfs partition is inconsistent or there is a hardware fault or RAID.  It tells you what to do to resolve this.  Unfortunately, it requires you to run chkdsk which of course is a windows program.  Do you have the windows installation medium as there might be a way to do it using that, selecting the Repair option.   There might be some other way to repair.  I don't use windows so maybe someone else will be along who is more familiar.

---

### Post by oldfred on 2016-04-14
Since UEFI, you may be able to directly boot Windows from UEFI boot menu, not grub.
And you may need f8 to get into repair console to use chkdsk.

And you must turn off Windows 10 fast start up which really is just hibernation. Grub/Ubuntu/Linux NTFS driver will not mount NTFS that is hibernated nor if it needs chkdsk. Or grub only boots working Windows.
Often best to just have a Windows repair flash drive.

       Fast Startup off (always on hibernation)
[URL="http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html"]http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html
[/URL]
 Repair/backup/restore
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

Should be similar for Windows 10

 Windows 8 UEFI fixes, if no repair flash drive you may be able to download Window installer and use it.
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)
Repair Windows UEFI ows 8 boot issues & repair CD or flash
[http://ubuntuforums.org/showthread.php?t=2105418](http://ubuntuforums.org/showthread.php?t=2105418)
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html](http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html)

[URL="http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options"]
[/URL]

[URL="http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html"]
[/URL]

---


---
title: "Can't access Windows 10 receive EndEntire Error"
date: 2016-06-21
forum: Installation &amp; Upgrades
---

### Post by jhuppi on 2016-06-21
After installing Ubuntu I can no longer access Windows 10. When I select Windows from Grub I receive an EndEntire Error. I ran boot-repair and it said it was successful, but I still can't access Windows. Here is the paste bin log: [http://paste2.org/6an20nOA](http://paste2.org/6an20nOA). Thanks,

---

### Post by oldfred on 2016-06-22
Grub only boots working Windows.
And Windows cannot be hibernated nor need chkdsk.

And Boot-Repair can only do minor repairs to Windows, it primarily is for Linux repairs.
If you need to repair Windows you need to have a Windows repair flash drive.

But since UEFI you may be able to use UEFI one time boot key to directly boot Windows entry in boot menu (not grub menu) and use f8 to get into Windows internal repair console.

       Repair/backup/restore
[URL="http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options"]http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options
[/URL]
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html) 


[URL="http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options"]
[/URL]

---


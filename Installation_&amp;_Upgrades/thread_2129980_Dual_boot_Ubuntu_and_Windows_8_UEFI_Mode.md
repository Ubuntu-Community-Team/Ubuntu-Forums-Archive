---
title: "Dual boot Ubuntu and Windows 8 UEFI Mode"
date: 2013-03-27
forum: Installation &amp; Upgrades
---

### Post by homarques on 2013-03-27
Hi,

I install Ubuntu 12.10 amd64 in ultrabook samsung series 5 with HDD and SDD, and It have Windows 8 pre-installed, when I installed Ubuntu the grub didn't work, then I used boot-recovery to fix it, but windows 8 entry do not work.

[http://paste.ubuntu.com/5654012/](http://paste.ubuntu.com/5654012/)

Thanks.

---

### Post by oldfred on 2013-03-28
Do you have secure boot on. Some systems work with it on or off, others only boot Windows with it on.

You have the Intel SRT, did you turn that off and now have you turned it on?

Some others with Samsungs
 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)

---

### Post by homarques on 2013-03-28
> **oldfred said:**
> Do you have secure boot on. Some systems work with it on or off, others only boot Windows with it on.

You have the Intel SRT, did you turn that off and now have you turned it on?

Some others with Samsungs
 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)

Yes, my secure boot on and Intel SRT on too, I didn't turn off it.
I read the threads, but nothing work here.
Have you something else?

---

### Post by oldfred on 2013-03-28
From UEFI menu can you directly boot Windows?

It does not look like Boot-Repair has renamed the Windows boot file, unless you reran Boot-Repair. Some systems only boot Windows efi file. So Boot-Repair has to rename Windows or you can un-rename it and should have the original Windows file. May have to try with secure boot both on and off. Many seem to only be able to boot Windows with secure boot on.

 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by homarques on 2013-03-28
> **oldfred said:**
> From UEFI menu can you directly boot Windows?
When I press F10 in boot appears a menu boot with the options ubuntu and Windows bootloader, if a choose ubuntu then appears the grub, if a choose Windows bootloader then I boot windows 8.
> **oldfred said:**
> 
It does not look like Boot-Repair has renamed the Windows boot file, unless you reran Boot-Repair. Some systems only boot Windows efi file. So Boot-Repair has to rename Windows or you can un-rename it and should have the original Windows file. May have to try with secure boot both on and off. Many seem to only be able to boot Windows with secure boot on.
If a turn off secure boot the entry in grub work, but the entry don't work with boot secure on. Then is it impossible work with boot secure on?

> **oldfred said:**
> 
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by oldfred on 2013-03-28
Does Windows 8 boot with secure boot both on and off?

Ubuntu only boots with secure boot off? Ubuntu uses the Microsoft UEFI secure boot key to boot, so it still should boot if you are using the shim efi file as that is the version with the key.

But some systems need the files renamed as they only boot the Windows efi file with secure boot. Then you can use Boot-Repair (rename files in advanced options posted above) to rename shim to the Windows file & both should boot with secure boot on.

---

### Post by oldfred on 2013-03-28
Another user who did not want Windows, so he erased it.

[http://ubuntuforums.org/showthread.php?t=2129858](http://ubuntuforums.org/showthread.php?t=2129858)

---

### Post by homarques on 2013-03-28
> **oldfred said:**
> Does Windows 8 boot with secure boot both on and off?

Ubuntu only boots with secure boot off? Ubuntu uses the Microsoft UEFI secure boot key to boot, so it still should boot if you are using the shim efi file as that is the version with the key.

But some systems need the files renamed as they only boot the Windows efi file with secure boot. Then you can use Boot-Repair (rename files in advanced options posted above) to rename shim to the Windows file & both should boot with secure boot on.

I boot windows 8 by grub with secure boot off. I can boot windows with secure boot on when a press F10 for boot Menu.
I don't know if I did it it correctly:

> **oldfred said:**
> 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows.

It's OK, I can  do it.
> **oldfred said:**
> 
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair -->  Advanced Options --> "GRUB options" tab --> tick "SecureBoot"  --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

I can't find this files, then I used liveCD for recovery the grub.

---

### Post by oldfred on 2013-03-28
So can you boot from grub both Ubuntu & Windows with secure boot off? Then I would just leave it and use it that way. Or do both work with secure boot on when booting grub  to grub menu, then from grub menu boot Windows?

       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

### Post by homarques on 2013-03-28
OK, I will use it.
Maybe the next version fix it

---


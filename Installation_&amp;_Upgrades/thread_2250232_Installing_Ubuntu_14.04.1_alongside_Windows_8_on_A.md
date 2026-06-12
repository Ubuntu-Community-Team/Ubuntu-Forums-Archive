---
title: "Installing Ubuntu 14.04.1 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI)"
date: 2014-10-27
forum: Installation &amp; Upgrades
---

### Post by jjer on 2014-10-27
Hi, 

The laptop I successfully configured for EFI dual boot (Windows 8 & Ubuntu 12.10) in February 2013 does not boot into Windows anymore. 

The reason is that I have upgraded from Ubuntu 12.10 to Ubuntu 14.04.1 LTS today, following the same procedure as I followed in post #6 (created with help from oldfred) in this thread:  
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)

The differences between the upgrade done in February 2013 and the upgrade done today are in the details (the Ubuntu version and the boot-repair versions differ). 
Furthermore, boot-repair completed the work with an error message: "An error occurred during the repair". 

Summary of original set-up and the intended use of the partitions: 
Hard-disk (sda): 
[LIST]
[*]sda1: EFI partition with windows boot files
[*]sda2: NTFS Windows recovery
[*]sda3: unknown
[*]sda4: Windows 8 OS (NTFS)
[*]sda5: NTFS Restore
[*]sda6: ext4 unused partition
[*]sda7: NTFS shared Windows / Ubuntu partition
[*]sda8: ext4 additional Ubuntu /home partition
[/LIST]

SSD-disk (sdb): 
[LIST]
[*]sdb1: EFI partition (overwritten during installation of Ubuntu 14.04.1 when the HD was removed)
[*]sdb2: ext4 unused partition
[*]sdb3: Swap area for Ubuntu
[*]sdb4: ext4 unused partition
[*]sdb5: ext4 Ubuntu root partition
[*]sdb6: ext4 Ubuntu primary /home partition
[*]sdb7: ext4 unused partition
[/LIST]

I think sda1 was the active EFI partition before I did the upgrade today. It seems that sdb1 now is the active EFI partition? 

The boot-repair info before i did the upgrade is here: [http://paste.ubuntu.com/8701696/](http://paste.ubuntu.com/8701696/)

The boot repair info after the upgrade is here: [http://paste.ubuntu.com/8702999/](http://paste.ubuntu.com/8702999/)
Here, boot-repair completed the work with an error message: "An error occurred during the repair"". 

 Please help me get Windows 8 back. I use Windows 8 it to transfer data between my Samsung Galaxy smartphone and the laptop. Occasionally I use software that run in Windows OS only.

[B]The problem is that the laptop only boots into Ubuntu 14.04.01. The windows boot option (in the list) does not work.

[/B]PS: I also posted this issue in the boot-repair thread [http://ubuntuforums.org/showthread.php?t=1769482&page=221](http://ubuntuforums.org/showthread.php?t=1769482&page=221) in case it is an issue with boot-repair.

---

### Post by oldfred on 2014-10-27
You have this file  in both sda1 & sdb1 your two efi partitions:
 /EFI/Microsoft/Boot/bkpbootmgfw.efi 

Before the only way we knew was renaming bootmfgw.efi to be grub and then using an entry that Boot-Repair created to boot the bkp.. file which is the "real" Windows efi boot file.

Grub reinstalled correctly as error code 0 is no error.
Reinstall the GRUB of sdb5 into the MBR of sdb
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sdb: exit code of grub-install /dev/sdb:0

But Boot-Repair may pick up some minor error and report that at the end of the report.

But now grub2's os-prober has been fixed an will create a correct efi boot entry. But that is to the bootfgw.efi which now is grub's efi file or a loop back to grub.
The entry Windows efi file is correct if the Windows file is bootmfgw.efi not the renamed version.

Some computers only boot Windows or the bootmfgw.efi. So that is why Boot-Repair would rename that file to really be grub. UEFI would then think it is booting Windows but really boot grub/Ubuntu.
If you can boot the ubuntu entry in UEFI you do not need rename. But it is one of the now several alternatives to get Windows "only" systems to boot Ubuntu.

Several alternatives:
      
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

Back-up efi partitions before making any changes:

I would first run the un-rename in Boot-Repair. I may only un-rename one of the two entries.
      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair of bootmfgw.efi will need to be redone after a Windows update as it will restore Windows files. Only if that is the only way you can boot Ubuntu.

---

### Post by jjer on 2014-10-28
Thanks oldfred, 
I will read and try to understand what to do.

---

### Post by jjer on 2014-10-31
Oldfred, thanks again for the thorough reply. I am afraid that I do not completely understand the details. 

I see the file **/boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi**. 
I have now backed up the data to /usr/share/boot-sav/ with the tool boot-repair. 

Please clarify whether I should: 
Rename (or copy) the above mentioned file to **/boot/efi/EFI/Microsoft/Boot/grub.efi**?
And/or try to rename (or copy) it to **/boot/efi/EFI/Microsoft/Boot/shim.efi**?

Thanks for your help.

---

### Post by ubfan1 on 2014-10-31
Neither, you want to rename the bkpbootmgfw.efi to bootmgfw.efi.  Your existing bootmgfw.efi is a copy of either shimx64.efi or grubx64.efi, look at the filesizes to tell if you are curious.

---

### Post by jjer on 2014-10-31
Thanks Ubfan1, 
The problem is solved using your advice! I now can boot into either Ubuntu 14.04.1 or Windows 8.

---


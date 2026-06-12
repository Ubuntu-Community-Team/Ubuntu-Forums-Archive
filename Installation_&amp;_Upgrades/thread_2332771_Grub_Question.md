---
title: "Grub Question"
date: 2016-08-03
forum: Installation &amp; Upgrades
---

### Post by RobGoss on 2016-08-03
Hello everyone I wanted to know let's say if I install Ubuntu as a dual boot with Windows 10 and decide to remove Ubuntu, will the Grub menu replace Windows boot loader after removed and will I be able to boot Windows as I did before.

Thanks so much

---

### Post by yancek on 2016-08-03
With windows 10, probably UEFI so the method differs.  See the Ubuntu documentation at the link below.  You should be able to select windows from the BIOS or with a specific boot key.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2016-08-04
Whether UEFI or BIOS always restore default boot of Windows before deleting Ubuntu partition.
While Windows works always make the Windows repair/recovery flash drive, so you have a way to repair Windows.

With BIOS you must reinstall the Windows boot loader to MBR.
       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader) 
    
With UEFI you can just select Windows as new default. 
But you may want to also remove ubuntu entries in UEFI and /EFI/ubuntu folder.
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)

How to: Create a Recovery Drive for reinstalling Windows 10 from Windows 10
 [http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5](http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5)
Repair/backup/restore
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by RobGoss on 2016-08-04
Thanks so much Fred for the information very helpful

---


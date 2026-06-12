---
title: "Windows boot manager and Grub issues"
date: 2014-01-01
forum: Installation &amp; Upgrades
---

### Post by tears of the river on 2014-01-01
Hey guys,

I have tried to dual boot Ubuntu 13.10 (64-bit) to my cousins laptop, acer aspire E1-571G, which already contained the pre-installed windows 8 (upgraded to 8.1). The first of many problems to come was that an error appeared saying:

```
APAP CDROM: MATSHI TADVD-RAM UJ8C0 has been blocked by current security policy
```

I was quite confused as this error as upon searching about the error it meant that the secure boot was blocking the cd when it shouldn't because as far as I knew the newer versions of ubuntu didnt go through these problems. Anyway the search results all said to disable secure boot. There were a number of tutorials about how to do that however none of them worked because as can be seen by the attached picture there is an option of secure boot however it can not be selected or altered.

[ATTACH=CONFIG]249097[/ATTACH]

so the forums said to change it from uefi to legacy. So we did that and the installation came up. So we then followed: [http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html) we had already 'disabled' secure boot, and fast boot and had a working boot able disk so we went on through the installation we had partitioned 62 GB of free space from windows for Ubuntu and hence we used that. We gave 30 GB to mount point: / , 16 GB to mount point: /home, 16 GB to swap area and 200 MB to Reserved Bios boot area as it said to put some for boot.

We then installed it successfully however when booting up there came no option for changing in between the sytems. As when it was set to legacy it would boot to ubuntu and on uefi it would load into windows 8.1 so the forums said that we should run boot-repair however when it finished it gave this:

[ATTACH=CONFIG]249098[/ATTACH]

We then set it onto uefi and boot it then we got the error

```
Windows boot manager has been blocked by current security policy
```

upon pressing ok we get:

```
HDD: has been blocked by the current security policy
```

when we which to legacy and try to load up Ubuntu we get:

```
error: file '/boot/grub/i386-pc/normal.mod' not found
```

followed by grub rescue prompt.

I have no idea what to do now and am too scared to experiment on it so i decided to post to you guys.


NOTE: as far as we know we cant load to either OS however we can load to live disk through legacy and we used live disk to do boot-repair

---

### Post by oldfred on 2014-01-01
Post link to Bootinfo report from Boot-Repair.

Boot-Repair probably converted your BIOS boot install to UEFI. So then you get an error trying to boot in BIOS/Legacy/CSM mode.
Did you also run the "buggy" UEFI suggestiong by Boot-Repair. I do not suggest that until all other issues are resolved and we then know for sure you cannot boot an ubuntu entry from UEFI menu.

Some systems may want a password to allow you to change UEFI from secure boot?
Or you have the settings to change that in another screen?

See also additional info in the link in my signature.

---

### Post by tears of the river on 2014-01-01
The boot info is: [http://paste.ubuntu.com/6673842/](http://paste.ubuntu.com/6673842/)

and I am not quite sure however I do believe that I installed it in 'buggy' UEFI suggestion

---

### Post by dm_65 on 2014-01-01
Repair steps should fix first Windows booting then Ubuntu.

Ubuntu boot manager/loader (GRUB) can boot Windows by chain loading Windows boot manager.
Windows boot manager cannot boot/chain load GRUB on GPT/UEFI.

Windows 8 is installed on GPT disk so you should use UEFI booting for both systems (Win8 and Ubuntu).

1. To repair Windows 8 booting you should have a Windows 8.1 Recovery USB/CD/DVD. 
This can be made on another computer with Windows 8.1 (assuming 64-bit for UEFI installation).

Having the recovery media try automatic repair.
If it does not succeed then on recovery console use this command:
[B]bcdboot c:\windows 
[/B]assuming c: drive is where Windows is installed else change drive letter.

Please note: 
Installation and recovery media should be booted the UEFI way (not legacy) !!
Windows installations can boot when Secure Boot enabled and when it is disabled.

2. I would reinstall Ubuntu after having repaired Windows. 
This will also create a dual boot entry for Windows in GRUB boot menu.

Boot related files for UEFI installations are on EFI System partition (Windows creates a 300 MB ESP).
This partition should be backed up before installing new systems so you can restore you computer easily
to previous state.

MBR code is irrelevant when booting the UEFI way.

---

### Post by fantab on 2014-01-01
```
parted -l:

Model: ATA Hitachi HTS54757 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
**Partition Table: gpt**

Number  Start   End    Size    File system     Name                  Flags
1      1049kB  420MB  419MB   ntfs            Basic data partition  hidden, diag
**2      420MB   735MB  315MB   fat32           EFI system partition  boot**
4      869MB   665GB  664GB   ntfs            Basic data partition  msftdata
3      665GB   696GB  30.7GB  ext4
5      696GB   712GB  16.4GB  ext4
7      712GB   730GB  17.5GB  linux-swap(v1)
**8      730GB   730GB  200MB                                         bios_grub**
6      730GB   750GB  20.0GB  ntfs            Basic data partition  hidden, diag

```

Your Partition '8' is 'bios_grub' partition. This is needed on a GPT formatted Disk to boot Linux OS in 'Legacy/CSM/MBR' boot mode.
Since you already have Windows 8.1 booting from your '2' partition, which is EFI, your 'bios-grub' partition is NOT required and is confusing UEFI. If you have not made the 'bios_grub' partition yourself then it was created as a consequence of booting 'Boot-Repair' in 'Legacy' mode. Because Linux OS can boot from 'GPT' disks only if the disk has as 'bios_grub' partition.
Recommendation: Remove/Delete partition /dev/sda8 with 'bios_grub' flag.

If you had earlier make backups of your Windows partitions, especially EFI System Partitions [ESP] then you must restore it. If you haven't then ignore this.

In some Acer Aspire, to be able to manage 'Secure Boot' you may have to set the 'Supervisor Password' in the UEFI/BIOS menu. Only then will it be activated. It will be good idea to disable 'Secure Boot'.

When you ran 'Boot-Repair' your Windows EFI entries got renamed:
```
sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi 
                       **/EFI/Microsoft/Boot/bkpbootmgfw.efi **
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi

```
To correct this you have to run 'Boot-Repair' again and 'check' the option '*Restore EFI backups'*, and don't let BR rename them again. BR MUST be run in EFI mode only, so boot your Ubuntu DVD/USB in EFI mode only.

Checklist:
Disable 'FastStartup' in Windows 8.1
Disable 'Fastboot' in UEFI/BIOS
Disable 'Secure Boot'.

---

### Post by oldfred on 2014-01-01
The bios_grub and grub in the MBR are because you installed in BIOS/CSM/Legacy mode.
Boot-Repair converted install to UEFI.
You ran the buggy UEFI fix, but we do not know if needed or not. Best to undo and only then if you cannot boot ubuntu entry in UEFI menu then add it again.

 With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.
And a Windows update may rewrite the bootmgfw.efi file overwriting the shim version, so then if you can only boot the Windows version you have to rerun boot repair. If you can boot Ubuntu entry in UEFI menu, undo the rename.

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

Best to always boot in UEFI mode since your installs are UEFI.

---


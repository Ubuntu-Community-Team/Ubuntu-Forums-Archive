---
title: "Ubuntu 14.04 &amp; Windows 8.1 on hard disk + SSD"
date: 2015-02-16
forum: Installation &amp; Upgrades
---

### Post by Alessio_Locallo on 2015-02-16
Hi, I have an ASUS S500CA notebook with a 24GB SSD and 500GB hard disk. I'd like to have both ubuntu and windows. I installed windows on the hard disk and then I installed ubuntu on the SSD. Root partition and /boot/efi partition are on the SSD, while swap area and /home partition are on the hard disk. 
This is fdisk -l:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x3ca2dca6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   315230207   157255680    7  HPFS/NTFS/exFAT
/dev/sda3       315230208   327229439     5999616   82  Linux swap / Solaris
/dev/sda4       327229440   976771071   324770816   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 24.0 GB, 24015495168 bytes
255 heads, 63 sectors/track, 2919 cylinders, total 46905264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1    46905263    23452631+  ee  GPT
``` 
The problem is that windows doesn't appear in the grub menu and ubuntu boots directly. I've tried update-grub, but nothing change. What should I do? Thank you!

---

### Post by oldfred on 2015-02-16
You are not showing an efi partition on sda, so Windows must be installed in BIOS boot mode. And with an efi partition on sdb, you have Ubuntu in UEFI mode.
UEFI and BIOS are not compatible. They write hardware system info differently to hard drive for operating system to use. So you can only dual boot from UEFI menu or full reboot. And you may have to turn on/off UEFI or CSM modes.

If you do want to have Windows in grub menu, you can either reinstall Windows in UEFI mode or convert Ubuntu to BIOS boot mode. You can adda tiny 1 or 2MB unformatted partition and give it the bios_grub flag. That is required for grub to install correctly to MBR of sdb and you want it in sdb. And then use Boot-Repair to convert from UEFI to BIOS using advanced mode. It really is uninstalling grub-efi-amd64, and installing grub-pc(BIOS).

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[URL="https://help.ubuntu.com/community/Boot-Repair"]https://help.ubuntu.com/community/Boot-Repair

[/URL] GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

[URL="https://help.ubuntu.com/community/Boot-Repair"]
[/URL]

---

### Post by Alessio_Locallo on 2015-02-17
Thank you so much for the answer!

So, if I want to convert Ubuntu to BIOS mode, I have to delete the /boot/efi partition on /dev/sdb and replace it with a tiny unformatted partition with bios_grub flag; then, I'll use grub-repair. Is it correct?
How can I add the bios-grub flag to an unformatted partition? I can't manage flags...

And, if I want to reinstall everything, my partition table should be like that:
/dev/sdb: sdb1: 2MB unformatted, bios_grub flag
              sdb2: /
/dev/sda: sda1: 100MB, windows reserved
              sda2: 150GB, windows
              sda3: swap
              sda4: /home

---

### Post by fantab on 2015-02-17
> to convert Ubuntu to BIOS mode, I have to delete the /boot/efi partition  on /dev/sdb and replace it with a tiny unformatted partition with  bios_grub flag; then, I'll use grub-repair. Is it correct?

That is correct. Just removing the 'boot' flag will also render it ineffective as ESP.
You should also disable UEFI boot and enable Legacy/Bios/csm boot in BIOS/UEFI menu if you have that option.

You can add the 'bios_grub' flag with gparted ([how to]("http://www.dedoimedo.com/computers/gparted.html#mozTocId143113")), right click on the partition from gparted, from the drop down menu select either 'manage flags' or 'flags'.

[s]IMO it would be a better idea to make the bios_grub partition on the SSD[/s], and you can take advantage of the faster SSD to boot faster.
EDIT: Your /dev/sda is MBR, so just install grub to the SSD you don't need a bios_grub parittion if you install Grub to the MBR of SSD. You'll also have to set your /dev/sda, SSD as your first boot device in BIOS/UEFI menu.

---

### Post by Alessio_Locallo on 2015-02-17
If I install ubuntu in BIOS mode, I can't see the SSD in the BIOS, so windows starts automatically...
How can I install win in EFI mode?

---

### Post by oldfred on 2015-02-17
some links on Windows installs in UEFI.

  You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)

   Convert Windows BIOS to UEFI - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)

   Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---


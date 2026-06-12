---
title: "Windows doesnt appear in grub after installing alongside Ubuntu"
date: 2015-12-21
forum: Installation &amp; Upgrades
---

### Post by alex479 on 2015-12-21
I have two hard drives, one I installed Ubuntu on, and then the other I installed windows on.  If the ubuntu hdd is unplugged, I boot to windows automatically.  If the ubuntu hdd is plugged in, grub starts but windows does not appear as one of the options.

Does anyone know how to enable booting to windows through grub when the installation is on a separate hdd?

Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 59DDA7D4-FB46-44B3-B775-3D5BA0295614

Device          Start        End    Sectors   Size Type
/dev/sda1        2048    1050623    1048576   512M EFI System
/dev/sda2     1050624 1920253951 1919203328 915.2G Linux filesystem
/dev/sda3  1920253952 1953523711   33269760  15.9G Linux swap


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x2cbcc594

Device     Boot  Start        End    Sectors   Size Id Type
/dev/sdb1  *      2048     206847     204800   100M  7 HPFS/NTFS/exFAT
/dev/sdb2       206848 1953521663 1953314816 931.4G  7 HPFS/NTFS/exFAT

---

### Post by QIII on 2015-12-21
Did you have the Windows drive disconnected when you installed Ubuntu?

If so, have you set your Ubuntu drive as the first in the boot order and run

```
sudo update-grub 
``` from Ubuntu?

---

### Post by alex479 on 2015-12-21
I first installed Ubuntu on the first hdd, leaving the second as unallocated space.  Later I unplugged my Ubuntu hdd in order to install windows on the second hdd.  I plugged my Ubuntu hdd back in and grub starts, because my first hdd which has only grub and ubuntu is first in the boot order, but there is no option to boot windows, which is on my second hdd.  I booted into Ubuntu and ran sudo update-grub and restarted my computer, but there was still no windows entry in grub.  If I choose which drive to boot from my bios rather than grub, I can select my second hdd in order to boot windows, however this is not ideal because then i need to mash F10 while my computer is starting in order to do so.  

There must be something more I have to do in order to get my windows installation from my second hdd to appear in grub.

---

### Post by grahammechanical on 2015-12-21
Have you read this?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I am guessing that Ubuntu has been installed in EFI mode & Windows in BIOS/Legacy/Compatibility mode.

sda disklabel type = GPT and it has sda1 = EFI system

sdb disklabel type = Dos but without a EFI partition.

Ubuntu installed in EFI mode cannot recognise Windows installed in BIOS mode.

Regards.

---

### Post by alex479 on 2015-12-21
I take it I'll have to reinstall windows 7 then?

How would I go about installing it in EFI mode though?  The custom install options would only throw errors...

---

### Post by oldfred on 2015-12-21
The Windows 7 DVD defaults to BIOS with MBR partitions. You have to copy to flash drive and move the efi boot files to correct place for it to boot in UEFI mode. Then only gpt partitioning is allowed, so make sure you do not have other data on drive as it will be lost. Or you can manually convert to gpt and usually preserve data. Backups still required, just in case.

       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)
rem === Copy boot files to the System partition =========
W:\Windows\System32\bcdboot W:\Windows /s S:\Windows\Boot\EFI

---

### Post by alex479 on 2015-12-22
Would using rufus set to GPT partition and FAT32 file system suffice for making a UEFI version of Windows 7?  Also would an alternate solution be to convert my windows 7 installation to gpt and reinstall a boot loader, instead of reinstalling windows entirely?  How likely would that be to actually work?

---

### Post by oldfred on 2015-12-22
Good backups required whatever you do. Any major system change may need a backup to recover system.
I did see a post where someone did use Rufus to create a UEFI bootable system. I know it works for Windows 8, but do not know for sure with Windows 7. UEFI has to boot from /EFI/Boot/bootx64.efi so it needs bootx64.efi in correct place on FAT32 formatted partition with boot flag on flash drive.

I also have seen some say conversion can be done. But in UEFI Windows likes added partitions. But you convert the 100MB Boot partition into both the ESP - efi system partition and the system reserved. 

       Converting to or from GPT
[URL="http://www.rodsbooks.com/gdisk/mbr2gpt.html"]http://www.rodsbooks.com/gdisk/mbr2gpt.html
[/URL]
 How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[URL="http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html"]http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html

[/URL]        [http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
    
This user used above:
[http://ubuntuforums.org/showthread.php?t=2304736](http://ubuntuforums.org/showthread.php?t=2304736)


[URL="http://www.rodsbooks.com/gdisk/mbr2gpt.html"]
[/URL]

---


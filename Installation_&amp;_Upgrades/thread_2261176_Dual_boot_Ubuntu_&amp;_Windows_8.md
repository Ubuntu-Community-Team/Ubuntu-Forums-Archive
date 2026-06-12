---
title: "Dual boot Ubuntu &amp; Windows 8"
date: 2015-01-16
forum: Installation &amp; Upgrades
---

### Post by Joel_V on 2015-01-16
Hello!

I am currently trying to dual boot Ubuntu along side a windows 8.1 installation. Installation went fine but I cannot boot into Ubuntu, it goes straight to Windows. I've run boot-repair and here is my output:

[http://paste.ubuntu.com/9765019/](http://paste.ubuntu.com/9765019/)

This is on a Sony Vaio SVS131C1DL.

Thanks!

---

### Post by yancek on 2015-01-16
What happens when you try the suggestion in the last paragraph of the boot repair output which describes exactly your situation?

---

### Post by Joel_V on 2015-01-16
It says the operation was successful, when I try to reboot I still boot immediately to windows.

---

### Post by oldfred on 2015-01-17
One of the other fixes is to rename /EFI/Boot/bootx64.efi to really be grub or shim and boot hard drive entry from UEFI menu.

Best to make full backup/copy of entire efi partition, so you have original files. Boot-Repair may have copies somewhere in system, but best to have on another device.

       From live installer mount the efi partition on hard drive, lines with # are comments only:
#Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.
mount /dev/sda2 /mnt
#only if not already existing, (you have it so skip mkdir command)
mkdir /mnt/EFI/Boot
cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# If new folder created, the bootx64.efi will not exist, skip this command (yours exists, so backup)
mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. If not existing, may have to update UEFI also with efibootmgr.
mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi

---

### Post by Joel_V on 2015-01-18
SOLVED

If I understand correctly the problem was with how Sony has decided to implement the UEFI boot process. It looks for Windows specific files to boot. In this case one of the files it looks for is /EFI/Windows/Boot/bootmgfr.efi.

I was able to get grub running by backing up bootmgfr.efi and copying over /EFI/ubuntu/Boot/grubx64.efi and renaming it to bootmgfr.efi. After this step I was able to boot Ubuntu (through grub) but not Windows. After adding a grub entry for Windows, dual boot works!

Thanks for all the help!

sources:
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2239922](http://ubuntuforums.org/showthread.php?t=2239922)

---

### Post by oldfred on 2015-01-19
That is one of the options. And was what Boot-Repair did when we did not know about some of the other alternatives.

But I now only suggest that if none of the other options work.
If Windows does an update, it will overwrite the bootmgfw.efi file and you have to copy grub over again. And if grub does a major update you may have to copy it again.
Also you can then only boot Windows thru the grub menu, not directly from UEFI menu or perhaps one time boot key.

---


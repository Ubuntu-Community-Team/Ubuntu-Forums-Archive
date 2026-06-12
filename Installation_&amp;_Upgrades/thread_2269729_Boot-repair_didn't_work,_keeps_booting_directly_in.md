---
title: "Boot-repair didn't work, keeps booting directly into Windows 7"
date: 2015-03-17
forum: Installation &amp; Upgrades
---

### Post by quiptro on 2015-03-17
Hello all,

I have installed Lubuntu 64-bit on my laptop, with Windows 7 installed first in UEFI mode. The installation went without any problems up until I restarted the computer after the installation had finished. When the computer boots up, it goes straight to Windows 7. I tried using the recommended repair with boot-repair from a Live-USB but nothing changed.

The boot-repair gave me the following summary:

[http://paste.ubuntu.com/10617451/](http://paste.ubuntu.com/10617451/)

I would be thankful if anybody could help me figure this out and finally start using Lubuntu properly, instead of running it on a virtual machine.

Regards,
quiptro

---

### Post by oldfred on 2015-03-17
It looks like a Sony. Was it orginally Windows 8, as those Sony's modify UEFI to only boot Windows. We then have to do a work around. There are several ways to work around the issue, depending on whether dual booting or not.

Most dual booting with Windows copy grub and/or shim into the /EFI/Boot folder and rename it to be the bootx64.efi file. That is normally a hard drive boot entry in the UEFI menu. 
But I do not even see a Windows UEFI entry. Perhaps Sony only likes Windows 8?
Standard example below, your efi partition is sda3, so change to that. And you already have /EFI/Boot folder. 
Best to fully backup efi partition before moving & copying files, just in case.

       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

    
 Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi Then boot harddrive entry in UEFI menu.
Older rename of Windows efi file not recommended anymore. (old versions of Boot-Repair did rename the Windows efi file)

   From live installer mount the efi partition on hard drive, lines with # are comments only: Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.

   sudo mount /dev/sda1 /mnt
only if /EFI/Boot not already existing, run the mkdir command,
sudo mkdir /mnt/EFI/Boot
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot

   If new folder created, the bootx64.efi will not exist, skip backup command
sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup

   make grub be hard drive boot entry in UEFI. Then boot hard drive entry in UEFI menu.
sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi

---

### Post by quiptro on 2015-03-18
Thank you very much oldfred! My dual-boot is now working.

Renaming and replacing EFI/boot/bootx64.rfi with grubx64.efi did not work but one of the links you posted suggested to also rename and replace EFI/Microsoft/Boot/bootmgfw.efi with grubx64.efi, which did work and I got the grub boot menu after restart.

Now as a follow up question, how can I clean up the grub menu? At the moment it displays the following options:

1. Ubuntu (boots Lubuntu)
2. Advanced options for Ubuntu
3. Windows UEFI bootmgfw.efi (does nothing)
4. Windows Boot UEFI loader (boots up Windows 7)
5. EFI/ubuntu/MokManager.efi (haven't tried it)
6. EFI/boot/bkpbootx64.efi (I think this one booted the recovery partition)
7. EFI/microsoft.boot/bootmgfw.efi (does nothing)
8. Windows Boot Manager (on /dev/sda3) (does nothing)

I would like to remove all of the options except "1. Ubuntu" and "4. Windows Boot UEFI loader". Also, it would be nice if I could rename "Windows Boot UEFI loader" to just "Windows 7".

Many thanks for your help.

---

### Post by oldfred on 2015-03-18
If you have renamed this file, keep both a Windows repair flash drive & your Ubuntu live installer handy.
EFI/Microsoft/Boot/bootmgfw.efi

Windows updates will overwrite the bootmgfw.efi file with a new copy of it, so it is not grub anymore. And grub updates will only update the copy of grub in /ubuntu folder so you have to manually copy it over whenever grub has a major update.

I looks like Boot-Repair did create a 25_custom. You can edit that at will with anything you want. I normally add my own entries into 40_custom for the same reason. 
And you can turn off os-prober as that is finding bootmgfw.efi as a boot entry  for Windows, but you have made it grub.

You can change names in grub just by editing 25_custom and running sudo update-grub.
If in UEFI you have to use efibootmgr to edit names in UEFI menu.

       In /etc/default/grub I added this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true

If you every want to run the prober again to find new systems or boot stanza again, just change to false or delete that line.

Mokmanager is for editing the UEFI key files. Advanced, but may be required in future if Microsoft ever changes its key which Ubuntu and a few others are using for secure boot.

Some more info on efibootmgr & menu clean up in link in my signature below.

---

### Post by quiptro on 2015-03-18
Thanks a lot! Your comments have been very helpful, I managed to do what I wanted. Case closed :-)

---


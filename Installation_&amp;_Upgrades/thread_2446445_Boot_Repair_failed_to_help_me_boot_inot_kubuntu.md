---
title: "Boot Repair failed to help me boot inot kubuntu"
date: 2020-06-30
forum: Installation &amp; Upgrades
---

### Post by ochism on 2020-06-30
I tried to install kubuntu alongside my windows os, and the installer failed while setting up grub, and the  boot repair failed to fix it.
boot repair pastebin is here [http://paste.ubuntu.com/p/452rSJH8GB/](http://paste.ubuntu.com/p/452rSJH8GB/)

---

### Post by oldfred on 2020-06-30
UEFI really wants gpt partitioning. Windows requires gpt partitioning for UEFI boot of Windows, but Ubuntu does not (it should).

So your sda drive has the old MBR partitioning. If new install better to convert to gpt & reinstall now before you have done configuration. But you always should have good backups, so reinstall is always an option.

Your Ubuntu UEFI entry shows boot from the ESP on the Windows drive, to a drive that does not now exist.
And you have an ESP on the MBR drive that has Ubuntu UEFI boot files, but no entry in UEFI to use those files.
UEFI boot entry uses GUID/partUUID to know which ESP - efi system partition to boot from.
See this to see GUID and detailed UEFI entries, like shown in report on line 113.
sudo efibootmgr -v

This shows UUID & partUUID
lsblk -o name,fstype,size,fsused,label,partlabel,mountpoint,partuuid

If you convert sda to gpt, you have to do a total reinstall of grub from Boot-Repair's advanced options.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Be sure to have good backups. If you use gparted to change to gpt, it erases entire drive.
Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)
Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

See
man efibootmgr

Even if you do not convert to gpt, you need a full reinstall of grub to add a correct UEFI boot entry or use efibootmgr to add a correct entry.
And use efibootmgr to remove old UEFI boot entries to avoid confusion.
 from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B

---


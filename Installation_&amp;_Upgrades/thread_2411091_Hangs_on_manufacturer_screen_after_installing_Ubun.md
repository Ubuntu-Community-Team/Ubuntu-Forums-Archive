---
title: "Hangs on manufacturer screen after installing Ubuntu 18.10 from live USB"
date: 2019-01-24
forum: Installation &amp; Upgrades
---

### Post by greedylizard on 2019-01-24
Hi there!  I was trying to get any Linux OS on an old Toshiba Satellite C55-B5352 laptop that was running Windows 10 before.  Ubuntu hangs on the Toshiba manufacturer screen upon starting up, but by holding F12 when the USB is in I am still able to boot from the live USB so all is not lost it seems.  I did a standard installation, no messing with partitions or anything, just removing the previous OS since I didn't want it.  I'm hoping I didn't make a mess of things when I was experimenting with Mint and Fedora installations earlier (which also wouldn't boot). The laptop has secure boot disabled and is in UEFI boot mode. I have an alternate laptop I can use to flash the USB again if needed and can post any additional information needed!

---

### Post by oldfred on 2019-01-24
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If you have UEFI, it is less than 5 years old.
You should update UEFI from Toshiba.
Some Toshiba's only booted from the UEFI fallback entry /EFI/Boot/bootx64.efi which may show as a UEFI:hard drive or similar entry in UEFI.
It used to be we had to manually copy shimx64.efi to bootx64.efi, but now grub installs it, or Boot-Repair will auto do the copy.

       
 May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boto-info summary report ( do not post report), the auto fix sometimes can create more issues.


Perhaps similar:
       Toshibs C55-B5356 "Failed to open \EFI\BOOT\grubx64.efi - Not Found" 
[https://ubuntuforums.org/showthread.php?t=2387851](https://ubuntuforums.org/showthread.php?t=2387851)
Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba Satellite P55-A (UEFI) [SOLVED] Trouble installing Xubuntu 14.04 - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)

---

### Post by greedylizard on 2019-01-24
[http://paste.ubuntu.com/p/wfN2nnFXyq/](http://paste.ubuntu.com/p/wfN2nnFXyq/)

The results of the boot repair summary report are above.  I haven't updated the UEFI yet.  I see something listed as a BIOS update for it (which I assume is it), but need to see if I can find another flash drive or something first.

UPDATE: I tried to put the BIOS updater on a flash drive, but it would not load.  I think it is only meant for CDs/DVDs judging by the readme file that came with it.  The only computer I have that can burn a disk is the one that I tried to put Ubuntu on, and it isn't allowing me to burn an iso from the live USB.

---

### Post by oldfred on 2019-01-24
I would run the suggested repairs by Boot-Repair. And update UEFI.
I do not remember for sure now, but I thought my 2006 BIOS Toshiba updated from flash drive. But for a long time I did still have XP on it and may have used that. Has to be FAT32 formatted.

You are not showing the fallback /EFI/Boot/bootx64.efi, but show some other files there.

You also can houseclean out of the ESP the /EFI/fedora folder and the UEFI entries to boot fedora since that is not there anymore.
       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---

### Post by greedylizard on 2019-01-24
When I ran the suggested repairs I got this error:
[http://paste.ubuntu.com/p/yvPTzc4jbM/](http://paste.ubuntu.com/p/yvPTzc4jbM/)

In addition, my attempt to update the UEFI through a disk I burned did not seem to work.  Sorry for the photo quality, I tried to make sure everything could be read.  It doesn't do anything once it reaches this part, do I have to input something?

[IMG]https://i.imgur.com/DxFj20M.jpg?1[/IMG]

---

### Post by oldfred on 2019-01-24
It says grub installed correctly. And you do not show a correct UEFI boot entry for Ubuntu in EFI boot menu.
I think error it is saying you have is related to flash drive. That is often created with dd, and then does not have standard partition table, but a hybrid for dvd or flash drive configuration.
It looks like if you select ubuntu in UEFI boot entry using f12 you should boot.

Is your system using an EFI shell program for updating UEFI. 
My UEFI systems (motherboards in desktop system) do not do it that way, but my old Toshiba just updated.
Most systems I have seen have several ways. From Windows, from a DOS bootable flash drive and directly from inside UEFI. Now some systems can also do it directly from Linux.

---

### Post by greedylizard on 2019-01-24
This laptop seems to have unconventional F12 functions, it allows selecting to boot from the HDD/SSD, USB, ODD, or LAN.  It doesn't seem to allow me to select which OS I want from one of these options.

As for the UEFI updater, I honestly have no idea what is going on there.  The screen I got when using the burned disk to update didn't look anything like what other users were getting online when updating AND it didn't seem to work either.

I'm starting to suspect either I or Toshiba (or perhaps both) have screwed up royally.

---

### Post by oldfred on 2019-01-25
The EFI Shell is normally an advanced command line tool to edit UEFI settings. I am not really familiar with it, but did not think it was used to update UEFI.

---


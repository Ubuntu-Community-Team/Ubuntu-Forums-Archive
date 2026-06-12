---
title: "Dual Boot ubuntu 22.04 with bootable sandisk drive. Grub does not display boot option"
date: 2022-06-11
forum: Installation &amp; Upgrades
---

### Post by dbayler on 2022-06-11
[https://paste.unbuntu.com/p/9K8vhG3XCF/](https://paste.unbuntu.com/p/9K8vhG3XCF/)


[LIST]
[*]n which step, the installer throw an UEFI error? Partitioning or installing?                                 – [Emoji]("https://askubuntu.com/users/1037951/emoji")                 
                 [yesterday]("https://askubuntu.com/questions/1413252/dual-boot-ubuntu-22-04-with-bootable-sandisk-drive-grub-does-not-display-boot-o?noredirect=1#comment2456761_1413252")             
         

[*]                                   
                                                                                                     
         

[*]                                               You should only have one ESP  per device/drive. If ESP that Windows is using is not correctly seen  make sure Windows fast start up is off. Please copy & paste the  pastebin link to the Bootinfo summary report ( do not post report), do  not run the auto fix till reviewed.Lets see details, use ppa version  with your USB installer (2nd option) or any working install,  not  Boot-Repair ISO  [help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")   &            [sourceforge.net/p/boot-repair/home/Home]("https://sourceforge.net/p/boot-repair/home/Home/")                                 – [oldfred]("https://askubuntu.com/users/126395/oldfred")                 
                 [yesterday]("https://askubuntu.com/questions/1413252/dual-boot-ubuntu-22-04-with-bootable-sandisk-drive-grub-does-not-display-boot-o?noredirect=1#comment2456777_1413252")             
         

[*]                                   
         
                                                        The UEFI error occurred at the initial startup after installation.  Reference [paste.unbuntu.com/p/9K8vhG3XCF]("https://paste.unbuntu.com/p/9K8vhG3XCF/")                                 – [Dan]("https://askubuntu.com/users/1602863/dan")                 
                 [yesterday]("https://askubuntu.com/questions/1413252/dual-boot-ubuntu-22-04-with-bootable-sandisk-drive-grub-does-not-display-boot-o?noredirect=1#comment2456908_1413252")                                                                               


[/LIST]

---

### Post by oldfred on 2022-06-11
You have an old Vista BIOS install? That would be from before UEFI, so system is UEFI with very old Windows?

Windows only boots in BIOS mode from MBR(msdos) partitioned drives.
Windows only boots in UEFI mode from gpt partitioned drives.
You cannot have Windows BIOS mode & Ubuntu UEFI mode on same drive, and generally all installs need to be same boot mode.
But UEFI hardware should have UEFI installs.

The reason UEFI & BIOS Windows do not mix is that Windows must have boot flag on its boot partition, your sda1.
But UEFI will move boot flag to the ESP- efi system partition. Only one boot flag per drive.

You first need to delete all the duplicate UEFI boot entries.
# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

Do you really want to keep the very old obsolete Vista install?
Conversion to gpt typically erases drive to be sure to have good backups of any data you want to keep.
You really want UEFI installs on UEFI hardware.

---


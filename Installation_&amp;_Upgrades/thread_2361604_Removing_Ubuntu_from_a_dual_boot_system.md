---
title: "Removing Ubuntu from a dual boot system"
date: 2017-05-18
forum: Installation &amp; Upgrades
---

### Post by Neil_Nand on 2017-05-18
Hello,

This seems to be the most relevant place to post this, currently I have a dual booting laptop with Windows 10 & Ubunutu 16.04 (I think, it's 16 something). What is the best way to remove Ubuntu & have Windows use the whole hard drive and have no dual booting?

---

### Post by LastDino on 2017-05-18
Your primary concerns can be>
1. Boot type> I'm assuming UEFI as it is Win 10 machine it seems
2. Boot-loader Manager> Right now, you must be using "Grub", you will need to change that using your Windows recovery disc and install windows boot manager. 
3. Partitioning scheme> You will need to get rid of Linux Partitions

First thing first
 [B]Take Backup of all your data

Easy guide (Although old)

[/B][URL="https://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on"]https://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on

[https://itsfoss.com/uninstall-ubuntu-linux-windows-dual-boot/](https://itsfoss.com/uninstall-ubuntu-linux-windows-dual-boot/)
[/URL]

---

### Post by oldfred on 2017-05-18
Best to make sure you have Windows as default boot before deleting any partitions.
And make sure you have a Windows repair DVD or flash drive.

If UEFI:
Go into UEFI and change boot order so Windows is first.
 Uninstall Ubuntu from menu, Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi) 


If BIOS 
reinstall Windows boot loader to MBR first.
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Then you can delete Linux partitions, better to use gparted from Ubuntu installer to delete them.
Then use Windows partition tools to expand Windows partition.

---


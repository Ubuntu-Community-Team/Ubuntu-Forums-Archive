---
title: "Grub not displaying Windows 7"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by JohQ on 2010-01-19
Hi!

I have just installed my system from a scratch, and got some problems with grub.

Basically, i have 3 OS and 4 hard drives. First is for Ubuntu, second for Win7 and third for WinXP (they are on AHCI mode, and drive listing in BIOS gives me that order). The last one is for backups.

Ive set up the BIOS to load from Ubuntu disk so i could choose with grub which system i wish to use. For a reason or another, grub only displays Ubuntu Linux & WinXP, no windows 7.

Ive searched the net for probably 14hours by now, and tried everything i found, even reinstallation of linux.

In most cases i found it was something to do with the /boot/grub/menu.lst file, but i don't even have it!

Im running
Ubuntu 9.10 (32-bit), and i assume my grub is version 1.97beta 4
WinXP SP3 (32-bit)
Win7 (full version, not the RC or beta)(64-bit)

Due to some earlier problems, while installing XP & Win7 i had all other drives unplugged, and while installing ubuntu i had all drives plugged.

Note: When i installed Win7, i let it (due to problems, again:roll:) do the hard drive partitioning and formatting all by itself, so on the Win7 disk i have two partitions, both created by the installer.

(ill post the disk listing soon..)

Im kinda stuck, so if anyone has an idea what to do next, please share it :)

---

### Post by darkod on 2010-01-19
I have never had two versions of windows on my computer but it has been mentioned on this forum that windows combines the bootloader of the two versions. This might be part of the issue since you had all other drives disconnected while installing both XP and 7.
The way I understand it, if 7 finds installed XP it will combine its bootloader with entries for both 7 and XP. In your case there was nothing to find.
But having said that, ubuntu should still be able to see both 7 and XP and add them to grub menu. You said you had all drives connected while installing ubuntu.

Can you download the script in my signature, move it on desktop for example, and run it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with info about your boot process and boot files. Copy the content of the file here and wrap it in CODE tags for easier reading (with the text selected hit the # button in the toolbar above).

---

### Post by JohQ on 2010-01-19
Thanks for the fast reply. Sorry for this, it makes no sense, but by running "sudo update-grub" in the terminal it suddenly found windows 7 (did it just for the heck of it while waiting for updates to finish), even though i had already ran that command thousands of times before.

---


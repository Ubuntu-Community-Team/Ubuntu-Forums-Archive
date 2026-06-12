---
title: "Installing grub on a usb flash drive"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by tatortot on 2007-10-18
Ok, I know this can be done I just don't know how. I want to install Ubuntu to a third partition on my computer, but want to leave my MBR alone. I want my thumb drive to have GRUB on it so when its plugged in my Ubuntu partition will boot and without the thumb drive everything will be the same. I know my computer can boot from the drive because I had Damn Small Linux on it at one point.

Is there somewhere in the installer for 7.10 to specify where to put GRUB or is there another way to get this to work?

---

### Post by LainattheWired on 2007-10-18
[[COLOR="Red"]Solution[/COLOR]]("http://ubuntuforums.org/showthread.php?t=500723")

---

### Post by tatortot on 2007-10-18
> Make sure your bios allow boot from usb
When fresh install identify your usb partition, say /dev/sdb1 (example)
When asking to install bootloader, select /dev/sdb1 root partition.
I have installed Ubuntu twice using this method and all I get when the computer boots is the word GRUB in the corner of my screen. I know for a fact grub is on the thumb drive because once I restart and remove it, windows boots normally.


> For existing install, identify your desired usb booting partition, say /dev/sdb1
As root>grub-install /dev/sdb1
Mount /dev/sdb1 to say /mnt/usb (root>mount /dev/sdb1 /mnt/usb)
Copy your current boot loader menu.lst to usb device
root>cp /boot/grub/menu.lst /mnt/usb/boot/grub/
Identify your usb partition's UUID
root>vol_id /dev/usb1 | grep UUID
Copy the UUID for the booting partition to your menu.lst file to replace UUID
Since I cant boot into my Ubuntu install I have tried following this to the best of my ability from the live cd. 

Could someone give me step by step directions to reduce the possibility of me screwing it up.

---


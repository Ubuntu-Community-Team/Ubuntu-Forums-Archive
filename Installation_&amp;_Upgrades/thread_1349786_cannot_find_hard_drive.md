---
title: "cannot find hard drive"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by decipherfreak on 2009-12-08
I tried dual booting easypeasy, which caused some errors in my xp partition maybe because I didnt defrag it first. I have an eeepc 1005ha, so I tried F9 to restore, but it no longer worked, so I deleted the partition with ubuntu on it. Now when I try to boot I get the Grub error 22. I tried loading a XP install on a usb drive and booting from that. When I choose to boot the GUI mode option, it starts to load XP then blue screens. Then I tried the text mode boot, it leads to Windows Setup. Here I tried to use fixmbr in the Recovery Console, and also tried to do fresh install, but both in both options the setup can't find my hard drive.

HELP!!!!!

---

### Post by darkod on 2009-12-08
Hold on, it all got mixed up. Both XP and Ubuntu can't see the drive to install on it? Boot with the ubuntu cd/stick and open Gparted (in System - Administration). That's GUI partition manager. What does it show about your drive?
If you right click on a partition in the list I think it even offers Check option to check the partition. The only think, it must not be mounted (not to have keys symbol next to it). You can unmount with right click too (or select swapoff for swap).

---

### Post by decipherfreak on 2009-12-09
I tried booting from ubuntu live usb as well but when it reaches unetbootin screen it just loops the countdown, when I click default it just refreshes the countdown. This happened before when the usb drive was formated FAT instead of FAT32 but this time it is FAT32.

---

### Post by decipherfreak on 2009-12-09
I tried the live usb on another computer and it didn't work either. I tried reformatting the usb but it didn't help. Is there something wrong with the usb drive? The easypeasy iso file is the same.

---

### Post by darkod on 2009-12-09
OK, unetbootin menu is sometimes weird. Format the stick as FAT32 if it's not. Then again use unetbootin to put the ISO on it, just in case. After it finished ignore the question to reboot, just close unetbootin.

To get rid of the unetbootin menu and have the ubuntu main menu open the stick in windows and do:
1. In the root folder rename syslinux.cfg to syslinux.old
2. In the isolinux folder find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

That will enable the ubuntu main menu. The above is if creating the stick on windows.

If you have working ubuntu on another computer just go in System-Administration and use the USB Startup creator. In that case you don't need to change anything, it works fine straight away.

---

### Post by decipherfreak on 2009-12-09
Now it doesn't go the unetbootin screen. It just says

could not find kernel image: linux
boot:

---

### Post by darkod on 2009-12-09
> **decipherfreak said:**
> Now it doesn't go the unetbootin screen. It just says

could not find kernel image: linux
boot:

Sounds like the files are not there. It has always worked. Format the stick again, to make sure everything is deleted, and try creating it again. Run unetbootin as administrator (right click, Run as Administrator).

---

### Post by decipherfreak on 2009-12-09
I reformatted, and ran again as administrator, changed file names, same result. Should I try another iso? or is it the computer

---

### Post by darkod on 2009-12-09
> **decipherfreak said:**
> I reformatted, and ran again as administrator, changed file names, same result. Should I try another iso? or is it the computer

Very strange. I have created few times a stick with different image for my netbook (because I was trying both UNR and Desktop 32bit versions), and it always worked straight away.
An image corrupted during download might be the reason, but I can only speculate. You said that with unetbootin menu it didn't work either, so it can be an image problem. Otherwise unetbootin menu Default is working fine but the difference is it starts the Install Ubuntu option directly, while with the standard menu you have option for Try Ubuntu too.

---

### Post by decipherfreak on 2009-12-09
Yay, I loaded up an iso of full ubuntu and it booted. In GParted it shows all of the hard drive.

/dev/sda1   ntfs          72.06 GiB        flags: boot
/dev/sda2   extended  72.05 GiB
    unallocated             72.05 GiB
/dev/sda3   fat32   PE   4.89 GiB         flags: lba
/dev/sda4   unknown    47.07 MiB

This is what it looked like before all hell broke loose. How do I get original partitions back? Dual booting can wait for later, XP comes first for me.

---

### Post by darkod on 2009-12-09
> **decipherfreak said:**
> Yay, I loaded up an iso of full ubuntu and it booted. In GParted it shows all of the hard drive.

/dev/sda1   ntfs          72.06 GiB        flags: boot
/dev/sda2   extended  72.05 GiB
    unallocated             72.05 GiB
/dev/sda3   fat32   PE   4.89 GiB         flags: lba
/dev/sda4   unknown    47.07 MiB

This is what it looked like before all hell broke loose. How do I get original partitions back? Dual booting can wait for later, XP comes first for me.

Well, under the assumption that your XP is on /dev/sda1, you only need to restore the windows bootloader on the MBR. However, depending how that repair process develops, it might be a faster way to install Ubuntu and the grub2 bootloader should boot your XP without any problems. In case you decide to do this, first in Gparted from the LiveUSB delete /dev/sda2 too, not to exist as extended partition. That space will be marked unallocated.
Then reboot with the LiveUSb again, but this time select Install Ubuntu option, and at step 4 just tell it to use the Largest Available Free Space. That will install it in the unallocated 72GB.
If you decide to go with XP repair first, there is a guide here, scroll down:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---


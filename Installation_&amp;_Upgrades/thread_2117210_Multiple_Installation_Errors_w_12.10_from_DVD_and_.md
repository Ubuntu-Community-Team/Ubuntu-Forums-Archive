---
title: "Multiple Installation Errors w/ 12.10 from DVD and USB Drive"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by emdub on 2013-02-17
Hi everybody, I'm new to the board and to Ubuntu. Finally decided to install and am running up against multiple errors attempting to install 12.10 64bit.

[INDENT]1. First tried to install from CD, but image was too big to burn on disc, so burned to DVD. Booted from DVD, and screen was purple with the keyboard/human icon for a long time. Eventually an unable to read sector error came up and I ended up aborting the install.

2. Made a bootable usb drive with the recommended Universal USB Installer utility. Booted from usb and made it to the ubuntu loading screen. Eventually went to command prompt with error "unable to find a medium containing a live file system."

3. Checked the forum and saw it mentioned to try a different usb port (specifically a usb 2.0 or older). Changed ports, and tried again but this time it reported error "unable to enumerate usb device on port 3."

3. Restarted with drive in another usb port, but was unable to boot anymore. Error reported was "no configuration file found."

4. Went back into Windows and recreated the bootable usb drive from the iso, and now I'm still getting the "unable to enumerate usb device" error.[/INDENT]

Anyway, I'm not sure what else to try at this point. Was hoping that install would have been a bit simpler but maybe someone can point me in the right direction?

Trying to make a dual boot system with the following specs:
Mobo: Gigabyte GA-MA785GM-US2H
CPU: AMD Phenom II X6 1100T
RAM: G.Skill 4GB
Gfx: GeForce GTX 460
Currently on Win XP SP3

Thanks in advance!

---

### Post by baseballa51 on 2013-02-17
I had this problem before.

Recreate your USB drive installation formatted in FAT16 (FAT) -- NOT FAT32.

After it's created open the drive to view contents.

There should be a folder named 'isolinux'. Change it to 'syslinux'.

Inside the newly-named 'syslinux' folder there should be 2 files named isolinux.bin and isolinux.cfg. Change them  to syslinux.bin and syslinux.cfg.

This should get rid of not being able to locate the configuration file.

Let me know if this helps.

---

### Post by emdub on 2013-02-18
Thank you for your reply. I am not able to reformat the usb drive in FAT16, locked into FAT32 and exFAT. But I will try your other suggestions and see if that helps.

---

### Post by emdub on 2013-02-20
Changed the file names to match as suggested and was finally able to begin with the installer! Thank you so much ^_^.

Of course now I'm running into new problems... the first being that quick installation didn't allow me to choose which drive to install Ubuntu on. It just started automatically installing on my primary drive, which isn't what I wanted.

The bigger problem, however, is that after installing, Ubuntu won't boot. It gets to the boot loader and when timer runs out or I select Ubuntu, the system just reboots. Not good... any thoughts?

---

### Post by oldfred on 2013-02-22
You have to use manual install or Something Else to get the option on which drive's MBR to install the grub2 boot loader into. It defaults to sda for all standard installs.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

    
What video card? Sometimes after the install you need nomodeset until you install the proprietary drivers.

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by emdub on 2013-02-27
Hi oldfred, thank you so much for the info. The links were very helpful and I managed to get Ubuntu installed on the second drive.

Unfortunately I am back at the problem of the installation not booting. I get to grub, and when choosing Ubuntu to boot from my screen goes black and system reboots. I have tried using nomodeset but this had no effect (and I am running a GeForce GTX 460).

I am also unable to boot into recovery mode, so nothing seems to help.

Will continue to keep looking for possible solutions, but if you could shed some more light on this issue I would be grateful.

---

### Post by oldfred on 2013-02-27
With a nVidia card you definitely need nomodeset. Have you removed quiet splash so you can see what loads or if you can spot another error? It does go by quickly.

Some systems need other boot options or perhaps settings in BIOS. Is BIOS in LBA, large or preferred AHCI, but not IDE? XP may not work with AHCI unless you installed those drivers when installing XP, so maybe LBA?

---


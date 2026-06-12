---
title: "Problem Copying Ubuntu to SD Card"
date: 2014-09-25
forum: Installation &amp; Upgrades
---

### Post by joe69 on 2014-09-25
So I already googled this issue several times. I also apologize if this has been posted to the wrong sub-forum.

Goal: Copy 14.04 off hard drive onto SD card, boot from SD card. Please help, I'm lost <snip>.

Attempt 1: Create Image using "Disks" on Ubuntu 14.04, to create a copy of the bootable Ubuntu with all my personal files
Result 1: Failed, gave cannot create image quark error 13 error.

Attempt 2: Create Image using "Disks" on Ubuntu 12.04 (live booted from USB with primary hard drive not being used), to create bootable Ubuntu backup with personal files
Result 2: Same as above.

Attempt 3: Copy hard drive using "dd" to SD card, then attempt to boot from it.
Result 3: All files copied over, unable to boot.

Attempt 3.1: Install another fresh Ubuntu 12.04 load out to different partition on SD Card with GRUB installed. Existing Ubuntu 14.04 files on seperate partition.
Result 3.1: Unable to boot 14.04

Attempt 3.2: Copy Hard drive using dd to SD card partition with Ubuntu 12.04 already installed and bootable on another partition. (Reverse of Attempt 3.1)
Result 3.2: Unable to boot 14.04

Attempt 4: Use dd to copy hard drive, then modify partition to "Bootable" and mount at root.
Result 4: Unable to boot.

I continued to combine attempts 3.1, 3.2 and 4 and still could not boot.

Hardware: HP Mini 1116NR 100 Series. 1GB of ram, 16GBSSD (ribbon wire connected so I can't connect it to another machine to image it). N270 Atom Processor (32bit, 1.6Ghz)

Update-The hardware does possess the capability to boot from an SD card, but I have tried copying both to the SD card through the SD card reader and through a USB adapter (its a micro SD, Class 10 64GB). I was able to run, Ubuntu 12.04, Mint Linux and Node Zero all off the SD card.

---

### Post by Vladlenin5000 on 2014-09-25
Hi, welcome.

Booting from a SD isn't possible for many computers that do boot from USB. Many BIOS/UEFI don't recognize certain memory card readers as bootable devices anyway. OTOH, external USB memory card readers usually work. I had several installers in microSD cards booting in a $1 microSD to USB adapter.

---

### Post by joe69 on 2014-09-25
Tried that as well, regardless of whether the SD card is in the slot or the USB port it doesn't boot the 14.04 copied from my hard drive but will boot any other Linux distro.

---

### Post by yancek on 2014-09-25
> Attempt 3.1: Install another fresh Ubuntu 12.04 load out to different  partition on SD Card with GRUB installed. Existing Ubuntu 14.04 files on  seperate partition.

After installing 12.04, you tested it by successfully booting, correct?  Did you use dd then to copy the 14.04 files from your other hard drive to the SD Card?  Did you run sudo update-grub from 12.04?  Are you selecting the SD Card as first boot priority with the 12.04 Grub code in the mbr?

---

### Post by oldfred on 2014-09-25
Your dd may not work as duplicate UUIDs are not allowed and system has issues. You may be able to change UUID, update fstab and reinstall grub after you copy to SD card.

Why not just a new install to SD card, then copy your /home over to SD card so it has you data and user configuration. If you changed any hardware type system settings those would be in /etc, but only copy if same version of Ubuntu as different settings may be needed if different version.

---

### Post by joe69 on 2014-09-25
> After installing 12.04, you tested it by successfully booting, correct?  Did you use dd then to copy the 14.04 files from your other hard drive to the SD Card?  Did you run sudo update-grub from 12.04?  Are you selecting the SD Card as first boot priority with the 12.04 Grub code in the mbr?

So when I would boot I hit F9 and select the SD card to boot from, the grub menu appears and showed Ubuntu 12.04 (installed on SD card), Linux Mint (installed on SD card), and Ubuntu 14.04 (installed on hard drive) it would not show the Ubuntu 14.04 installed on the SD card as a boot option after dd.

> Why not just a new install to SD card, then copy your /home over to SD card so it has you data and user configuration. If you changed any hardware type system settings those would be in /etc, but only copy if same version of Ubuntu as different settings may be needed if different version.

I don't have access to the internet on that computer at this time, I only can get on the internet with my work computer (secured network), and I don't have a 14.04 iso, otherwise I would just install 14.04 on the SD card fresh, and move all my programs over.

---

### Post by joe69 on 2014-09-26
Okay so now after formatting the SD card as NTFS, then trying the dd trick again (booted off Linux Mint live USB drive), I can get to the Ubuntu start up screen (Says Ubuntu with loading dots below it), but then it fails to mount the drive and gives me two options, skip mounting (defaults to hard drive) or Manually fix (which gives me a command line and I can't do anything. I am going to be attempting to change the UUID today after work and see if that helps.

---


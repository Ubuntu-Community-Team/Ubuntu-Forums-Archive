---
title: "Don't work Live USB"
date: 2024-01-06
forum: Installation &amp; Upgrades
---

### Post by olklym on 2024-01-06
I bought a laptop without an OS. I install Linux via a USB stick.

1) Installed Lubuntu first. All norms were immediately established. But it turns out that Lubunta is based on KDE components, I don't like it. Demolished the system.

2) I install Linux Lite. It is installed via "internal" Grub. Grub does not see vmlinuz for some reason and therefore cannot boot the system. Tortured - demolished.

3) Installed Puppy Linux (old version, based on Ubuntu). It works fine from a flash drive. But it cannot be installed on the hard disk. What I didn't do: I re-partitioned the disk, and registered grub (Puppy Linux is also started through grub) in different logical drives - it didn't help.

4) And, it seems, just in the process of this, I damaged something.

5) Now I want to install Xubuntu. But I don't have Live USB booting.

6) When I start the computer, it automatically starts grub from the hard drive and then tries to start Puppy Linux, but it can't.

Everything is set up correctly in Bios/UEFI:

• Bios/UEFI mode: both (both options), UEFI first (trying UEFI first).
• loading from USB - in the first line.

I tried to launch Live USB manually via F12 - it does not load.

I tried to turn off booting from the hard drive in Bios/UEFI in general - it still does not see Live USB.

7) What do I have now?

The hard disk is divided into 4 disks:
• sda1 - for Grub - 500 MB, in fat32 format,
• sda2 - for Linux - 35 GB, in gpt4 format,
• sda3 - for files - 84.5 GB, in gpt4 format,
• sda4 - swap file - 8 GB, in linux-swap format.

When the computer starts, grub is started from the hard drive.

He sees (ls) :
(memdisk) (hd0) (hd0,gpt1) (hd0, gpt2) (hd0,gpt3) (hd0,gpt4) (hd1)

When I want to see the file system of a USB stick:
ls (hd1)
Device hd1: No known filesystem detected - Sector size 512B - Total size 60088320KiB.

Accordingly, I cannot manually find and run vmlinuz

The USB stick was made as a Live USB with the EtchDroid (Android phone program). I recorded all previous Linuxes in the same way. The USB-stick is definitely working and everything is definitely written there in the correct format.

On another computer, these same Live USBs with both Xubuntu and Puppy Linux work perfectly. So, it is burned correctly. ///And I will repeat it again. THIS SAME Live USB on my laptop BEFORE installing Grub was working fine. AFTER installing Grub on the hard drive, the laptop stopped working with THIS SAME Live USB Puppy.

How to run Live USB?

---

### Post by yancek on 2024-01-06
> But it turns out that Lubunta is based on KDE components, 

Lubuntu uses LXDE/LXQT desktop environment not KDE.  Kubuntu uses KDE.

Each time you try to boot the USB, do you go into the BIOS firmware and verify that the usb is set to boot first?  If it was, it should not try to boot from the hard drive.  This would be the same process you used to boot/install Lubuntu.  Is that what you are doing and it is failing?

If no known filesystem detected is the error when trying to access the usb, I don't see how it will boot.  The usb may have been damaged in some way during your various efforts so since getting this error, does the usb still boot on another machine?

---

### Post by olklym on 2024-01-06
> **yancek said:**
> 

Each time you try to boot the USB, do you go into the BIOS firmware and verify that the usb is set to boot first?  If it was, it should not try to boot from the hard drive.  This would be the same process you used to boot/install Lubuntu.  Is that what you are doing and it is failing?

Yes, of course. I verify that the usb is set to boot first. 
> **yancek said:**
> 
If no known filesystem detected is the error when trying to access the usb, I don't see how it will boot.  The usb may have been damaged in some way during your various efforts so since getting this error, does the usb still boot on another machine?

Live USB work in another computer.

---


---
title: "Can't boot Ubuntu off a USB drive"
date: 2015-11-03
forum: Installation &amp; Upgrades
---

### Post by Lukoworgos on 2015-11-03
Hi!  I'm trying to run Ubuntu off of a USB drive but it's not working, and I was wondering if you could help me troubleshoot.

To install Ubuntu on a USB stick, I followed the instructions here:  [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)  I used Ubuntu 14.04.3 LTS.

Whenever I try to boot the OS from the USB drive, I get the error message "No DEFAULT or UI configuration directive found!  boot:  (blinking cursor)"

I've had the same problem with two different USB sticks (PNY 32 GB USB 3.0 and Lexar 32 GB) and on two different computers, my laptop and my desktop.

What's going wrong?  What do I do to fix it?

---

### Post by Bucky Ball on 2015-11-03
Welcome. Just a stab in the dark, but was your USB completely blank and formatted to FAT32 prior to creating the USB installer? If not, give that a try. Wipe everything from the USB, format it as FAT32, give it another shot with Universal USB Installer. Let us know what happens. Where did you download the 14.04 ISO from?

Also, do you have Windows installed? Are you booting the USB stick in UEFI mode? If you have Windows installed, try booting the stick in UEFI mode. (Another stab.)

---

### Post by Lukoworgos on 2015-11-03
One of the sticks was completely blank (fresh out of the package!) before I used Pendrivelinux on it.  I formatted both sticks to FAT32 as a part of the installation process.

I downloaded the 14.04 ISO from here:  [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

On the laptop, I have Windows 7 installed.  On the desktop, I effectively don't have any OS.

What's UEFI mode?  ETA:  I went through the BIOS on my laptop and didn't find any options for UEFI mode.

---

### Post by sudodus on 2015-11-03
Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It helps us help you :-) Otherwise we can only guess.

---

### Post by Lukoworgos on 2015-11-03
I mean...I've had the same problem on two different computers with completely different builds and specs (one a top-of-the-line desktop I built less than a year ago, the other an eight-year-old laptop).  The USB stick might be the problem, but I don't think the computer hardware is.

---

### Post by sudodus on 2015-11-03
You might need different iso files and different methods for the two computers.

Have you checked the md5sum (that the iso file is correct)?

You can try with another tool to create the USB boot drive.

There may be problems with the graphics driver - you may or may not need different proprietary drivers for your graphics chips.

---


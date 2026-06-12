---
title: "GRUB error when external disk is attached"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by pte on 2007-10-28
Hi all!

Ubuntu 7.10 works fine on my laptop (HP dv9670). Only when I have an external harddisk attached to the laptop then GRUB gives an error (usually error 22, with my usbdisk also other errors). It seems  that attaching an external disk during boot somehow reorders drive letters and confuses grub.

Has anyone had similar problems and knows of a way to solve this?

With kind regards,
Pieter Eendebak

---

### Post by Smoother on 2007-10-28
I have the same problem with my laptop and my desktop system.

Whenever I plug in an external hard drive (USB) or a USB stick I get Grub error 22.

---

### Post by Donkerewolf on 2007-10-28
Have you tried mounting the USB drive manually from a commandline?

---

### Post by Smoother on 2007-10-28
Whenever I plug in the drives after Linux or Windows is booted, they work fine and I can access all my data. 
Is that the questions you had? Because I never had to mount them manually in Linux to make them work.

---

### Post by pte on 2007-10-31
The usbdisk works fine if I attach it after the system has booted. But I do not want to disconnect and reconnect the cables each time I reboot or start up my laptop.

---

### Post by It_Was_Luck on 2007-10-31
Your computer might be set to boot to USB, so when Grub comes up it goes in a says to Grub "Look for the OS file on the USB drive!" 

Well Grub Error 22 is because it can't find the OS... this is because your computers boot priority might be set to USB so as I said Grub might be told to look in a place Linux is not.

---

### Post by meierfra on 2007-11-01
Trying changing the boot order in the bios. The usb-drive needs to be after the  internal drive.

---

### Post by pte on 2007-11-03
Changing the boot order in the BIOS did not work. I solved the problem by copying the boot files (/boot/grub/) to my external HD.

---


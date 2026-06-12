---
title: "Question: Is it possible to install Ubuntu fully onto a USB?"
date: 2017-08-22
forum: Installation &amp; Upgrades
---

### Post by skylarkblue1 on 2017-08-22
Apologies if this is a silly question, but I can't seem to find a definitive answer online for this. I installed and made a boot able USB stick with Ubuntu on it so I can boot it on my laptop that has windows on it. Found out that what I can use on the USB stick, the things I save on it gets removed after I shut it down which really sucks. It says I can install ubuntu, but looking online about it, that just installs it to the hard drive, which I can't/don't want to do. So, is it possible to properly install it to the USB stick? Or have I just got to deal with it flashing the "OS" every time I boot it?

---

### Post by RobGoss on 2017-08-22
Hello and welcome to the forums, You can install Ubuntu on a USB drive this link might shed some light on what's needed to create it
[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

I'm sure others will have better knowledge on how to achieve it

---

### Post by ajgreeny on 2017-08-22
Just be careful if the machine uses UEFI rather than legacy BIOS, as in a UEFI system the grub bootloader will always be installed on the internal drive, sda, and not the USB drive, sdb?, where you will want it, even if you ask the Ubuntu installer to put grub on sdb.

Even a persistent live USB as suggested by **RobGoss**, which can save your personal files, can not be updated or have any new packages added as they will be lost on reboot.

---

### Post by RobGoss on 2017-08-22
> **ajgreeny said:**
> Just be careful if the machine uses UEFI rather than legacy BIOS, as in a UEFI system the grub bootloader will always be installed on the internal drive, sda, and not the USB drive, sdb?, where you will want it, even if you ask the Ubuntu installer to put grub on sdb.

Even a persistent live USB as suggested by **RobGoss**, which can save your personal files, can not be updated or have any new packages added as they will be lost on reboot.

Good catch, the OP might not want to use a primary machine and over ride any other boot loader. Make sure you know what's involved

---

### Post by pbear42 on 2017-08-22
FWIW, I've had good luck so far with the solution given at Post #45 of [this old thread]("https://ubuntuforums.org/showthread.php?t=2213631&p=13391873#post13391873").  In fact, I was only willing to give Ubuntu a try (started out on Mint) if I could find a way to boot an external drive in UEFI.  Importantly, for the linked method to work, Ubuntu has to be installed from BIOS or legacy mode (using the "Something Else" option).  The EFI boot loader is then installed from Terminal.  After that, though, it boots fine in either UEFI or BIOS.  Also, I think it's only a feasible system if using either a flash drive on USB 3.0 or a hard drive on either 2.0 or 3.0.  That is, I was able to install to a 2.0 flash drive, but the performance was unacceptably slow.

Have seen many proposed solutions to this issue.  This one is by far the simplest.

---


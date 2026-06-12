---
title: "Unable to install Ubuntu to USB via Unetbootin"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by ChromaLife on 2012-10-23
Hello all! I used to have a Ubuntu partition on my laptop, but I had to delete it for storage reasons. I have a Sony Vaio VPCF1, and Ubuntu used to run perfectly on it. I'm trying to reinstall Ubuntu, but I've  tried pendrivelinux's usb installer, the one on the Ubuntu website, and Unetbootin and they all do not work, I get the error Boot Error when I try to boot from the USB. Any help would be greatly appreciated.

---

### Post by ~LoKe on 2012-10-23
It's not a problem with Ubuntu or the USB, it's in your BIOS' boot options.  Have a look here: [http://ubuntuforums.org/showthread.php?t=1949602](http://ubuntuforums.org/showthread.php?t=1949602)

---

### Post by Mark Phelps on 2012-10-23
To support ~Loke's claim ... I used pendrive Linux to create a bootable USB of Ubuntu 12.10 and then used it to do an installation.  SO, I can confirm that the universal USB installer works, as does the resulting USB stick.

Often, what you have to do is press a key like F12, and when presented with a list of boot options, choose HDD-USB (or, something like that).

If you're not being presented with those options, do you know that your PC can actually boot from USB?

---

### Post by kurt18947 on 2012-10-23
I agree with the BIOS problem.  I have a desktop with an AMD 785 chipset and Thinpad notebook.  If I use a flash drive with either factory FAT32 formatting or formatted with Gparted, the live USB will boot on the Thinkpad but not on the desktop.  If I format the flash drive in Windows then run Unetbootin, the live USB will boot fine on both machines.   I've set the boot flag after formatting with Gparted and it made no difference.  My wife has an older Gigabyte  AMD GM74(?) chipset and it boots live USBs fine.  The Gigabyte/AMD785 chipset MoBo is my only problem child.

---

### Post by ChromaLife on 2012-10-23
I have installed Ubuntu with this method before, and all I had to do was press f11 and the computer would boot from the USB, but I'll try editing the boot options when I get home. I'll post again if I have any problems.

---

### Post by ChromaLife on 2012-10-23
Okay, I changed the boot order in my bios and it still says boot error. I maybe I should try a different usb drive. I'm using a PNY if that matters.

---

### Post by ChromaLife on 2012-10-24
Here is an update. I tried the Ubuntu USB with another computer and it works just fine. I think because I had Ubuntu previously installed and I used the recovery disc to wipe the GRUB bootloader is the problem. I've been in my BIOS and changed the boot priority and everything and still no positive outcome. I check to see if there is a USB mass storage emulation type and there is none listed in my BIOS settings.

---

### Post by ChromaLife on 2012-10-25
Here is yet another update. I burned an Ubuntu disc and installed it. Problem solved.

---


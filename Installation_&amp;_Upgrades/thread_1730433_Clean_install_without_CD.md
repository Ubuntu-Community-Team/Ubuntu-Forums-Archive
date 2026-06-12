---
title: "Clean install without CD"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by mattfletcher on 2011-04-16
Hello, I want to perform a clean install on my machine - it's had loads of rubbish installed, and is a real mess.

Trouble is, while I have downloaded the ISO file, I do not have any blank CDs. Is there a way to mount the ISO and run the installer from within a running system?

Probably not, but I thought I'd ask in case I missed something.

---

### Post by coffeecat on 2011-04-16
Which version of Ubuntu are you running, and which version do you want to install? Not Feisty Fawn, I hope. That's what your personal details say. :) If 9.10 or later, with grub2, it's possible to set grub up to boot from an ISO image. See here:

[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

Since you'll be using grub from the system you are going to replace, you'd want to use that with caution. If the installer were to crash halfway through, you'd be left with an unbootable machine.

An alternative:

Does the BIOS on your machine support booting from USB and do you have a spare USB flash drive of 1GB or greater? Then you could create a live USB to install from. If you have 10.04 or 10.10 you can use Startup Disk Creator (usb-creator-gtk) in System > Administration. You need to use the 10.04 version of usb-creator-gtk to write a 10.04 ISO and the 10.10 version for 10.10. There's a bug involving syslinux that leads to an unbootable USB stick if you use 10.04 for 10.10 or vice versa.

An alternative app to create a USB stick in Ubuntu is unetbootin. It's in the repositories. Or using Windows you can use the usb-creator.exe app which is in the ISO image. See here:

[https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows](https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows)

---


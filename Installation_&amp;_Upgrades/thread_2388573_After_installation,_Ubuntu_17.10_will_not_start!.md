---
title: "After installation, Ubuntu 17.10 will not start!"
date: 2018-04-04
forum: Installation &amp; Upgrades
---

### Post by rghal on 2018-04-04
GRUB comes up with a command line.
I paste the pastebin report from boot-repair below
[http://paste.ubuntu.com/p/Gj2Hpnfj4g/](http://paste.ubuntu.com/p/Gj2Hpnfj4g/)

Boot-repair from my bootable USB stick (pendrive) does not seem to be able to do anything about this problem. (I also had huge problems finding a Win10 tool that would write an iso file to a usb stick, btw - only UltraISO worked as others could not lock the drive!)

---

### Post by yancek on 2018-04-04
What exactly is the problem?  You can't boot Ubuntu?  You can't boot windows?  You can't boot either?
Did you change the boot order in the BIOS to set sdc (447GB drive) to first boot priority?

You did a BIOS install on an EFI machine which can be seen under sdc6.  You can install Ubuntu or other Linux systems on a GPT partitioned drive with the BIOS boot partition but this won't work for windows. If you are using GPT then windows needs to be EFI.  Ubuntu is on sdc8.  Boot repair also shows Ubuntu EFI files so I suppose boot repair did that so you need to boot in EFI mode and select sdc as first in boot priority

If you are able to boot Ubuntu, you need to then open a terminal and run:

> sudo update-grub .

You have no windows entry in the grub.cfg boot menu file.

---

### Post by rghal on 2018-04-04
I couldn't boot Ubuntu as grub was going into command line. 
I could boot into Windows if I chose it in Bios boot options.
I did have both EFI and Legacy booting enabled in Bios btw
I used boot-repair to reinstall grub and this is the pastebin
[http://paste.ubuntu.com/p/XSNVvNDyTy/](http://paste.ubuntu.com/p/XSNVvNDyTy/)
I will reboot and see if that solved it.

---


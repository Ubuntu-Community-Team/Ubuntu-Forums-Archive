---
title: "installing ubuntu 14.04.1 server"
date: 2014-11-20
forum: Installation &amp; Upgrades
---

### Post by Ofloo on 2014-11-20
For some reason everytime when I install this system, .. it seems to be having problems installing the MBR is there a way I can fix this afterwards, .. or are there some things i can do during install to fix this, because this is starting to get really annoying been trying to install this crap for 3 days now, .. 

Any help or information into the right direction is really appriciated.

---

### Post by irv on 2014-11-20
I you are talking about the grub menu then run the boot repair.
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by Ofloo on 2014-11-20
[http://ask.xmodulo.com/install-grub-bootloader-master-boot-record-ubuntu-mint.html](http://ask.xmodulo.com/install-grub-bootloader-master-boot-record-ubuntu-mint.html)

after install i've tried running rescue, .. mount /dev/sda1 and /boot run the above but that doesn't work, .. what i did notice though was that it said it had grub i386, while i've installed amd64, .. is that normal?

---

### Post by irv on 2014-11-20
Are you running the server on its own box or with another OS? I don't know how to answer the question on the grub i386. Seeing the grub loads before anything else I would think it doesn't matter. But I maybe wrong.

---

### Post by oldfred on 2014-11-20
Grub's naming conventions are not so consistent with Ubuntu.
You have the i386 which really is the package grub-pc for BIOS boot.
The amd version is package grub-efi-amd64 for UEFI boot with 64 bit systems.

---


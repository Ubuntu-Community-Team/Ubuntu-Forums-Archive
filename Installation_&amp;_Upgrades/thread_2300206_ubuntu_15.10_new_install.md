---
title: "ubuntu 15.10 new install"
date: 2015-10-24
forum: Installation &amp; Upgrades
---

### Post by ronb19495 on 2015-10-24
Just installed ubuntu 15.10 in uefi mode no prblems noted so far its looking great

---

### Post by monkeybrain20122 on 2015-10-24
But live usb doesn't even boot in bios. [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1499746](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1499746)

---

### Post by ronb19495 on 2015-10-24
It does for me mate I used unetbootin to install my downloaded iso
what I should have said was I used unetbootin to load the usb stick with the iso I downloaded fron the ubuntu web site

---

### Post by sudodus on 2015-10-24
> **monkeybrain20122 said:**
> But live usb doesn't even boot in bios. [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1499746](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1499746)

This bug affects the Ubuntu Startup Disk Creator, SDC. But several other tools to create a live or persistent live USB drive are ***not*** affected by the bug. For example [mkusb](https://help.ubuntu.com/community/mkusb) works well in BIOS mode as well as in UEFI mode with all current Ubuntu versions including 15.10.

See also [this link](http://ubuntuforums.org/showthread.php?t=2291946&page=3&p=13366399#post13366399), which shows what is done to improve the SDC.

---

### Post by monkeybrain20122 on 2015-10-24
> **sudodus said:**
> This bug affects the Ubuntu Startup Disk Creator, SDC. But several other tools to create a live or persistent live USB drive are ***not*** affected by the bug. For example [mkusb]("https://help.ubuntu.com/community/mkusb") works well in BIOS mode as well as in UEFI mode with all current Ubuntu versions including 15.10.

See also [this link]("http://ubuntuforums.org/showthread.php?t=2291946&page=3&p=13366399#post13366399"), which shows what is done to improve the SDC.

I see. I tried with multisystem, didn't work either (can't even make the usb)

---

### Post by ronb19495 on 2015-10-25
well as it tuned out my ubuntu tuned a little sour on me,after a  few reboots ubuntu started to lag at reboot bcame rather slow to boot,my setup was sda fedora22,sdb ntfs storage,sdc sabayon linux,sdd ubuntu 15.19,I noiced ubuntu lagging worse on every boot.So to the fix remove ubuntu amd fedora reinstall ubuntu to sda and fedora to sdd and use btrfs file system for fedora it was previously lvm,I think there wsa a conflict with lvm and ubuntu.its all good now 
file system now, ubuntu efi ext4
sabayon lvm
fedora btrfs

---

### Post by Bucky Ball on 2015-10-25
All working now? If so, please see the first link in my signature. Good luck. :)

---


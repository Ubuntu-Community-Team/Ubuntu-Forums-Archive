---
title: "Fresh Install loads to command prompt with error"
date: 2020-08-02
forum: Installation &amp; Upgrades
---

### Post by reylas812 on 2020-08-02
Put a blank HDD in laptop formatted to Fat32
USB thumb drive with install files copied on to it
loads to grub_(can't remember the rest) and no command entered will have any effect...

---

### Post by ubfan1 on 2020-08-02
FAT32 is not a suitable filesystem for installation of Ubuntu. Use ext4 unless you have a specific reason to use something else.
Copying files onto a USB to create an installation media is not what I'd do.  You use a program like rufus or mkusb to burn the media.
Take a look at:
[https://ubuntu.com/tutorials?topic=desktop](https://ubuntu.com/tutorials?topic=desktop)
[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---


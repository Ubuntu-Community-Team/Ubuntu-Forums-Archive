---
title: "Ubuntu 17.10 problem with filesystem.squashfs"
date: 2017-11-12
forum: Installation &amp; Upgrades
---

### Post by DieFohlen on 2017-11-12
Hello,


For a long time I tried to install on my laptop to install on it new Ubuntu 17.10 (so far I have Ubuntu 17.04). I have trouble loading ISO into a USB stick. Every time I load ISO on a pendrive (I tested 5 and bought 6 new!) Pops up the message:


(initramfs) mount: mounting / dev / loop0 on //filesystem.squashfs failed: Invalid argument
Can not mount / dev / loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs


Interestingly, I tested the pendrive on another computer and it works. And on my laptop (Kiano Slimnote 14.1) pops up error ... so far every linux I installed was no problem ...


My laptop has UEFI. I have disabled the secure boot.


I installed ISO using Unetbooin and Rufus (on windows). I tried other Linux installs but all the time the same error. Can anyone help?


Regards

---

### Post by terrykscott57 on 2017-11-12
You say your laptop has UEFI
Are the pendrives you are trying to install from UEFI?
I needed to create a UEFI FAT partition on my SD card, unpacked the ISO to it using startup disk creator then booted to the UEFI on my bios rather than the device direct.
Just a thought

---

### Post by dino99 on 2017-11-12
i have had too much bad experience some times ago with unetbootin, so i've made an other choice: liveusb.info and installing from netboot mini iso
[https://www.pendrivelinux.com/liveusb-install-live-usb-creator/](https://www.pendrivelinux.com/liveusb-install-live-usb-creator/)

---

### Post by jeremy31 on 2017-11-12
Moved to installations & Upgrades as 17.10 has been released

---

### Post by DieFohlen on 2017-11-12
Yes, I know that I can update, but I want to do disk format and install clean linux, but it is still error, no matter what Linux I install. Always the same mistake.


Interesting that pendrives work on other laptops. Only on my laptop is the error. Maybe something with GRUB?

---


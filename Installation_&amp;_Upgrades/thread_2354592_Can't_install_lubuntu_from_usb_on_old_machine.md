---
title: "Can't install lubuntu from usb on old machine"
date: 2017-03-04
forum: Installation &amp; Upgrades
---

### Post by daniel.nistreanu on 2017-03-04
Hello, I have a** laptop model fujitsu amilo li 1718** and laptop **can't detect **my bootable** usb **flash drive in bios. I tried another thing, I took hard drive from fujitsu and put into **other laptop** (Asus x552LD), after putting all from Bios -> Boot menu options on enabled(a few of them are no present in fujitsu Bios), I managed to boot from usb successfully but during** installation** "grub-pc" or "grub2" package **will fail** and all I can do is to force power shutdown my laptop.

My goal is to install Lubunu on fujitsu laptop, **please help**, tell me what to do ! Thanks in advance! :)

---

### Post by slickymaster on 2017-03-04
*Thread moved to **Installation & Upgrades**.*

---

### Post by yancek on 2017-03-04
When you attach the fujitsu drive to the Asus laptop, do you have another drive in the Asus?  Is there a current operating system on the other drive if you have one?  If so, what is it?  How old is the fujitsu?  If it is an older machine, it may not be capable of booting from a usb.  On the Asus, which Installation Type option are you selecting and where are you trying to install Grub and is it an EFI or MBR machine?

---

### Post by RoundTuit on 2017-04-25
If you have a CD or a floppy that your BIOS will let you boot from look for PLOP Boot Manager ( [https://www.plop.at/en/bootmanager/download.html](https://www.plop.at/en/bootmanager/download.html)). It will allow you to select USB to boot from. When I used it on an old Dell Inspiron 3800 the boot from USB would hang if the USB was plugged in when I booted. Leave it unplugged and select USB. Wait for it to fail saying no device, plug in the USB and hit ENTER then select USB again.

---


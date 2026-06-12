---
title: "Live USB Stick 10.10"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by jessemck on 2011-04-17
I am trying to make a Live USB Stick to use to test out Ubuntu 10.10

I normally just download the ISO and use UNetbootin to create a bootable live thumb drive. But I can not get it to work with 10.10 

It appears to complete and I can boot but that it, I get thrown to a BusyBox shell. I know the download is good as I have used the same ISO to create VM in Virtualbox.

---

### Post by kourasmenos on 2011-04-17
1. Use del to enter bios and from the boot tab change the boot device to USB Flash (instead of your hard drive)
2. In the same  tab go Boot Device Priority and NOW set the USB Flash Drive 1rst.

PS: You need to connect the usb flash drive before getting into BIOS and do those steps.

---

### Post by jessemck on 2011-04-17
Getting the Laptop to see and bring up the USB drive is not the problem. It's almost like files are missing that allow the USB thumb drive to boot. 

As I said I get thrown into a BusyBob prompt 

When I burn to a DVD it boots the CD kine and I get the correct Kubuntu/Ubuntu start menu to select the boot options. From the USB I get none of those options.

---

### Post by kourasmenos on 2011-04-18
Can't you "see" the USB at all during booting?

---


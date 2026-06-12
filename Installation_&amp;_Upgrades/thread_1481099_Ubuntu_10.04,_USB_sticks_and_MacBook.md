---
title: "Ubuntu 10.04, USB sticks and MacBook"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by 3fps on 2010-05-12
I've got a MacBook 2.1 without a working internal harddrive. My goal is to run a ubuntu livecd from USB. However, as you may know, this is not easily done as the mac bios does not support booting from usb.

I've screwed around a lot with rEFIt on a small HFS+ partition on the beginning of the USB drive, but I have not managed to chainload linux. My next step was to do something similar to this

[http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/](http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/)

My question is, how is this done in ubuntu 10.04? Grub seems to be totally redesigned...

Thanks

---

### Post by dino99 on 2010-05-12
look at the link below for more info about grub2

---

### Post by 3fps on 2010-05-12
Thanks for your replay, I must though admit that the information availible from that post is a little above my level. My question was more like; is there a guide for the same purpose (boot cd to usb)?

If not, can I download old grub somewhere and use stage2_eltorito and menu.lst to follow the guide for 9.10 i linked to?

---

### Post by scottbuntin on 2010-05-13
Intel Macs, including the Macbook, can boot to USB.

10.04 includes a utility for creating a 'live USB' stick. See [http://www.jonathanmoeller.com/screed/?p=1645](http://www.jonathanmoeller.com/screed/?p=1645) for details.

In essence, you boot to liveCD, and run the "Create a USB Startup Disk" utility.

---


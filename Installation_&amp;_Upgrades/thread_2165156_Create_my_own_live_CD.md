---
title: "Create my own live CD"
date: 2013-08-03
forum: Installation &amp; Upgrades
---

### Post by AWB70UK on 2013-08-03
Is it possible to create a livecd with the nouveau driver disabled and the nvidia current driver installed? Would like to have a livecd when re-installing this week just because the interface is easier.  When I try and boot into livecd it doesn’t get along with my 6800gt nvidia card. I originally installed using the alternative cd.

---

### Post by sudodus on 2013-08-03
Welcome to the Ubuntu Forums,

Yes :-)

There are two easy alternatives.

1. A persistent live system, typically a USB pendrive with a casper-rw file or partition, that can save your files including installed packages. Such a system can have all kinds of installed packages except kernel packages, so you cannot upgrade the kernel, but it should work with a proprietary graphics driver.

Use unetbootin or usb-creator-gtk (might be slightly buggy) or usb-creator-kde (stable) to create a persistent USB pendrive.

2. An installed system of Ubuntu (and the flavours Lubuntu, Xubuntu, Kubuntu ...) is portable. It can be installed to any USB device, an HDD or pendrive or even a second internal HDD or SSD or flash card. Drivers for hardware are selected at boot time, and if you do not install any proprietary driver it will be very portable. In your case you want it to be 'portable among computers with nvidia graphics'. So an installed system with a proprietary nvidia graphics driver installed can also be used.

Example: I have an external SSD in an eSATA box for my operating system. It has a proprietary nvidia graphics driver installed and I can move it between two computers with nvidia graphics chips and run it. One computer is an HP xw8400 workstation with Xeon processors and the other one is a 'cube' with an Asus motherboard and an AMD Athlon dual core processor.

But I think is is harder to make a live CD like that because its file system is read-only.

If your computer is old, has USB, but cannot boot from it, you might be able to use a Plop CD to boot and install drivers, that will make it possible to continue booting from the USB drive. See this link

[http://www.plop.at/en/bootmanagers.html](http://www.plop.at/en/bootmanagers.html)

---

### Post by AWB70UK on 2013-08-03
Thanks, do I need to create the usb stick with another pc with an nvidia driver?  I'm trying to create a 12.04 livecd. I also have a netbook and work computer with 12.04 installed but both these have ati cards.  I have created a working usb stick with permanent file but on my nvidia gcard machine this gets stuck trying nouveau channels or words to that effect.

---

### Post by sudodus on 2013-08-06
I think it is possible to run in text mode and install the nvidia drive in any computer, for example the one with an nvidia card. One way to run in text mode is to boot with the boot option ***text***. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---


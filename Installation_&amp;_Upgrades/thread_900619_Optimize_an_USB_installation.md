---
title: "Optimize an USB installation"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by xemin on 2008-08-25
Currently I'm using ubuntu installed on 4Gb USB memory stick. Not like live USB, it's really installed. I'm wondering if I use tmpfs instead of the sticks' /tmp folder if it will be faster. And the more important if it will prolong the USB sticks' live.

Is there another way to prolong the sticks' live. I've read about the tmpfs at an article but it was just mentioned - no instructions how to make it tmpfs?

Is there another ways to make Ubuntu work faster?

,
p.s. Never seen such an operating system, it's wonderful (I've just had my first Ubuntu installation).

---

### Post by MattBD on 2008-08-25
Many Linux distros offer a "boot to ram" feature which copies the whole system into RAM. This takes longer to boot, but results in a *really* fast system. Unfortunately Ubuntu doesn't generally offer this.
That said, I just Googled it and found a couple of articles you might find handy:
[http://www.pendrivelinux.com/2007/10/15/ubuntu-toram-how-to-make-ubuntu-boot-to-ram/](http://www.pendrivelinux.com/2007/10/15/ubuntu-toram-how-to-make-ubuntu-boot-to-ram/)
and:
[https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)
As for extending the life of your flash drive, I've always heard that if you want to do that you should use a non-journalling filesystem such as Ext2, instead of Ext3 as that will cut down on the number of times your computer writes to the flash drive. Longer term, [LogFS]("http://logfs.org/logfs/") will no doubt offer a better solution for installing Linux on a flash drive, but that's for the future.

---

### Post by xemin on 2008-08-26
Thanks for the quick reply MattBD.
So about the booting to RAM. It is very good idea. But if you want to get your life CD loaded to it. What I need is to speedup my current installation. It is not live CD, or live USB but a real installation on 4G usb stick. However I think I could make the system boot to ram but since it is not the well compressed live cd it will take much more space in RAM (1.9G in my case). The other drawback is that anything I do in every session will be lost when I reboot or shut down the system.

What I intend doing is change the file system to ext2, and buy some ram. Currently I'm with 1G. Maybe to make /tmp folder tmpfs. Anybody knows if there are any drawbacks?

---


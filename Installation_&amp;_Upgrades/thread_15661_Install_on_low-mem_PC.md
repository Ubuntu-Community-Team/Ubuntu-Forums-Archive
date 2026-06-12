---
title: "Install on low-mem PC"
date: 2005-02-15
forum: Installation &amp; Upgrades
---

### Post by makobcn on 2005-02-15
Hi! Here is my problem... common with other linux distros. I have a toshiba laptop @ 166 Mhz and 32Mb RAM. After selecting the language and detecting hardware, when the installer is copying install files onto the hard drive (I think), it shows me a message saying I have low memory, and it restarts, and never finishes.
I have the disk partitioned as well, with one windows partition, a swap partition, and an ext2 partition. I would like to know how to set up the swap partition, located at /dev/hda5 (in a normal linux system), but when I try to mount it, it says the file doesn't exist.

Thanks

---

### Post by illek on 2005-02-16
You probably won't be able to run Ubuntu on that machine because the x-server needs at least 64MB of ram to run.  However, you could install a command line only version of linux (like pure Debian on which Ubuntu is based).

---

### Post by az on 2005-02-16
You are running from a ramdisk, so the device names are different, I think.

You would be able to run X, it would just be uncomfortable and jittery.

I had the same problem with low memory installation on a similar laptop.  I do not know it this is a bug in the Warty installer, since it should be able to install in low memory mode.

Either try the Hoary installer or try installing debian Woody.  You can then dist-upgrade from Woody to Warty.  The debian Woody installer is not that bad.  You just would have to know (or find out) what modules you need and load them yourself with modconf.

Insofar as debian being text mode, you also can install ubuntu in text mode only.  It is called custom.

---

### Post by iminj on 2005-02-18
Look at this:

[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://) 

-iminj

---


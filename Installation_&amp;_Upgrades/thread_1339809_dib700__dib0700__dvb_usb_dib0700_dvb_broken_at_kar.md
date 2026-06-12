---
title: "dib700 / dib0700 / dvb_usb_dib0700 dvb broken at karmic (ubuntu 9.10) upgrade"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by suntinel on 2009-11-27
Hi,

I have a Gigabye U8000-RH DVB-T Adapter(dib0700 chipset) It worked fine with Jaunty Jackalope (Ubuntu 9.04) and manual compiling of v4l-dvb . After the upgrade to Karmic Kola (Ubuntu 9.10) it refuses to work.

"dmesg | grep -i dvb" gives the following output:

[    9.604166] dvb-usb: found a 'Gigabyte U8000-RH' in warm state.
[    9.604229] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    9.607899] DVB: registering new adapter (Gigabyte U8000-RH)
[    9.868841] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[    9.997695] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.4/input/input6
[    9.997748] dvb-usb: schedule remote query interval to 50 msecs.
[    9.997753] dvb-usb: Gigabyte U8000-RH successfully initialized and connected.
[    9.997911] usbcore: registered new interface driver dvb_usb_dib0700

Everythings seems okay, adapter is in warm state and was found. But if i try to scan some television channels with me-tv (i've used the programm in jaunty) it freezes it and it is just stuck at 0%. The same in kaffeine. I've found some hints that the driver is broken.

My question is: Is this bug fixed in the meantime in karmic? Does someoney have a solution, patch or other smart workaround for this problem? Or maybe just waiting, that this bug is officialy patched from the ubuntu team in the next future?

I am missing watching TV :)

Thanks a lot !

---

### Post by aresthedog on 2009-12-07
I have the same problem :(

---

### Post by suntinel on 2010-02-08
Hi,

I've found a solution.

Installing the lucid kernel on karmic works wonder :)

My Gigabyte-U8000 is working out-of-the-box with karmic and lucid kernel with Me TV.

Installation of lucid kernel under karmic:
[http://ubuntuforums.org/showthread.php?t=1346216](http://ubuntuforums.org/showthread.php?t=1346216)

Thanks to aschalk:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429662](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429662)

---


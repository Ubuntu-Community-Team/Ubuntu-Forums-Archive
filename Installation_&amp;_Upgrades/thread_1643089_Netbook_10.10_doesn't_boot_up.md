---
title: "Netbook 10.10 doesn't boot up"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by illingd on 2010-12-11
I just downloaded Ubuntu Netbook 10.10 and created a boot usb stick.

My netbook runs ok from the stick (i.e. "Live CD" mode) and all seemed OK, so I went for an installation.

The install process appeared to complete ok, but when I restart the machine without the usb stick nothing happens -  after inputting my power-on password, nothing at all: no disk activity or anything, just blank screen.

The netbook is an Acer Aspire One, the solid-state disk version, no hard-disk (110Ab ZG5)

I previously had the EasyPeasy implementation of Ubuntu NBR 10.04 running without problem (and NBR Karmic before that)

How do I begin to trouble-shoot this?

---

### Post by illingd on 2010-12-11
Problem solved!

I tried re-installing after removing the additional SD card that I have as storage expansion (/dev/mmcblk0), and hey presto! it works.

I conclude that the install process must've installed the grub boot stuff on that disk instead of the main SSD. (And yes, I definitely did the original installation to the /dev/sda1 partition and not to the expansion disk - my data is still intact on that disk.)

---

### Post by Quackers on 2010-12-11
Yes, I think that has happened with cards plugged in before.

---

### Post by fonsi2099 on 2011-03-13
Thanks this worked for me:
Problem solved! 
I tried re-installing after removing the additional SD card that I have as storage expansion (/dev/mmcblk0), and hey presto! it works.
I conclude that the install process must've installed the grub boot stuff on that disk instead of the main SSD. (And yes, I definitely did the original installation to the /dev/sda1 partition and not to the expansion disk - my data is still intact on that disk.)
):P

---


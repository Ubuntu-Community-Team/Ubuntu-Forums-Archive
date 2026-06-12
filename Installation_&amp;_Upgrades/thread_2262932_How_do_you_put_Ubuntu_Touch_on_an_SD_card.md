---
title: "How do you put Ubuntu Touch on an SD card?"
date: 2015-01-28
forum: Installation &amp; Upgrades
---

### Post by Terminal_Bane on 2015-01-28
I'm trying to run Ubuntu touch on a Raspberry Pi, but I can't find the working iso.  Where can I find the version I can boot from an SD card?

---

### Post by MAFoElffen on 2015-01-28
This is the how-to article that most Raspberry PI cummunities see to link to:
[http://www.engineersgarage.com/embedded/raspberry-pi/how-to-load-ubuntu-on-raspberry-pi](http://www.engineersgarage.com/embedded/raspberry-pi/how-to-load-ubuntu-on-raspberry-pi)

Go to the "Description" tab read the article. Has the instructions and links to the files they used.

When you feel your questions have been answered, please remember to mark this thread as solved.

---

### Post by Terminal_Bane on 2015-01-28
I'm trying to use Ubuntu Touch.  Is it available?

---

### Post by QIII on 2015-01-28
Currently, Ubuntu supports ARMv7 onwards and will not work on the Pi's ARMv6 architecure.

Even Bodhi Linux, based on Ubuntu, based their Pi OS on Debian.

The short answer:  Ubuntu won't work on the Pi.

---

### Post by MAFoElffen on 2015-01-28
+1.

I followed the links to the download images in that article... and followed it to the Raspberry download site. I got the archive they said they used.. and inside that archive was Debian Wheezy // Not Ubuntu Touch (even though that is what they called it in their article!) They did have more images there, but none were Ubuntu Touch.

---

### Post by M4LFUNCT10N on 2015-06-06
> **QIII said:**
> Currently, Ubuntu supports ARMv7 onwards and will not work on the Pi's ARMv6 architecure.

Even Bodhi Linux, based on Ubuntu, based their Pi OS on Debian.

The short answer:  Ubuntu won't work on the Pi.

Any updates?  The Raspberry Pi 2 Model B uses an ARMv7 quadcore chip.  It seems everything for Ubuntu Touch is aimed at devices currently running Android.

---


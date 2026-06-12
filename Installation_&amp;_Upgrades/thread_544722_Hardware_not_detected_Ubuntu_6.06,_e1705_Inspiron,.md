---
title: "Hardware not detected: Ubuntu 6.06, e1705 Inspiron, Broadcom 1390 Wireless:"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by slackzer on 2007-09-06
Hardware:

Dell Inspiron e1705 (also referred to as 9400)

Running ATI x1400 video card.
Running Broadcom 1390 Wireless.

When trying to install Ubuntu 7.04, I get bcxx firmware errors. The live-cd won't even boot up, it simply errors out with those firmware errors. (want more details, I can provide.)

I can however install 6.06. Takes some work, but I can get my ATI card running. At least, I can get it to the point where I can increase my resolution to the max supported by my monitor, but I'm not certain if the hardware is being fully setup and configured. Is there a way to test this?

My main problem: My wireless card is NOT detected. (It does work.)

I have tried the native driver, but I get the following error when trying to extract the firmware (both bcmwl5 and bcmwl6): Sorry, the input file is either wrong or not supported by fwcutter. I can't find the MD5sum md5hash is here.

I have tried ndiswrapper, but in an ndiswrapper -l, the driver shows up as installed, but the hardware is not showing as present. I can follow ndiswrapper tutorial after tutorial and never receive a single error message.

In device manager, it does show up as an unknown device with product id 0x4311, which is the product id for the 1390 cards.

Any ideas?

Thanks.

(Yes, I can supply more information if it's requested or needed)

---

### Post by Pumalite on 2007-09-06
You have a big problem of a video card (search the forum). You can try the Alternate CD and at the end reconfigure xserver-xorg, but I'm not sure thats the solution. Better do a BIG search in the forum for your card.
Also, during installation is best to be connected ideally to a router that provides DHCP, and you configure your wireless later.

[http://ubuntuforums.org/showthread.php?t=297092&highlight=e1705+Inspiron](http://ubuntuforums.org/showthread.php?t=297092&highlight=e1705+Inspiron)

---

### Post by slackzer on 2007-09-06
I've followed that How-To thrice, and several like it too. 

At Step 4, when you do a ndiswrapper -l, and it says you should see hardware detected and driver present, I only get driver installed. No mention of my hardware.

Also, the command that shows detected Broadcom devices, my wireless does show up, but it's missing a bunch of information that other people typically see.

As for 7.04, I've tried both the Live CD and the Alternate Install CD. Trying to boot into the Live CD results in seeing the exact same problems as rebooting after a successful Alternate CD Installation.

Also, I either bypass network setup (if I don't have a hardwire) or I do network setup (only if I have a hardwire).

---

### Post by Pumalite on 2007-09-06
Have you looked at this thread: [http://ubuntuforums.org/showthread.php?t=221320&highlight=ATI+x1400](http://ubuntuforums.org/showthread.php?t=221320&highlight=ATI+x1400)

Also; have you tried Gutsy ( if you don't make a living out of your OS)?

---


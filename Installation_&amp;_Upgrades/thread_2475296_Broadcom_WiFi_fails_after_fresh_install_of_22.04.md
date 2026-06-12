---
title: "Broadcom WiFi fails after fresh install of 22.04"
date: 2022-05-21
forum: Installation &amp; Upgrades
---

### Post by SimonHGR on 2022-05-21
Hi all, my laptop has one of those broadcom wifi cards which in previous LTS releases have always been a manual post-installation fix. That said, it has always worked following that fix. Well, today I just put a new SSD in my laptop (to preserve my existing installation!), and ran the installation for 22.04. During the installation process the broadcom card worked out of the box. However, when I boot the new installation, it's not working. If I go to the "extra/proprietary drivers" panel in the software config tool (sorry, I'm not accurately remembering the names/labels, but I hope folks know what I'm talking about) the bcm?? thing is listed, but marked as not in use. If I select to use it, I get an odd error message about "expected two strings" in syslog, but the apply changes button is not enabled.

Does this have a quick/easy fix? Should I try to install over again? What logfiles should I search, and for what information, to try to get more information?

-----------------------
Well, I tried the installation a second time, and the device was not offered at all that time. However, it still could be added from the proprietary drivers element, and still didn't work from there.
I tried a third installation, and this time simply did the manual install as I've done in the past (see here: [https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers]("https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers") ) and it works just fine now.

I have no clue how it managed to get it running successfully in the installer the first time, but that sure as heck threw me. The only differences that I can see between the first and third installation are 1) that the first was done from a DVD (don't waste your time, that takes forever, I bought a USB stick before I bothered to do it again and the install went from perhaps 40 minutes down to maybe 5) and 2) that during the first install, when it was running in the "live disk" mode, I plugged one of my USB wifi adapters in and out a couple of times (it took many minutes to respond when I did), and somewhere during that, I noticed that, in this release, wifi has to be turned on in the menu before you even see the empty pizza slice wifi icon.

No idea what else might have happened, but if anyone else has trouble, just follow the instructions (including purging the stuff that's already installed for this device, as the linked page above suggests).

---


---
title: "Error with booting Ubuntu-Mate"
date: 2018-03-02
forum: Installation &amp; Upgrades
---

### Post by robinbux on 2018-03-02
Hi, I try to install Ubuntu-Mate on my Raspberry Pi 3. 
I downloaded the image and placed it on the SD card, but when I tried to boot it, I get the error ```
Failed to start load kernel modules
```.

So what I basically tried after some research, was commenting out lines in "cups-filters.conf", with "sudo nano/etc/modules-load.d/cups-filters.conf", but even though I'm in the root, I have no writing permissions. So after that I also tried "chmod u+w /etc/modules-load.d/cups-filters.conf", but I still have no writing access.

I'd really appreciate any help.

---


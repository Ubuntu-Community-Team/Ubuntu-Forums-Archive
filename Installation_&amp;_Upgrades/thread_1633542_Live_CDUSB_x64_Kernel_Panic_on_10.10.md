---
title: "Live CD/USB x64 Kernel Panic on 10.10"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by Craigacp on 2010-11-29
I'm currently running a 10.04 x64 (amd64) install which I upgraded from 9.10. I thought I'd try a fresh install of 10.10 as the upgrade process took 6 hours last time, and my computer could do with a clean up anyhow.

I downloaded the x64 version of 10.10, checked the md5sum, and put it onto both a usb pendrive and a CD. Neither of these boot on my machine, they both lockup with a kernel panic when trying any of the options (Try Ubuntu/Install/Check CD). If I set GRUB to bootup without "quiet" and "splash" then I get a stream of text which loops and cannot be stopped which contains a message about my motherboard type and many other things which scroll too fast to be seen (or captured by my phone camera).

Oddly the i386 10.10 live CD boots perfectly fine.

My computer has no issue with running the 10.04 x64 distro, but I haven't tried booting from a 10.04 live USB.

My computer is:
Intel Core 2 Duo E8500 - 3.16GHz
4GB DDR2
ASRock ConRoe 1333 DVI\H ([http://www.asrock.com/mb/overview.asp?Model=ConRoe1333-DVI/H%20R2.0](http://www.asrock.com/mb/overview.asp?Model=ConRoe1333-DVI/H%20R2.0))
250GB HDD

Due to the limitations of my motherboard it reports the 4GB of RAM as 3.3GB, which I think might be related to the issue, but as my computer works fine with 10.04 I'm not sure how.

Does anyone know what could cause this problem? Or even how I could diagnose it further given the live CD doesn't even get to a terminal?

---


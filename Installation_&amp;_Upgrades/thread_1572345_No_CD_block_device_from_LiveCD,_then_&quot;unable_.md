---
title: "No CD block device from LiveCD, then &quot;unable to find a medium containing a live file&quot;"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by mlreta on 2010-09-10
Friends:

I'm trying to install 10.4 32 bit Ubuntu on an IBM i Series notebook (model 1161-21X). It's a Celeron powered unit with RAM expanded to 512MB. It has a 10GB HDD, and an internal CD-ROM drive. Although it has two USB ports (1.1), it cannot boot from a USB drive, so no pendrive nor external CD unit solution possible.

When I boot from LiveCD, it stops at initramfs with the "unable to find a medium containing a live file" message. Looking at dmesg, there's no CD-ROM driver loaded. Also, there's a char device for sg0, but no block device for it, so no way to mount it. It seems that the driver module has been removed from the kernel. I'm currently running Fedora Core 5 in it. This very same problem happens with any Ubuntu newer that 6 or any Fedora post 7.

Is there any way to get the CD-ROM to work with the LiveCD? Am I stuck with FC5?

Thanks in advance,

Mariano López Reta
Buenos Aires, Argentina

---


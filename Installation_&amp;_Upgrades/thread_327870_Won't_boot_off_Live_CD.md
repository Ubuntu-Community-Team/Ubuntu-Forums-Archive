---
title: "Won't boot off Live CD"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by kaz_ on 2006-12-29
I recently purchased Ubuntu Linux Bible book that comes with a live CD with the option to install. I have already installed it on one PC with no problems. Today I tried to boot off the Live CD on my Dell Dimension 3000 Desktop PC (Pentium 4). It came up with the boot screen with the options: Start and Install Ubuntu, Check Disk for Errors, Memory Check, etc. (those aren't the exact words used). When I select 'Start and Install Ubuntu' it loads the kernel fine, but then it displays a black screen with a cursor in the upper left hand corner. I have tried it several times and it continues to happen. I even walked away and watch a movie for a couple hours, but it never continued. I have also tried it with the following boot options:

aic7xxx.aic7xxx=no_probe
hw-detect/start_pcmcia=false
debian-installer/probe/usb=false

I used to those to make sure it wasn't getting hung up on trying to load the drives that I don't use. Note: my keyboard and mouse are both PS/2, so they don't use the USB controller.

Additional Information:
Linux version: Ubuntu (Edgy Eft)
RAM: 512 MB
Processor: Pentium 2 (2.80 GHz)


Thanks for your time.
- Kaz

UPDATE: Memory check passed. Ubuntu would also hang in the same fashion as above when trying to  boot in safe-graphics mode and when trying to check CD for defects. Hmm....

---

### Post by teaker1s on 2006-12-30
unless anyone comes up with a better solution I have found that the live cd doesn't have the same range of packages and only works on some hardware. The way I resolved it was to download and burn the suitable alternate iso from [here]("http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download")

---


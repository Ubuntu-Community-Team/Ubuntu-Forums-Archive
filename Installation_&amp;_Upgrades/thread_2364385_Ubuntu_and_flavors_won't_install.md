---
title: "Ubuntu and flavors won't install"
date: 2017-06-22
forum: Installation &amp; Upgrades
---

### Post by salle22 on 2017-06-22
Hello, everyone. Recently, I decided to make my Windows 10 desktop computer dual boot Ubuntu or one of its flavors. I've used bootable flash drive utilities in the past to make a bootable flash drive that can install Ubuntu. However, recent attempts to install Ubuntu have ended in one of three outcomes after selecting either start or install Ubuntu. (It should be noted that I was trying to install the latest version of Ubuntu, which is 17.04.)

a). The blinking command cursor shows up, then a series of about 10 horizontal static-like lines appear and it freezes there.
b). A series of errors with the word "nouveau" appears and hangs there.
c). The computer doesn't output any video signal and the monitor goes to sleep.

I tried to use an earlier version of Ubuntu and it still didn't work. I've tried 3 different utilities: Rufus, UNetootin, and Universal USB Installer. I even tried Manjaro and it still gave me the same problems (It did give me the colorful boot screen when choosing to install or start though.). However, when I tried Linux Mint, it was able to install, run, and boot up fine alongside Windows 10. I should mention that I have been downloading the ISOs as torrents rather than the direct ISOs. Linux Mint was also downloaded from a torrent. I tried a different flash drive (a micro SD card in a USB adapter) and no change whatsoever. I also used Windows' built-in bootable DVD maker to burn the ISO data to a DVD with the same results.

My specs:

AMD FX-8320
EVGA GTX 970
ASUS M5A99FX PRO R2.0
Kentek 750W PSU
8GB G.SKILL RAM

Any sort of help will be appreciated. Thank you.

---

### Post by deadflowr on 2017-06-22
Try setting the nomodeset option:
basically start the install media, and at the Try Ubuntu boot screen press F6 and toggle the nomodeset option, then press ESC to get back to the main screen.
Then try starting it up.

If that does not work, try the suggested nouveau.nomodeset=0 option.
from here:
[https://askubuntu.com/questions/747314/is-nomodeset-still-required]("https://askubuntu.com/questions/747314/is-nomodeset-still-required")

---


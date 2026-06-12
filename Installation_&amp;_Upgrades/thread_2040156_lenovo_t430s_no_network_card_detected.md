---
title: "lenovo t430s no network card detected"
date: 2012-08-10
forum: Installation &amp; Upgrades
---

### Post by rondal on 2012-08-10
I have a new Notebook T430s from lenovo and tried the following i386 installers: Desktop 12.04 and Desktop 12.10 alpha 3.

The NIC, it's a Intel 82579LM,  is not detected. I read that the driver e1000e should be choosen for this nic. But when I choose this driver from the list in the text based installer nothing happens.
Then I have downloaded the latest driver from Intel (Version e1000e-2.0.0.1.tar.gz) compiled it on my old notebook which has ubuntu 11.10 on it, copied the e1000e.ko file to a usb drive and copied it from there to /lib/modules/$(uname -r)/kernel/net with the shell provided from the text installer. After that I could choose the new driver from the list but again the NIC is not detected.

What can I do to make ubuntu detect the NIC on a t430s?

PS: Yes, lspci is listing the NIC

---


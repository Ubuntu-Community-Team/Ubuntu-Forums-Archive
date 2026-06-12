---
title: "usb boot black screen"
date: 2020-04-21
forum: Installation &amp; Upgrades
---

### Post by hanneshuber on 2020-04-21
Hi I want to make a dual boot install with a live usb. (currently there is windows 10 installed). It is possible to select booting from usb but after some time loading it only shows a black screen. I tried the boot repair and got following output:

[http://paste.ubuntu.com/p/v69wW5n95c/](http://paste.ubuntu.com/p/v69wW5n95c/)

Thanks in advance

---

### Post by CelticWarrior on 2020-04-21
Welcome and thank you for making an effort.

However, Boot Repair and its summary report is only useful for installed systems that aren't booting properly.
Posting you hardware specifications would have been better, namely the graphics card. It may need additional boot parameters in some cases but this assumes the USB is fine. The first thing to do is actually making sure the downloaded ISO is correct.

---

### Post by ajgreeny on 2020-04-21
The first thing that comes to my mind is that you may be using an nvidia graphics card, needing the "nomodeset" boot option when booting to the USB.

See [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) scrolling down to the appropriate part for nomodeset.

---

### Post by ActionParsnip on 2020-04-22
Does the system have a make and model, please?

---


---
title: "downgrade from 10.04 to 9.10"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by calvimm on 2010-07-28
hello.

i need help downgrading from 10.04 to 9.10. i've already downloaded the ISO and have made a usb using usb-creator-gtk. however, i don't know how to boot from the USB or install over 10.04.


thank you!

---

### Post by cj.surrusco on 2010-07-28
First of all, this usually isn't recommended, but if you are sure that you want to, go ahead. 

Do you plan on keeping the files and settings that you have? If so, you need to follow a procedure like [this]("http://linuxologist.com/1-general/howto-fresh-ubuntu-install-without-losing-your-current-settings/"). To boot from the USB, plug it in, and then boot into the Bios. When you are in the Bios, look around for "boot order" or "boot sequence" and when you  find it, set the USB drive to boot first. It would probably be named something like "USB Drive" or the name of the manufacturer.

---


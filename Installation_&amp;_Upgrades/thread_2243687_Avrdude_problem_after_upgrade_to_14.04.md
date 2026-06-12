---
title: "Avrdude problem after upgrade to 14.04"
date: 2014-09-10
forum: Installation &amp; Upgrades
---

### Post by radoslav2 on 2014-09-10
Hi to everyone,
Since i upgraded from 13.10 to 14.04 avrdude 6.01 gives me the folowing error in the end of programming:
Reading |                                                 | 0% 0.00smake: *** [writeflash] Floating point exception (core dumped)

So i reinstalled avrdude from synaptic, but with no luck. I've tried to buid it from source. On ./configure step it gives me folowing error:


Configuration summary:
----------------------
DO HAVE    libelf
DO HAVE    libusb
DON'T HAVE libusb_1_0
DON'T HAVE libftdi1
DO HAVE    libftdi
DON'T HAVE libhid
DO HAVE    pthread
DISABLED   doc
ENABLED    parport
DISABLED   linuxgpio

Anyway i ran  sudo apt-get build-dep avrdude and then make but the result is the same in programming. Any help is appreciated.

---


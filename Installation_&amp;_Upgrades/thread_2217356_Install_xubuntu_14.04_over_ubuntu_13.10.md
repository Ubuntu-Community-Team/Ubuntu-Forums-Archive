---
title: "Install xubuntu 14.04 over ubuntu 13.10"
date: 2014-04-16
forum: Installation &amp; Upgrades
---

### Post by andeh19 on 2014-04-16
Hi,

Currently I am dual booting Windows 8.1 with Ubuntu 13.10 (using GRUB), however I am planning to install Xubuntu 14.04 over Ubuntu 13.10 and start fresh.

Do I just select the option "something else" when I install it over USB? And reformat the existing root partition?

Thanks

---

### Post by slooksterpsv on 2014-04-16
If **don't** need any of your data. Yup you choose Something else, select your Ubuntu 13.10 drive, double click on it, set it to / and format, choose OK, select where you'd like your bootloader to go (I don't put it on /dev/sda, I put it on the drive I use for (K,Ed,X)Ubuntu where my system uses EFI (so my drive is /dev/sda6 for my Xubuntu installation).

If you need your data, back it up, then go from what I said above.

---

### Post by andeh19 on 2014-04-16
Awesome thanks!

---


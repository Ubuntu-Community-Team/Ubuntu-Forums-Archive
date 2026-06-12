---
title: "Ubuntu 12.04 installation problem on a usb disk"
date: 2012-07-12
forum: Installation &amp; Upgrades
---

### Post by Kunami75 on 2012-07-12
Hello,

I have installed Ubuntu 12.04 on a external usb drive and I have this error message when I want to boot.

[[IMG]http://free0.hiboox.com/images/2812/074a5b4a2a06d414c5cfdf0a8321d89c.jpg[/IMG]]("http://www.hiboox.fr/go/images/informatique/sans-titre,074a5b4a2a06d414c5cfdf0a8321d89c.jpg.html")


Thanks for you help

---

### Post by plucky on 2012-07-13
> **Kunami75 said:**
> Hello,

I have installed Ubuntu 12.04 on a external usb drive and I have this error message when I want to boot.

[[IMG]http://free0.hiboox.com/images/2812/074a5b4a2a06d414c5cfdf0a8321d89c.jpg[/IMG]]("http://www.hiboox.fr/go/images/informatique/sans-titre,074a5b4a2a06d414c5cfdf0a8321d89c.jpg.html")


Thanks for you help

It is trying to boot /dev/sda which is unlikely to be the external USB drive.

Have you changed the BIOS to boot the removable drive?

Is your computer capable of booting USB drives?

---

### Post by efflandt on 2012-07-15
Which drive did you put grub on and which drive are you actually booting (your internal drive or the USB drive)?

Does the external drive have regular msdos partitions, or gpt partitions (which requires doing something special).

---


---
title: "upgrade 9.10 to 10.04  alpha 3"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by joe1600 on 2010-03-01
hello

please help me out...i tried update-manager -d from GUI and asked to downlaod 678 MB...so i downlaoded the i386 iso 685 from cdimage.ubuntu.com/alpha-3..now how to upgrade to 10.04 lucid alpha  3 from 9.10....

9.10 is also i386 installation..
regards

Joe

---

### Post by darkod on 2010-03-01
Why do you want to upgrade to 10.04? It's still in development and it's not recommended to upgrade your main system to it.
If you want just to test it, either run it with the Try Ubuntu option from the cd, or install in separate partition without installing the bootloader. Then in 9.10 just run update-grub to find the new 10.04 install.
If you upgrade your main system to 10.04 even if it works at the start, it can easily break down later.

---


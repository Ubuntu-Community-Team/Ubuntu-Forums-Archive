---
title: "Screen black  with Xorg Server"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by candidoaramburu on 2010-05-20
Hi,

I have upgrade Ubuntu 9.10 to 10.4 on my Dell Inspiron Desktop and OKI TV monitor.

After reboot the new version I can read the menu.lst on the screen and i select ubuntu 10.4 but after the screen is black permanently and the boot process stop.

I have tried with a acer monitor and all is OK, but i would like use the OKI monitor.

With the OKI monitor I have not problems with old versions of Ubuntu, neither Ubuntu CD Live, neither Knoppix.

I have see that there is not  /etc/X11/xorg.conf so I have tried with differents xorg.conf files:
 a) with dpkg-reconfigure -phigh xerver-xorg
 b) copying xorg.conf from Ubuntu 8.10 Live LoW Graphics mode
 c) copying xorg.conf from Knoppix Live

but the result is the same : black screen

I have tried also Xorg -configure but it say a warning message: "Server is running"

I think that start up script dont read xorg.conf and the boot process is blocked

THANKS IN ADVANCE

---

### Post by uRock on 2010-05-20
If you have a separate /home, I'd recommend a clean install.

---

### Post by candidoaramburu on 2010-05-21
Thanks for the advice, then next one i first will probe CDlive.

I have fix the problem with a new option in the grub/menu.lst controlling the intel chipset.

i915.modeset=0

my intel chipset is G33/G31 no 915 .  I dont understand why this option work with G33


Thanks

---


---
title: "Problems Installing Kubuntu 12.04"
date: 2012-09-03
forum: Installation &amp; Upgrades
---

### Post by OGAMIITTO on 2012-09-03
Hello all,

I bought an Eee PC net-book earlier this year and I want to install Kubuntu 12.04 on it. 

When I used the Windows desktop installer, the net-book froze a third of the way through installation. I tried 5 or 6 times a day for a week but the same thing kept on happening.

So, as the net-book has no CD drive, I then downloaded the ISO and extracted it and put it on an external pen drive using the Ubuntu recommended pen drive installer.

The problem I have with that is when I access the boot up screen, there is no option to boot via USB. 

Bearing all that in mind, what is the best and easiest way for me to install Kubuntu?

Many thanks for your time

Ogami

---

### Post by SeijiSensei on 2012-09-03
When the machine boots, hit F2 to go into setup, then browse around in the BIOS until you can find the settings that let you specify the order in which devices are checked during boot.  On my 1201n, it's under the Advanced menu.  Move the entry for the "removable device" to the top of the list, then save your settings and reboot.

---


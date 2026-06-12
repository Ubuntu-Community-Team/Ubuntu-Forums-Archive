---
title: "Installation screen won't display correctly"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by franckn on 2010-11-05
Hello, I can't install either ubuntu 10.10 desktop or netbook in HP Pavilion dv6000 laptop.

This is all it displays:
[IMG]http://img801.imageshack.us/img801/6199/1001361i.jpg[/IMG]

Suggestions?

Thank you

---

### Post by dino99 on 2010-11-05
is it a fresh installation or an dist-upgrade ?

looks like the installation have some video driver issue, which is the chipset or card inside ?

[http://www.google.fr/search?as_q=dv6000%2Bmaverick&hl=fr&tbo=1&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=all&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.fr/search?as_q=dv6000%2Bmaverick&hl=fr&tbo=1&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=all&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

there is lot of posts around this laptop, try to boot with either: nomodeset, noacpi, nolapic, noapic, irqpoll ( be added to the boot line, press F6 if i remember well)

---

### Post by franckn on 2010-11-11
It is a fresh installation. I booted using nomodeset and was able to fully install. Unfortunately, after the first reboot, the desktop display was as messed up as the original installation screen (like the image I showed when describing the problem).

I was able to make it work by installing the Additional Drivers (NVIDIA accelerated graphics driver (version current)[recommended]). I did this by randomly clicking the screen until I selected the item I wanted (e.g. clicked on Additional Drivers and Activate). Then rebooted, and now it looks great.

---


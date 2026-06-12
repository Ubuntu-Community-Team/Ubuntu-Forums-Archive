---
title: "[SOLVED] Video scrambled on 8.04.1 install"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by gilman22 on 2008-08-04
I am running version 7 of Ubuntu and when I boot the 8.04.1 install the initial screen comes up with diagonal bars on the screen. When I use safe graphics mode it is totally non viewable. I loaded on another system with a different motherboard OK. I am running an MSI  Motherboard.

---

### Post by overdrank on 2008-08-04
> **gilman22 said:**
> I am running version 7 of Ubuntu and when I boot the 8.04.1 install the initial screen comes up with diagonal bars on the screen. When I use safe graphics mode it is totally non viewable. I loaded on another system with a different motherboard OK. I am running an MSI  Motherboard.

Hi and welcome, could you give us some specs on the system you are having issues with? Like graphics, memory and so on.

---

### Post by gilman22 on 2008-08-05
The Motherboard is an MSI P4M900M2-L with a VIA P4M900 Northbridge. The graphics on the Northbridge is an S3 Graphics Chrome9 HC Integrated Graphics Core. The system has 512 meg of RAM.

---

### Post by overdrank on 2008-08-05
> **gilman22 said:**
> The Motherboard is an MSI P4M900M2-L with a VIA P4M900 Northbridge. The graphics on the Northbridge is an S3 Graphics Chrome9 HC Integrated Graphics Core. The system has 512 meg of RAM.

Ok the S3 graphics can be a issue. If you are booting the live cd you can try when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add vga=771 or 775 before the -- then press enter. 
I have heard users even using 778 and this has help. The support for the S3 graphics is not good. If this is a onboard graphics then you may look at adding a graphics card.

---

### Post by gilman22 on 2008-08-05
Thanks for the help. It didn't work. Is there a way I can get 8.04.0 that seems to be working?

---

### Post by overdrank on 2008-08-05
> **gilman22 said:**
> Thanks for the help. It didn't work. Is there a way I can get 8.04.0 that seems to be working?

You may try the alternate cd for the installation as it is a text based install. So it is not the live cd but if you want to install and then try and configure the graphics afterwards.

---

### Post by gilman22 on 2008-08-05
Turns out I had to install 7.10 and then update via the Web to get it to work. Thanks for your help. :)

---


---
title: "Dual monitor with old graphic card"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by Trompette83 on 2012-02-09
Hello there,

I have an old PC Pentium 3GHz HP Motherboard (32 bits), 3 GB RAM, Graphic card ATI Radeon 9600 RV350.

With Ubuntu 9.10 Karmic Koala I can use 2 monitors VGA and DVI not mirroring without any problem.
I installed from scratch Ubuntu 11.04 Natty Narwhal in another HD and I can boot one or other by activating the right HD in the BIOS.
I do not use UNITY but classic.
I can't use ATI driver, unsupported any more.

With 11.04 I can use 2 monitors as mirror but when I change for NOT mirroring, screens are unusable. See pictures.
I did not find any thread resolving this issue for an old graphic card.
Someone could help me?

Many thanks

Edit: 2 monitors with the same resolution 1280x1024 60Hz

---

### Post by Trompette83 on 2012-02-10
Would be very happy to get some help.

---

### Post by Trompette83 on 2012-02-12
As they say here
[http://ubuntuforums.org/showthread.php?t=1748037]("http://ubuntuforums.org/showthread.php?t=1748037")
I added the /etc/X11/xorg.conf file.
Unfortunately this didn't solve the problem maybe because I don't use the ATI driver.

I tried to change the resolution on both monitors; with 800x600 and 1024x768 this is working well. With 1152x864 and 1280x1024 there is the problem. I'd guess this is a graphic memory issue with 11.04.

Anybody has this problem?

---

### Post by Trompette83 on 2012-02-13
I got it! :D

Easy;
Change to "Ubuntu classic (No effects)" with System > Administration > Login Screen Settings.

Thanks to all of you for your help ;-)

---

### Post by Cookieh on 2012-02-13
Change the thread to solved.. Thanks now I can connect 2 more to my pc..:D

---

### Post by Trompette83 on 2012-02-16
Could you explain me how to change to solved?

Thanks

---


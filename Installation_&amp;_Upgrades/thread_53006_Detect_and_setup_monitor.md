---
title: "Detect and setup monitor"
date: 2005-07-29
forum: Installation &amp; Upgrades
---

### Post by jemt on 2005-07-29
Hi Experts.

I have just successfully performed an Ubuntu Linux Minimal/Server Installation with X and Xfce4. Almost everything seems to be working fine except for my monitor. When I'm performing a normal installation, my monitor is automatically configured and I can run all available resolutions the monitor supports. Unfortunately this is not possible at the moment. This is probably because some kind of generic driver has been loader.

The question : How do I detect and setup my monitor? It's a Hitachi CM620ET and should be capable of running 1024 x 768 @ 85 Hz (75 Hz would be just fine), 32 Bit Colors.

 - Thanks :)

---

### Post by hondje on 2005-07-29
[QUOTE=jemt]Hi Experts.

I have just successfully performed an Ubuntu Linux Minimal/Server Installation with X and Xfce4. Almost everything seems to be working fine except for my monitor. When I'm performing a normal installation, my monitor is automatically configured and I can run all available resolutions the monitor supports. Unfortunately this is not possible at the moment. This is probably because some kind of generic driver has been loader.

The question : How do I detect and setup my monitor? It's a Hitachi CM620ET and should be capable of running 1024 x 768 @ 85 Hz (75 Hz would be just fine), 32 Bit Colors.

 - Thanks :)[/QUOTE]

If X is installed, you can run dpkg-reconfigure xserver-xorg.  You can also get some information from here: [https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)

---

### Post by jemt on 2005-07-29
Thanks alot - worked like a charme :-)

---


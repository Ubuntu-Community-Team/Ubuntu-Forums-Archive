---
title: "Acer one 522 boot issues"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by Mattymcg112 on 2011-04-08
Hi, my first post here. I'm having troubles installing ubuntu on my "Acer one 522" netbook, I have made a pendrive with unetbootin and ubuntu 11.04 natty and upon booting into the usb i get the boot loader displayed properly, start to load ubuntu, then about halfway through i get some screen tearing with a really small shot of the boot loader screen in the top left hand corner followed by some command lines saying "cannot mount /dev/loop0 :invalid argument". I'm a complete linux noob here so go easy on me. Thanks! and yes I have searched lol.

---

### Post by tactus on 2011-04-14
> **Mattymcg112 said:**
> Hi, my first post here. I'm having troubles installing ubuntu on my "Acer one 522" netbook, I have made a pendrive with unetbootin and ubuntu 11.04 natty and upon booting into the usb i get the boot loader displayed properly, start to load ubuntu, then about halfway through i get some screen tearing with a really small shot of the boot loader screen in the top left hand corner followed by some command lines saying "cannot mount /dev/loop0 :invalid argument". I'm a complete linux noob here so go easy on me. Thanks! and yes I have searched lol.

Try to install Ubuntu 10.10 first and then upgrade to 11.04, that worked for me.

I had problem with freezes if ethernet cable is unplugged with Aspire One 522, so I had to disable ethernet driver and only load it manually if I need cable connection. Maybe it will not affect you, I think it's related to models with Atheros AR9285 wireless card, but I don't know.

It's fairly new hardware and support is immature, but I think in future it will be very well supported out of the box on most distributions. If you don't mind waiting until Ubuntu 11.10, you should consider waiting. You can always test Linux in Virtualbox. It works well on this machine, but only with 32 bit guest OS and upgraded amount of ram.

---


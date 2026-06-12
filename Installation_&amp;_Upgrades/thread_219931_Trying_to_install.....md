---
title: "Trying to install...."
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by BigJerm on 2006-07-20
Me and a friend have been trying to install Ubuntu for the past 5 hours with little to no luck. When installing, it freezes up when loading the *Hardware drivers*, only when I am trying to use my ATI Radeon 9200 SE though. I figured out that I could easily avoid, the freezing, by turning on my integrated card through the BIOS. I can then install Ubuntu no problem. This is only a small fix, seeing as I cannot seem to get my ATI Radeon 9200 SE to work when Ubuntu is finished installing. It continually freezes at the same *Hardware drivers*sequence. I have tried different methods to loading the drivers on, and attempting to get Ubuntu to accept the card. I have used official ATI Linux drivers, I have tried following this guide [[here]("http://ubuntuforums.org/showthread.php?t=191944&highlight=ATI+Radeon")], no luck. If anyone could help me in the slightest, I would appreciate it greatly. I am extremly interesting in Linux, and Ubuntu, and I want to be able to enjoy it. Thanks.

Here's my hardware I am currently using:

Celeron D 2.93GHz
1.25GB RAM
ATI Radeon 9200 SE 128MB PCI 
160GB HDD
DVD/RW Drive

---

### Post by zhoux on 2006-07-20
you can try this command within terminal:

sudo dpkg-reconfigure xserver-xorg

you can try changing the driver for the ati card...such as "ati", "radeon", or if you have the ati driver installed "fglrx"...

---


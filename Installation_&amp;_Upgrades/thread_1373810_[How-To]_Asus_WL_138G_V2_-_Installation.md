---
title: "[How-To] Asus WL 138G V2 - Installation"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by Akavashi on 2010-01-06
Now, as most people have probably noticed that their WL 138G V2 wireless lan card installs but just doesn't quite find networks within Ubuntu. So I thought I may as well throw in the most simple and cunning solution - instead of using the silly method of installing ndiswrapper (Yes, I did it without thinking >.< ).

Just go to Administration->Hardware Drivers and click the "Broadcom B43 wireless driver" and activate it.

Restart your wonderful Ubuntu machine and voilah! You should have nice and simple wireless internet that works flawlessly with Network Manager!

This worked in Ubuntu 9.10, so hopefully anything after Hardy Heron should be the same! Note that this should work with any version of the Broadcom Wireless chipsets :P

---


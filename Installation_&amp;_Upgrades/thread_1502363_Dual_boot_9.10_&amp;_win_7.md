---
title: "Dual boot 9.10 &amp; win 7"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by ronaldbrijo on 2010-06-05
I had 2pc's one running Ubuntu 9.10 and another with win7. The ubuntu pc mobo died and now I want to dual boot my win 7 pc.

I tried using the win7 drive as primary and used Bcd, to configure the win7 bootloader to ubuntu as a boot option. BCD adds it but I cannot boot into the ubuntu drive ,gives an unable to locate neogrub? error. So now I have Ubuntu as the primary drive and would like to edit the grub loader to add win7.

How would I do this please.

Thank you

---

### Post by darkod on 2010-06-05
If this was a clean install of 9.10, that is using grub2. Just boot ubuntu and in terminal do:

sudo update-grub

---

### Post by ronaldbrijo on 2010-06-05
Thank you

Quick & easy!!

---


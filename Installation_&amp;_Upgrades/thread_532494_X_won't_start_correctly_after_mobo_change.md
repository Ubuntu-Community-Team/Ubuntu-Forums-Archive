---
title: "X won't start correctly after mobo change"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by bravemosquito on 2007-08-22
Hi, guys!

Before a week I brought a new mobo - ASRock ALiveNF7G-HDReady with integrated nVidia 7050 videocard. The mobo replaced the old one - ASRock K8NF4G-SATA2 with nVidia 6100 int. videocard.

The issue comes when I use the same hdd with Ubuntu 7.04 32bit on the new board. After bootin' the kernel (2.6.20-16) the X starts in 720x400@70Hz (monitor is Dell P1130 and he is correctly added in xorg.conf) and I saw only a black screen. Rapidly I start the recovery mode (second option for the kernel from grub-menulist) and tried to pre-install the videodriver - the current one on hdd is 97.55 - without success :( The driver preinstalls fine but there's not a sign from my standart resolution in X - 1024x768@100Hz (under Gnome btw).

Please, give me a clue how to fix this [-o<

---

### Post by Pumalite on 2007-08-22
Get in the system first: sudo dpkg-reconfigure xserver-xorg Say yes to most defaults, choose 'vesa' as your driver. Later install appropriate driver.

---

### Post by bravemosquito on 2007-08-22
Thanks. I forgot for vesa :mrgreen:

BTW I realised that nVidia 7xxx onboard cards are supported from 100.14.11. Found in download page on nVidia's website.

The problem was fixed. For now...

---

### Post by Pumalite on 2007-08-22
You are welcome.

---


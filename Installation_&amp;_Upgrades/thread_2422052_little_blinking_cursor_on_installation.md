---
title: "little blinking cursor on installation"
date: 2019-07-01
forum: Installation &amp; Upgrades
---

### Post by maurice-volaski on 2019-07-01
I'm trying to install Disco Dingo, aka 19.04 to a ASUS X399-A system running a Threadripper 2950x. The boot of the DVD gets to a point where it displays a tiny blinking white cursor at the upper left of the screen. The DVD is no longer being accessed. Any idea what might be going on?

---

### Post by CatKiller on 2019-07-01
Which GPU? If it's an nvidia one you'll probably need to use the nomodeset kernel parameter until you've got the proprietary driver installed.

---

### Post by maurice-volaski on 2019-07-01
Ah, how can I alter the kernel parameter on the boot media?

---

### Post by CatKiller on 2019-07-01
It's a while since I've done it but, from memory, where you have the "try Ubuntu without installing" option you can press e to edit the kernel line. Just add in nomodeset to where it probably says quiet splash, and then whatever button it says to carry on booting. You'll probably need to do it once more when you've installed it, this time from the Grub menu which you get by pressing Esc at boot. Once you've installed the proprietary driver you shouldn't need it any more.

---

### Post by zeroxfcpersonal on 2019-07-03
esc doesnt really work for me but do you reinstall ubuntu and then when you have the option to try or install and then press e

---


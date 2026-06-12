---
title: "Dual boot with XP"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by richard-elland on 2008-06-16
Hi
I have installed Ubuntu 7.10 on IDE with windows XP on SATA
PC just boots into XP.
Sorry - Im an absolute novice but no sign of grub and dont know how to boot into Linux from here at all.  Any help appreciated
Richard

---

### Post by Pumalite on 2008-06-16
One of the solutions is to install both OS's in the main drive (XP's) and keep the other for storage or a separate /home for Ubuntu:
[http://ubuntuforums.org/showthread.php?t=46003](http://ubuntuforums.org/showthread.php?t=46003)

[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

### Post by meierfra. on 2008-06-16
If you can, change the boot order in the bios.

---

### Post by louieb on 2008-06-16
Welcome to Ubuntu and dual booting. Two hard drives one ide - one sata = GRUB  install confusion. 
When GRUB is installed it guesses which drive boots first - sometimes like in your case it guessed wrong.

Try meierfra suggestion 1st. If that doesn't work then.

I guess you can boot windows. So for now get [Explore2fs ext3 viewer - read only]("http://www.chrysocome.net/explore2fs") and bowse your Ubuntu install. and post the content of **/boot/grub/menu.lst** and [B]/boot/grub/device.map.

[/B]Its not hard to fix unless you have never done it before and know nothing about GRUB :confused:Here's a how to by longtime Ubuntu user confused57.  [Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")

Any help I give I probably learned from that thread or the DUAL BOOT link in my signature.

---

### Post by richard-elland on 2008-06-18
All sorted out now - thanks for your help :)

---


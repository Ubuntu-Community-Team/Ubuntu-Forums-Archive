---
title: "[SOLVED] instaling on usb drive"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by liopard on 2007-06-26
I installed ubuntu 7.4 on my computer when I turned it back on and tried to log on to ubuntu 7.4 it did not find wear to boot from so it boots to win xp I installed the Win Grub but it did not Evan recognize the drive I formatted the computer agen ant going to try one's more . Is thar any thing special I mast do to mike it recognize the drive ?:):(

---

### Post by davmaz on 2007-06-27
Did you put a separate partition for /boot? I've forgotten it in the past and had problems. Also, Windows usually expects a master boot record (MBR) that it boots from. If you partition your own /boot sector you can put both Windows and Linux boot loaders in it. I'm no expert on this -- you may want to check the Linux boot HOWTO.

---


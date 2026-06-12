---
title: "gutsy hangs when booting from grub"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by piwi1999 on 2007-10-19
Hi, my ati radeon x1600 worked very good under 7.04 but when installing 7.10 from live cd (which worked well....no errors reported)....when booting from grub....my computer hangs (only black screen - not possible to use ctrl+alt+backspace)...anybody knows how to help me? thanks in advance

---

### Post by my_linux on 2007-10-19
What do you see if you press Alt - F1 during the boot process?

Have you tried editing the grub entry by placing vga=791?

---

### Post by piwi1999 on 2007-10-19
nothing changes

---

### Post by TheMarex on 2007-10-19
I too have a X1600 and I am experiencing the smale problem here. However I could work aorund it with booting without "splash", "quite" etc. parameters and installing fglrx from repository, chaning the xorg.conf and reboot. The screen still remains black while booting but after about 2 min GDM shows up and everything is fine.

---


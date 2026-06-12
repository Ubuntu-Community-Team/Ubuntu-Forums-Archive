---
title: "Is it possible to disable graphical boot screen?"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by spmurphy on 2010-06-09
64 bit 10.04

Is it possible to disable the graphical boot screen so that the boot process shows what's actually happening, like "old" linux versions used to do? (Scrolling text, "starting this... starting that..." etc.)

I still want to boot into X when it's done, just don't want the lo-res 5 dot display. I'm trying to fault find and the graphic doesn't really help.

---

### Post by oldos2er on 2010-06-09
In /etc/default/grub, change GRUB_CMDLINE_LINUX_DEFAULT=" quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="text"
Then run **sudo update-grub**
Reboot, and after you login, run **startx** to load Gnome.

---

### Post by spmurphy on 2010-06-10
Thank you :)

---

### Post by guy-rouillier on 2010-06-16
Thanks from me also.  I've been searching all over these forums trying to find this magical answer.  Works perfectly.

---

### Post by grenness on 2010-06-28
What do I have to do (sorry, I'm a bit noob) to have a text only boot sequence as the tip above fixed, but then have the server automatically start Gnome when/if everything has loaded successfully?

I.e. not having to type "startx"...

Thanks,
Christopher

---

### Post by hefko on 2010-11-07
to get it, just leave this option empty:
GRUB_CMDLINE_LINUX_DEFAULT=""
:)

---


---
title: "anyone know how to display (not hide) grub2 boot screen on startup?"
date: 2009-08-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kraymore on 2009-08-19
can anyone tell me how to display the grub2 screen instead of being forced to press escape?

i successfully added a theme easily enough but i want my menu to be displayed.

thank you

---

### Post by plun on 2009-08-19
> If you're upset by the boot menu being hidden all of a sudden, then you
should edit /etc/default/grub, comment out the GRUB_HIDDEN_TIMEOUT line,
and set GRUB_TIMEOUT to the timeout you want in seconds (say "10"), then
run 'sudo update-grub'.

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-August/000599.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-August/000599.html)


--

---


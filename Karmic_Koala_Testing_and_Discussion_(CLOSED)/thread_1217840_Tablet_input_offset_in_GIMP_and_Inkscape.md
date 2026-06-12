---
title: "Tablet input offset in GIMP and Inkscape"
date: 2009-07-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by juanchito2006 on 2009-07-20
Greetings, I've got a Genius G-Pen 4500 tablet I've been sucessfully using on Ubuntu 9.10 for a couple of months.

However, I wanted to work on some drawings today, I noticed that the input on both GIMP and Inkscape is offset; the tracing is away from the actual cursor. However, I can use my tablet without issues as a regular pointing device.

I'm not very sure what has caused this, but hope it gets fixed soon. This issue has halted my work, and maybe I'm being forced to work on Windows.

---

### Post by ScislaC on 2009-08-17
I just ran into the same issue with an Intuos 2... I'm going to search LP to see if anything is filed.

---

### Post by bear24rw on 2009-08-17
it is also offset with my toshiba tablet

---

### Post by MacUntu on 2009-08-17
[https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/410267](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/410267)

---

### Post by juanchito2006 on 2009-08-18
> **MacUntu said:**
> [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/410267](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/410267)

Thanks for the bug info, I'm glad this issue has been confirmed already.

---

### Post by Favux on 2009-09-22
Hi everyone,

Loic2 reports they fixed the bug upstream and gives links to the patches in post #314 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=32](http://ubuntuforums.org/showthread.php?t=967147&page=32)

It would be good to get the fix into Karmic.

---

### Post by juanchito2006 on 2009-09-24
Thanks, now in GTK+ 2.18 the issue seems solved.

---


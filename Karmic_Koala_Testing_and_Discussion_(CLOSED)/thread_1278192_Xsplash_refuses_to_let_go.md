---
title: "Xsplash refuses to let go"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by NCLI on 2009-09-29
Xsplash stays in front of my desktop even after logging in, totally frozen and crashed. The only way to make it go away is launch a gksudo gnome-system-monitor(if one presses alt+tab one can browse through static images of the open windows, which disappear as soon as one lets go.) The desktop is fully loaded and can be controlled using the keyboard, though the mouse/touchscreen don't work.

---

### Post by dino99 on 2009-09-29
I was having this problem, but with today's updates karmic boot properly & xsplash too.

graphic card: 8500 gt

---

### Post by NCLI on 2009-09-29
My netbook gets the updates a little later since I'm running UNR, so I guess it'll be fixed soon...

---

### Post by VMC on 2009-09-29
> **NCLI said:**
> Xsplash stays in front of my desktop even after logging in, totally frozen and crashed. The only way to make it go away is launch a gksudo gnome-system-monitor(if one presses alt+tab one can browse through static images of the open windows, which disappear as soon as one lets go.) The desktop is fully loaded and can be controlled using the keyboard, though the mouse/touchscreen don't work.

When that happened to me, I removed xsplash to see what was happening beneath it. After that it booted much quicker without any delays. I just added it back yesterday and now it works perfectly.

---

### Post by jdmpike on 2009-09-29
+1

This is also happening on my Acer AspireOne netbook. I didn't try alt+tabing or alt+f2 to run gksudo gnome-system-monitor - instead opting to drop into another vterminal, log in, and kill -9 xsplash (it was also using 100% of cpu).

Look forward to getting this gone. :)

---

### Post by vishalrao on 2009-09-30
Fixed I think: [https://launchpad.net/ubuntu/karmic/+source/xsplash/0.8.1-0ubuntu2](https://launchpad.net/ubuntu/karmic/+source/xsplash/0.8.1-0ubuntu2)

---

### Post by TunaCanTommy on 2009-09-30
I had the xsplash problem on my ASUS EeePC running Karmic (UNR).
The update fixed it for me . . .

---

### Post by hanzomon4 on 2009-09-30
This was fixed in an update this morning

---


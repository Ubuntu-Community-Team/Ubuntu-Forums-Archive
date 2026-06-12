---
title: "X doesn't start on live CD"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by Fimget on 2007-08-18
hello everybody!!
got my new laptop - HP dv9525 (with vista :blech:)
I'm trying to install kubuntu but the live CD won't open the X:
"fatal error
screen not found"
/etc/X11/xorg.conf device section doesn't look suspicious...
(this also happens with ubuntu 6.06 live CD)
Of course kubuntu must be installed and X is critical for GUI design work....

any tips?

10x.

---

### Post by jd65pl on 2007-08-18
What is the graphics card on the machine?

---

### Post by merlinus on 2007-08-18
Try Safe Video Mode or text-based Alternate Desktop install cd.

-merlin

---

### Post by Ub1476 on 2007-08-18
If you have a ATI card, the alternate CD will not help you much after you have installed Ubuntu. Follow this little guide fix your problem: [Link]("http://ubuntuforums.org/showthread.php?t=528105&page=2")

If you have a nvidia card, you're lucky and probably only have to do this (or do the alternate CD):

Boot to Live CD, choose No to view x error details, press Enter (sometimes F2) to enter the terminal. Write: sudo nano /etc/X11/xorg.conf, and scroll down to the "Device" section. Edited the driver to be called "Vesa". Like this:

Driver		"Vesa"

Hope that helps.

---

### Post by Fimget on 2007-08-19
no luck for me... :(
the card is Intel Graphics X3100 (NVidia based??- it's a laptop after all)

The best i got was to change xorg.conf (what does the "vesa" mean?)
the result was a grey screen with X for mouse - responding but no desktop...

---


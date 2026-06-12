---
title: "Libreoffice on 18.04, xfce"
date: 2018-06-05
forum: Installation &amp; Upgrades
---

### Post by mlnease on 2018-06-05
Hello,

I've just upgraded to 18.04 from 16.04 and am experiencing some unfamiliar problems with Libreoffice (Writer fails to properly resize etc.).  Anyone else?

Cheers,

mn

---

### Post by ajgreeny on 2018-06-06
No problem here but I always clean install, not upgrade.

Try renaming the ~/.config/libreoffice folder in your home after making sure LO is completely closed to see if that solves your problem.

---

### Post by mlnease on 2018-06-06
> **ajgreeny said:**
> No problem here but I always clean install, not upgrade.

Try renaming the ~/.config/libreoffice folder in your home after making sure LO is completely closed to see if that solves your problem.

Sorry, I misspoke--this is a clean install from a CD, not an upgrade.

My problem with Writer is that it opens maximized and won't unmaximize (even from the dropdown in the far upper left).  At the far upper right, there are '--', '+' and two 'x's--the '+'does nothing, the '-' minimizes and both 'x's close the file.  I've been using Writer since it was new and never had this problem before.

Calc seems OK.  Haven't tried anything else.

Thanks for your time and attention.

---

### Post by ajgreeny on 2018-06-06
It sounds as if your unmaximised window is full size even if not actually maximised.
Try a right click in the LO Writer window button in your panel which should show the options** Minimise, Unmaximise, Move and Resize**, though the latter will be greyed-out if the window is maximised.

If you don't have an active option to Resize, first click the Unmaximise option then right click again and choose Resize.
Moving the mouse will now resize the window.

---

### Post by mlnease on 2018-06-06
> **ajgreeny said:**
> It sounds as if your unmaximised window is full size even if not actually maximised.
Try a right click in the LO Writer window button in your panel which should show the options** Minimise, Unmaximise, Move and Resize**, though the latter will be greyed-out if the window is maximised.

If you don't have an active option to Resize, first click the Unmaximise option then right click again and choose Resize.
Moving the mouse will now resize the window.

The **Unmaximize** option in the active LO Window Button has no effect either--the Resize option remains greyed out.

By the way, I think the window actually *is* maximized as the corners are not rounded as they are when a window is full-sized but not maximized.

Thanks very much for the thought!

[edit]  If I *drag* the window it unmaximizes automatically but can only be resized to a width of no less than five inches.  If I close the file and reopen it, it reopens unmaximized but still with the 5" horisontal minimun.  Curious.

---


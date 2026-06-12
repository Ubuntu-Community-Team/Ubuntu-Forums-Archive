---
title: "Rhythmbox, status icon, show/hide, window position fix"
date: 2008-10-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by pelle.k on 2008-10-28
Hiya. You might discover that rhythmbox doesn't remember it's window position when unhiding from pressing the status/notification icon in the system tray.
I've corrected this behavior and and sent the fix to launchpad and the gnome bugtracker.
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/175164](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/175164)

If you want to try the patched rhythmbox out, i've created packages for testing here;
[http://download.tuxfamily.org/pandora/temp/rhytmbox-intrepid/](http://download.tuxfamily.org/pandora/temp/rhytmbox-intrepid/)

I hope this is useful to someone.

---

### Post by jfernyhough on 2008-10-28
Thank you for taking the trouble to do all that.

(Though it works fine already for me. :) )

---

### Post by pelle.k on 2008-10-28
> **jfernyhough said:**
> Thank you for taking the trouble to do all that.

(Though it works fine already for me. :) )

Are you sure?
I mean, if you move it to say upper right corner and then minimize to tray, then unminimize, does it appear in the upper right? Also, if you repeat this procedure (trying new positions) a few times, does it alway find the position you minimized from?

---

### Post by Fixxxer on 2008-10-28
> Are you sure?
I mean, if you move it to say upper right corner and then minimize to tray, then unminimize, does it appear in the upper right? Also, if you repeat this procedure (trying new positions) a few times, does it alway find the position you minimized from?
I tried that and for me Rhythmbox remembers it's position every time. I also tried minimizing it both by pressing the close button and by pressing on the tray icon, no difference.

---

### Post by pelle.k on 2008-10-28
Ok. That is so strange! Oh well, it was a learning experience at least.
I'll better purge my gconf or reinstall or something LOL, cause the original rhythmbox does *not* do that for me.

Thanks guys for the feedback!

---

### Post by pelle.k on 2008-10-28
Allright. The bug is *only* evident if you run metacity as window manager as opposed to compiz as a window manager.

Again, thanks guys :)

---

### Post by Fixxxer on 2008-10-29
No problem! And you're right, when using metacity as window manager Rhytmbox doesn't remember it's position.

---


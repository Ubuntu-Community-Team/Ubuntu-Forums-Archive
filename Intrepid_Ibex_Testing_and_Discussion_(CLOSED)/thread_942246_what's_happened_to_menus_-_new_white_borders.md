---
title: "what's happened to menus - new white borders?"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by scradock on 2008-10-09
I have noticed that the menus in my GNOME desktop have white borders - I think that's new. Can anyone confirm? 

The border is several pixels wide and looks plain ugly, obscuring what lies underneath the menu without being in any way useful.

As this is Gnome I am sure I can configure them - but how? Where are menus configured?

---

### Post by inportb on 2008-10-09
This may be what malfunctioning drop-shadows look like.
Video processing problems, perhaps?

Try killing X, restarting X nicely, or rebooting.

---

### Post by ronacc on 2008-10-09
I don't think I'm seeing that here , screenshot please .

---

### Post by inportb on 2008-10-09
I think it might be a transient issue; I had a minor glitch with KWin not being able to enable compositing until I killed X to restart it (restarting X normally did not work).

---

### Post by scradock on 2008-10-09
> **inportb said:**
> This may be what malfunctioning drop-shadows look like.
Video processing problems, perhaps?

Try killing X, restarting X nicely, or rebooting.

Yes, that was it - malfunctioning drop-shadows. Restarting compiz fixes it, but it happens again next time I start up. But not every time - very annoying!

I'm using the gtk-decorator and indirect rendering.

---

### Post by Hairy_Palms on 2008-10-09
what video card do you have?

---

### Post by scradock on 2008-10-09
> **Hairy_Palms said:**
> what video card do you have?

ati Radeon Express 200M (5955)

I'm using the ati/radeon drivers, since fglrx doesn't work in Intrepid.

---


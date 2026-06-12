---
title: "Gnome-shell now broken"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by prattmd on 2009-10-12
On the latest update, gnome-shell is now broken.  Get an error stating it is trying to use an unsupported open GL command.  

This has already been reported.

I was really liking playing with gnome-shell

bummer

Mark

---

### Post by buzzmandt on 2009-10-13
still runs for me, but with error
> buzzmandt@buzzmandt-laptop:~/gnome-shell/source/gnome-shell/src$       JS LOG: conforming method: IntrospectRemote for org.freedesktop.DBus.Introspectable
      JS LOG: Loading equations.js
      JS LOG: Done loading equations.js
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!


---

### Post by Peter09 on 2009-10-13
I noticed that it failed on the first run, with an error, but running it immediately again was alright. I think it is to do with compiz dropping out.


Edit: - at least one of my machines now fails to run gnome-shell after the latest update :(
Edit:  - at least two of my machines now fails to run gnome-shell after the latest update #-o

---

### Post by jfernyhough on 2009-10-13
> **prattmd said:**
> trying to use an unsupported open GL command.Hmm... I get this with my nvidia drivers when trying to play RA3 in Wine. It used to work up until around the last driver update to 190.36.

---

### Post by Peter09 on 2009-10-13
My Gnome-shell is now working after a further update - I have also noticed that I can remove openoffice and evolution from the favorites menu by right clicking - plus the clock also has a calender when clicked - when did this happen?

---


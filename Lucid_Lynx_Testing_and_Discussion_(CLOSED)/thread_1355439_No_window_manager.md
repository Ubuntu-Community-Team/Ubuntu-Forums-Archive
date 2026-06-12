---
title: "No window manager"
date: 2009-12-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by PaulInBHC on 2009-12-14
I got home from work and ran update from the dropdown. I did not install partial updates as far as I know. Opened FF. It starts minimised, upper left, blocking the top panel. There is no top bar on the FF window to allow max, min or close. I tried window manager and get an error popup stating I don't have one. Now what?

---

### Post by jpeddicord on 2009-12-14
> **PaulInBHC said:**
> I got home from work and ran update from the dropdown. I did not install partial updates as far as I know. Opened FF. It starts minimised, upper left, blocking the top panel. There is no top bar on the FF window to allow max, min or close. I tried window manager and get an error popup stating I don't have one. Now what?

Try this first (Alt+F2):
```
gtk-window-decorator --replace
```
Sometimes for whatever reason gtk-window-decorator will launch but won't draw anything... this fixes it for the session.

If that doesn't work, try:```
metacity --replace
``` (replace metacity with compiz if using desktop effects.)

---

### Post by PaulInBHC on 2009-12-14
I booted back in to Lucid. Black screen but got the bongos. Logged in. I did not have to try your suggestions, the windows are back to normal.
No mouse pointer visible now. I used alt + F2 to start FF. I am using crtl to find the mouse position.
yikes

Edit, I opened synaptic, typed pointer into search, and my pointer appeared, lol

---

### Post by VMC on 2009-12-15
> **jpeddicord said:**
> Try this first (Alt+F2):
```
gtk-window-decorator --replace
```
Sometimes for whatever reason gtk-window-decorator will launch but won't draw anything... this fixes it for the session.

If that doesn't work, try:```
metacity --replace
``` (replace metacity with compiz if using desktop effects.)

I have to remember this trick next time this happens to me. Great tip. I never knew what to do so I delete .gconf and have it rebuild everything from scratch.

---

### Post by panaut0lordv on 2009-12-15
> **PaulInBHC said:**
> I booted back in to Lucid. Black screen but got the bongos. Logged in. I did not have to try your suggestions, the windows are back to normal.
No mouse pointer visible now. I used alt + F2 to start FF. I am using crtl to find the mouse position.
yikes

Edit, I opened synaptic, typed pointer into search, and my pointer appeared, lol

I love your bug :popcorn: xD I think I won't upgrade today!

---


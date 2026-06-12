---
title: "Grub2 background image - 05_debian_theme changes?"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by BrokeMahPC on 2010-04-06
I was wondering about adding a background image to Grub 2 in Lucid.
The format of the /etc/grub.d/05_debian_theme has changed. The place on line 16 where you used to add the background image has changed format and moved to line 26?

for i in /boot/grub/`basename ${WALLPAPER}` ${WALLPAPER} ; do

Is there new advice anywhere for theming Grub2?

---

### Post by MacUntu on 2010-04-06
Should be sufficient to update the line: ```
WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"
```

---

### Post by BrokeMahPC on 2010-04-06
Thank you MacUntu!
I wondered about that but could not believe it was that simple. I moved a picture of the plymouth splash to: /usr/share/images/desktop-base
with code: gksu nautilus

(from reading it's probably best if your picture size in pixels matches the grub resolution?)

Then
code:
  gksu gedit /etc/grub.d/05_debian_theme

edit line 10:
WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"
to:
WALLPAPER="/usr/share/images/desktop-base/plymouthsplash.png"

if you use a dark picture you need white text so also edit line 11:
COLOR_NORMAL="black/black"
to:
COLOR_NORMAL="white/black"

then code: sudo update-grub

all done - I have a nice aubergine Ubuntu Grub splash with white text.

---


---
title: "KDE apps distorted in gnome."
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by danboy on 2009-04-10
My KDE apps seem to have font rendering issues in gnome, i searched the forums, but can't seem to find anything.

Anyone see this before?

I've tried turning compiz on/off, messed w/ font settings, etc.

nada.

Nvidia video card.

sony via vgn-ar570

Check the attached screenshot.

---

### Post by danboy on 2009-04-12
bump.

---

### Post by phenest on 2009-04-12
Hmmm. I've used both Compiz, and Metacity. I also use VirtualBox, and I have an nVidia card. No problems here. Very odd.

---

### Post by inportb on 2009-04-12
Incidentally, Virtualbox is not a KDE app but a Qt app.
(KDE apps are Qt apps, but not necessarily the other way around.)

---

### Post by Zorael on 2009-04-12
Any insane ~/.fonts.conf file?

And, hm, could the qtconfig app help in this case?

---

### Post by danboy on 2009-04-13
qtconfig was my first thought unfortunately it has the same distortion issues, so i'd just be clicking blind.

---

### Post by jensbw on 2009-04-14
There was a known issue with using subpixel font rendering with the vrgb setting in Qt 4.5.0. You might try to change this setting to see if that affects you.

---


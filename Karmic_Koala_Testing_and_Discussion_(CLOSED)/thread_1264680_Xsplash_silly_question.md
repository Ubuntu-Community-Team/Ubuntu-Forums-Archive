---
title: "Xsplash silly question"
date: 2009-09-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dentaku65 on 2009-09-12
I know that xsplash is nice and sexy; but I don't understand why to boot my machine I have to do:
usplash+xsplash+gdm+xsplash+gnome
instead of
usplash+gdm+gnome

Beside the eyecandy, what is or what will be the benefit to use xsplash?

---

### Post by taavikko on 2009-09-12
usplash will be dropped in it's due time, they're working on it.
It will remain as a fallback on those machines that takes a loooong time to boot
and for fsck and such.

---

### Post by knn on 2009-09-12
> **dentaku65 said:**
> I know that xsplash is nice and sexy; but I don't understand why to boot my machine I have to do:
usplash+xsplash+gdm+xsplash+gnome
instead of
usplash+gdm+gnome

Beside the eyecandy, what is or what will be the benefit to use xsplash?

The real goal is to start X as soon as possible. With the os selector, you'd then be able to select the os while Ubuntu is loading in the background, instead of delaying Ubuntu loading with the grub timeout. Unfortunately, that has been postponed.
I also imagine gdm will be started before everything is up, so while you're typing your password the system could still be booting.
Xsplash is just the eye candy so you don't stare at a blank X session.

---

### Post by cyberkilla on 2009-09-14
I wonder whether we'll still be able to disable this by removing the splash parameter in GRUB.

---


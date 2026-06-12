---
title: "Screen's brightness is dark after login (with NVidia binary driver)"
date: 2009-09-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by krausest on 2009-09-19
There's something strange going on on my laptop (hp hdx 9300).
GDM starts, shows the splash screen and when the splash screen is finished the brightness is reduced in few steps until finally my screen is completely dark. If I switch back to a console and then back to X11 the screen has full brightness again.
It happens both when I'm on AC and on battery. (BTW I do have the same effect on Fedora 11 since a few weeks.)

I've no idea what could be the cause for that behaviour. There's nothing interesting in dmesg or Xorg.log.

Any ideas what could cause that effect?

---

### Post by gnomeuser on 2009-09-20
This happens for me as well, On F12 with the nouveau driver and on Karmic with the proprietary driver (haven't yet tested nv).

---

### Post by gnomeuser on 2009-09-21
I filed this here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433889](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433889)

---

### Post by krausest on 2009-09-23
Filed a bug too
[https://bugs.launchpad.net/ubuntu/+bug/434163](https://bugs.launchpad.net/ubuntu/+bug/434163)
(BTW: What does "is not in ubuntu" mean in a bug report's title?)

Maybe I found a workaround, but as usual I did two things at the same time and thus don't know what it was...
- I disabled all dimming in the power management preferences and clicked on "make default"
- I edited in gconf-editor "apps > gnome-power-manager > backlight" and unchecked every option there.

At least the issue hasn't shown up since those changes.

---

### Post by talkingwires on 2009-09-24
The only way I've been able to adjust my screen brightness the past few releases has been to boot into Windows or do it before the GDM kicks in. I've got bug reports over three years-old regarding my laptop. Just sayin'.

---


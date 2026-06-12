---
title: "easy video problem (I think)"
date: 2009-04-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Awareness on 2009-04-22
Similar problem than [http://ubuntuforums.org/showthread.php?t=1121841](http://ubuntuforums.org/showthread.php?t=1121841) but with video

kde works fine, but if i enter in gnome it says "out of range" and nothing else is displayed in the screen

If i create a new user, gnome works fine... what should i delete from home?

I tried .gnome .gnome2 .gnome_private and anything else with gnome in the folder name but still the same problem :S

Ive got nvidia card with nvidia drivers btw

---

### Post by Zorael on 2009-04-22
Tried this?
> [SIZE="4"]Resetting an out-of-range resolution[/SIZE]

If you set a resolution inappropriate for your monitor in the Screen Resolution GUI tool, you can reset it by running **rm ~/.config/monitors.xml** from a terminal. 
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by Awareness on 2009-04-22
Worked like a charm...

Thank you very much... i've been googling for months for this... and lots of rebooting... I guess im not very good searching :(

On the bright side, it made me try kde and i liked it :lolflag:

---


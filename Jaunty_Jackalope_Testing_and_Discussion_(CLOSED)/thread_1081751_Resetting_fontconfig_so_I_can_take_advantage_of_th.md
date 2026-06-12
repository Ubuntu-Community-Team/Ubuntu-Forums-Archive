---
title: "Resetting fontconfig so I can take advantage of the new DPI defaults?"
date: 2009-02-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-02-26
How would I go about resetting fontconfig so that my manually set 96dpi setting is removed?

---

### Post by andrewabc on 2009-02-26
Not sure.

What about
system->preferences->appearance->fonts->details->input dots per inch you want?

Although I'm guessing you want to try out the new xorg thing where it detects monitors default dots per inch setting? I have no idea how that works.

---

### Post by Starks on 2009-02-26
> **andrewabc said:**
> Not sure.

[B]What about
system->preferences->appearance->fonts->details->input dots per inch you want?[/B]

Although I'm guessing you want to try out the new xorg thing where it detects monitors default dots per inch setting? I have no idea how that works.

Doing that would defeat the purpose of Jaunty detecting the ideal DPI automatically.

---

### Post by kerry_s on 2009-02-27
the default is usually 96, which is what windows uses.
you should calculate and set it manually.
use this:
[http://www.raydreams.com/prog/dpi.aspx](http://www.raydreams.com/prog/dpi.aspx)

---

### Post by forumache on 2009-02-27
dan@shuttle:~$ xdpyinfo |grep dots
resolution:    85x86 dots per inch

This is calculated automatically by X and, with the new changes, should be used by Gnome. But you can adjust it manually. No need to calculate yourself (although you can verify it was calculated correctly)

---

### Post by Gourgi on 2009-02-27
> **forumache said:**
> dan@shuttle:~$ xdpyinfo |grep dots
resolution:    85x86 dots per inch

This is calculated automatically by X and, with the new changes, should be used by Gnome. But you can adjust it manually. No need to calculate yourself (although you can verify it was calculated correctly)

```
$ xdpyinfo |grep dots
  resolution:    87x83 dots per inch
```
85 is set through appearance, so i guess it's ok ?

---

### Post by MacUntu on 2009-02-27
> **Starks said:**
> ideal DPI

Ideal for whom? On my 14" 1280x768 notebook the "ideal" DPI is far from being ideal. :P

---

### Post by uBeer on 2009-02-27
> **MacUntu said:**
> Ideal for whom? On my 14" 1280x768 notebook the "ideal" DPI is far from being ideal. :P

Just like the 132x133 on my 17" 1920x1200... I bought this thing to have lots of screen space, but with 133 dpi it's all for nothing ;)
But I don't mind that much, I know how to change it to my needs and I guess that my resolution is not a widespread phenomenon. But maybe it could be a good idea to set some restrains for the dpi setting (if it isn't already so) like dpi can't be lower than 88 and can't get higher than 112. Does anyone know if there are some limits to it?

---

### Post by andrewabc on 2009-02-27
LG 20" -> 99 dpi (formerly 96?)
samsung t220 -> 90 dpi  .........Intrepid->96 dpi

Very interesting.
So does proper dpi make things easier to read/see?

---


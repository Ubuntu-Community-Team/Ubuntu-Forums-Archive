---
title: "Karmic Intel 965 card with xrandr"
date: 2009-09-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by shanix on 2009-09-14
Hi All,

Not sure if I am the only one, I have the 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

When I tried to setup the dual screen using the gnome-display-properties, there is no response. i.e. when you click apply, the window just stay there.

Tried, xrandr --auto (when I try to enable the second monitor), same thing. No error, no response. 

I also try the x-edgers ppa, normal X driver and the x-testing. they all behave the same.

Anything else that I might be able to try?

Oh, I also tried disable the compiz, remove the xorg.conf file, none of them help...

Thanks!

---

### Post by C38a7r1zvl on 2009-10-26
Shanix,

you might want to double check the names of your output devices. In Jaunty my laptop screen was named LVDS and my external display TMDS1, now they are LVDS and DVI1 respectively. Took me a while to spot this..

Cheers,
Niels

---


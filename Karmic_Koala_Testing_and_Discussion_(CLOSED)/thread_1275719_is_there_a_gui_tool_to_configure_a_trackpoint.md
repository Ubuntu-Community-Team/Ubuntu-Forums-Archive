---
title: "is there a gui tool to configure a trackpoint?"
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by excogitation on 2009-09-26
e.g. like for touchpads?

I'm trying to get my 3rd mouse button to work and
use the z-axis to make mouse clicks.

configure-trackpoint doesn't detect my trackpoint.

The pointing stick is
044e:3017 Alps Electric Co., Ltd
on a Vaio VGN-P11Z.

---

### Post by kerry_s on 2009-09-26
did you look in preferences-> mouse

---

### Post by jmcvey on 2009-09-26
Had a similar issue with a thinkpad. Found gpointing-device-settings available in the repos. Install and then run it from a terminal. It pops up a graphical configuration tool that has a "wheel emulation" option. Check that box and it should enable it. Only issue I had once I turned that on was the default button number was 4. I changed that to 2 and using the middle mouse button and pushing up or down on the trackpoint now scrolls up or down respectively.

---

### Post by excogitation on 2009-09-26
> **kerry_s said:**
> did you look in preferences-> mouse
;-) Did you read my post?

> **jmcvey said:**
> Had a similar issue with a thinkpad. Found gpointing-device-settings available in the repos. Install and then run it from a terminal. It pops up a graphical configuration tool that has a "wheel emulation" option. Check that box and it should enable it. Only issue I had once I turned that on was the default button number was 4. I changed that to 2 and using the middle mouse button and pushing up or down on the trackpoint now scrolls up or down respectively.

I missed the scrolling feature when I last tried that. Thanks.

Still no clicking with the pointing stick... [like with this tool]("http://tpctl.sourceforge.net/configure-trackpoint.html") (that unfortunately doesn't work with karmic andor my pointing stick).

---


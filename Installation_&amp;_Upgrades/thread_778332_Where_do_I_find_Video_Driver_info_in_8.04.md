---
title: "Where do I find Video Driver info in 8.04"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by mike farad on 2008-05-02
I upgraded to 8.04 from 7.10 today, and I'm trying to get my 780G based MoBo to work,  I loaded the fglrx package and everything seemed to work ok, but i see no difference from what I had before I loaded them,  In the older Ubuntu version, if I could go to the System tab, Administration something'er other, and find a tab which would let me look at my monitor setting and loaded Graphic Driver setting.  Under 7.10, my 780G chip set would only report back as Vesa.  In 8.04, going thru the System Tab, all I can see is a 'cut down' version of the older info screen.  Now I can't see what Graphic Driver is loaded, and the menu only reports something like 'Cloned Screen' and its resolution setting.  Has 8.04 dumbed the graphic reporting info?

Mike

---

### Post by ansicplusplus on 2008-05-02
Hy, hardy uses autodetection as prefered method and removed the configuration-dialog from the menu. Unfortunately autodetection doesn't work for everyone. Try ```
gksudo displayconfig-gtk
``` and you get what you are looking for.
Yours, ansicplusplus

---


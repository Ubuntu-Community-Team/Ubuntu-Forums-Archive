---
title: "Text too small in Jaunty after changing resolution"
date: 2009-02-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by leillo1975 on 2009-02-25
Hello

I'm installed Jaunty today, and I configure xorg.conf with and old configuration of Hardy (the screen resolution by default is 800x600 and I can't change to 1280x1024 in Preferences-> Screen Resolution). I have a Digitus Video Selector to connect two PC's in one LCD Monitor, and it provoques that the X server don't detect correctly the monitor. 

In hardy I configure the monitor with displayconfig-gtk, but in Intrepid this application was deleted from Ubuntu (and repositories), and now I need the old xorg.conf to configure screen. Developers, can you include displayconfig-gtk or something like it...

The problem in Jaunty are the text, that now is very little, after changing the resolution. I try to change it in Preferences -> Appearance -> typography, but the text in amarok, emesene, openoffice, k3b and other applications is  little.

¿Can I change the text lenght by default in this apps?

---

### Post by Mr. Picklesworth on 2009-02-25
Go to System Preferences -> Appearance and look under the Font tab.

---

### Post by leillo1975 on 2009-02-25
this is exactly I did it, I´m change the four lenghts of the fonts, but in certain programs the letters don´t change

---

### Post by terry_gardener on 2009-02-25
i had something very similar to this when i first installed jaunty. 

the way the i got round it was by increasing the font dpi to 96 has it changed to 60 making text very small. 

to change the font dpi, goto system-preferences-appearance and then click the font tab. in this tab click details and the very top option should be resolution (dot per inch) change this to 96.

---

### Post by leillo1975 on 2009-02-26
Thank you everybody

I'm change dpi to 90 and the font lenght to 10 and everything is ok

Thanks

---


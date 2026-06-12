---
title: "gusty window title font big"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by El Viejo Lobo on 2007-11-25
I am lost with this problem, I took down the font size but it is keeping appear too big as you can see in the screenshots attached.

---

### Post by johnconnor on 2007-11-26
Hi!

Take a look at this :
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/141001](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/141001)

---

### Post by El Viejo Lobo on 2007-11-26
> **johnconnor said:**
> Hi!

Take a look at this :
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/141001](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/141001)

Thanks for the information. I went to System/Preferences/Appearance opened Visual Effects   
tab and change it from "Normal" to "None" and the problem was fixed but beauty was left for other and better days.   :(
See attached sceenshot!

---

### Post by johnconnor on 2007-11-27
Don't change anything in the Appearance dialog, just type this in your terminal:

*gtk-window-decorator --replace &*

Then press Ctrl + Alt + Bksp. This way you can keep visual effects turned on

---

### Post by El Viejo Lobo on 2007-11-27
I do not know how and why but I tried again: "visual effects"  in "Normal" and it works with no bug anymore. 
Thanks for your advice.
:guitar:

---


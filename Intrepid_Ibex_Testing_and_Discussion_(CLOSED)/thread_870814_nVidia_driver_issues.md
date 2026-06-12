---
title: "nVidia driver issues"
date: 2008-07-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phenest on 2008-07-26
The Hardware Drivers gives 3 possible nVidia drivers: 96, 173, and 177. 96 does not seem to recognize my video card and gives default settings. That's not a problem, as 173 and 177 do work but not properly. I use Avant Window Navigator instead of Gnome Panels, and use Metacity as composite manager. This results in AWN having artifacts left all over the place. If I switch to the open source nv driver, all is fine. But then I don't get 3D support.

---

### Post by ronacc on 2008-07-26
try using your xorg.conf from hardy , that allowed me to use the 177 or 173 driver .

---

### Post by phenest on 2008-07-26
I am.

---

### Post by phidia on 2008-07-26
xorg.conf has changed since hardy & xorg 7.3 see the note and additional troubleshooting from [this page]("https://help.ubuntu.com/community/Video").

although how that applies to ibex I'm not completely sure.

I ran "nvidia-xconfig" a couple of times and rebooted and the nvidia driver is working now-but it wasn't working until I ran that command. 
I also tried using the xorg.conf from a working stable release but it didn't fly.

---

### Post by phenest on 2008-07-27
To clarify, I have included a screenshot. This happens with the 173 & 177 proprietry drivers, but no problems with the nv driver.

---

### Post by Gina on 2008-07-27
Alpha 3 new install.  No problem.  177, 173 and 96 drivers listed but not enabled in Hardware Drivers dialog.  Ticked the Enable on 177 (6200 graphics)... the drivers installed and display worked perfectly after reboot.

---

### Post by phenest on 2008-07-27
Are you using AWN with Metacity as composite manager?

---

### Post by Gina on 2008-07-27
> **phenest said:**
> Are you using AWN with Metacity as composite manager?No - only tried the default setup so far.  Lots still to check out yet.

---

### Post by ronacc on 2008-07-27
using compiz and emerald here .

---

### Post by litemotiv on 2008-07-27
> **phenest said:**
> Are you using AWN with Metacity as composite manager?

well, i hade the exact same problem but in my case it was caused by an awn update

---

### Post by Gina on 2008-07-28
Must try AWN sometime - I like the look of it :)

---

### Post by phenest on 2008-07-28
Another issue I've noticed is the open source nv driver gives me the correct refresh rate of 60Hz, whereas the nvidia restricted driver gives a lower 51Hz.

Any reason for the differing rates?

---

### Post by Nullack on 2008-07-28
Nvidia hacks up the reported refresh rate due to limitations in X - your still actually getting your normal refresh rate its only different in what it says. To get it to report the actual you can disable twin view but then it wont work with twin view obviously.

---

### Post by minisori on 2008-07-31
I have the same problem with awn, but i use compiz. I also noticed the problem too in emesene at times, mainly when you open the contact list, but it get fixed after a few seconds.

Maybe the problem is related to python refresh? Because when you move the mouse over icons which bounce or something similar, those artifacts are gone.

---


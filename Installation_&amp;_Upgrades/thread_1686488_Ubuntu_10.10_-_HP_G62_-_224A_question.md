---
title: "Ubuntu 10.10 - HP G62 - 224A question"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by PT-Desu on 2011-02-12
Hey, I have a HP G62 - 224A laptop and running Ubuntu 10.10 not updated to lazy ^^, anyhow there are two things I can't solve

1 - The battery icon always tells me Calculating or was it Estamating but never gives me battery %

2 - I am right handed and the windows controls minimzie, maximice, and close do bug me since they are in the left corner and I am more used to older ubuntu being in right corner 

so how would I can get the battery to show me % instead of always telling me that its calculating the % and never gives me a number, I always have to go into the extend properties of it. 

and not only that how can I decrease the load on the battery since when using Ubuntu the laptop dies much quicker then using W7

---

### Post by gordintoronto on 2011-02-12
I also have a G62, but I'm running 10.04. My battery icon works properly. To change the location of the window controls, right-click on empty desktop and select "Change Desktop Background." Select the "Theme" tab, and select "Clearlooks." You can play around with different themes if that one doesn't appeal to you.

In System/Preferences/Power Management I think you can find a brightness control, which can help extend battery life.

---

### Post by PT-Desu on 2011-02-12
I had a copy of 10.04 somewhere, and yes I think it did show me battery and such but I lost it somewhere so I dl a copy of 10.10 and then the icon never worked

---

### Post by fett2k on 2011-03-10
any way to downgrade whatever is needed to the power icon works properly?

about the right handed thing..
Alt+F2, then you run gconf-editor. here you go to /apps/metacity/general/button_layout, and you enter ":minimize,maximize,close"

---


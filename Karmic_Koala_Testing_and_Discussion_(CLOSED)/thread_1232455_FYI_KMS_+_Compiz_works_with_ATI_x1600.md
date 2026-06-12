---
title: "FYI: KMS + Compiz works with ATI x1600"
date: 2009-08-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wayne_cat on 2009-08-05
ok ... one of the updates (today) fixed it. My Macbook boots with a 1440x900 resolution
and Gnome + Compiz starts without problems ... no crashes or freezes since 2 hours.

- Kernel: 2.6.31-5-generic + boot option "radeon.modeset=1"
- Packages from xorg-edgers

Unfortunately my ATI does not support "gfxpayload=1440x900x32" ... so no seamless
 booting at the moment ... but at least a usable TTY resolution and Compiz eye candy.

---

### Post by taavikko on 2009-08-05
Yes, 600/700 cards have a working 3D Compiz, too bad it requires xorg-edgers :(
i just hope that they'll push the code to official repos so anyone could be happy :)
At least to final release...

---


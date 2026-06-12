---
title: "Almost have ATI drivers"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by zoomy942 on 2008-10-15
So, I finally see the restricted drivers available but when i try and activate them, i get this...

Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid.

---

### Post by helliewm on 2008-10-15
New ATI Catalyst Drivers have literally just come into the Intrepid Repositories see my post here for full instructions:


[http://ubuntuforums.org/showthread.php?t=948529]("http://ubuntuforums.org/showthread.php?t=948529")

This should solve your problem.

Helen

---

### Post by zoomy942 on 2008-10-15
Edit

---

### Post by zoomy942 on 2008-10-15
so now my desktop effects wont enable either.

---

### Post by zoomy942 on 2008-10-15
hmm..  So i did a few more updates and now everything is current.

Anyone else have their ATI broke?

---

### Post by zoomy942 on 2008-10-15
cancel that

ran sudo aticonfig --initial -f and it worked great!

---

### Post by rbmorse on 2008-10-15
Odd. All I did was click the "activate" button on the restricted driver manager when it announced the restricted driver was available.  Desktop effcts work and VLC plays video in Xv mode. 

I did not have to make any changes to xorg.conf or run any aticonfig routines. I did reboot the machine after the driver was installed.

---


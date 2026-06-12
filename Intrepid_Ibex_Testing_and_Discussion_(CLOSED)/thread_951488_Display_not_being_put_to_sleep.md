---
title: "Display not being put to sleep"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nirro on 2008-10-18
Since update to Intrepid Beta,
My display does not being put to sleep,
In power-configuration it is set to 30mins on AC (desktop- no battery),
but it doesn't work.

I use Compiz, nvidia 7600GS.


Does anyone know how to fix this ?

Thanks.

---

### Post by forumache on 2008-10-19
It might be this bug: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/159263](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/159263)

---

### Post by otherush on 2008-10-19
In compiz config settings manager go to general options. Select the general tab and untick "undirect fullscreen windows". If this doesn't work I would suggest unticking "force independent output painting" also, if it wasn't already.  I hope this works for you, it did for me. :)

---

### Post by dondad on 2008-10-19
> **otherush said:**
> In compiz config settings manager go to general options. Select the general tab and untick "undirect fullscreen windows". If this doesn't work I would suggest unticking "force independent output painting" also, if it wasn't already.  I hope this works for you, it did for me. :)

This worked for me also. Mine would go to the screensaver and immediately come back to the screen. Screensaver and powerdown of the monitor did not work. Unticking the box fixed both.

---


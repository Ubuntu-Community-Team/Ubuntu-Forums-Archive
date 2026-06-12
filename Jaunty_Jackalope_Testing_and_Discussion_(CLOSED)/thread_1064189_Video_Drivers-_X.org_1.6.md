---
title: "Video Drivers- X.org 1.6"
date: 2009-02-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by damispyderbyte on 2009-02-08
Hi,
I still cannot find solid proof of what drivers are ready for x.org 1.6.  I have a nvidia 8600GT and wondering if it is safe to install the nvidia beta 180.10 driver. Thanks for your help!!!

---

### Post by RAOF on 2009-02-08
The beta 180.10 driver?  No.

The 180.27 release driver, that you'll get by installing the nvidia-glx-180 package?  Yes.

---

### Post by blazemore on 2009-02-08
So we can install the Nvidia drivers on Jaunty now and have them work? With 3d effects?

---

### Post by RAOF on 2009-02-08
Modulo [bug 326344](https://bugs.launchpad.net/bugs/326344), yes.

---

### Post by Keks01 on 2009-02-08
> **blazemore said:**
> So we can install the Nvidia drivers on Jaunty now and have them work? With 3d effects?

not really, a recent xorg update doesn't play nice with 3d effects - session hangs on startup if compiz is enabled.
but you can install nvidia drivers and they should work.

---

### Post by blazemore on 2009-02-08
Compiz, but what about Kwin?

---

### Post by RAOF on 2009-02-08
If I read the bug correctly, anything that tries direct rendering will lock X.  So, if you're using the OpenGL backend for KWin, yes.  That will also lock X.

---

### Post by jman6495 on 2009-02-09
Confirming The Same Problem With ATI Radeon,And Radeon Mobility
(to be exact Moblilty x300)

Jman6495

---


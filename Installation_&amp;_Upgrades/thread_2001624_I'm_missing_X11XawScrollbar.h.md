---
title: "I'm missing X11/Xaw/Scrollbar.h"
date: 2012-06-11
forum: Installation &amp; Upgrades
---

### Post by Icarus92 on 2012-06-11
Hi I've just started to use Ubuntu for my uni projects and I've come across a problem while trying to run a program required for my projects.

The error says
missing X11/Xaw/Scrollbars.h

I went to the folders where X11 is located and I have Xaw3d but for some reason I'm missing the 2d counterpart. Could someone tell me the name of the package I can use with apt-get to get Xaw2d. 

Thanks

---

### Post by David Andersson on 2012-06-11
I suspected it was in a "-dev" package and searched for "xaw" in Synaptec. Found /usr/include/X11/Xaw/Scrollbar.h in package **libxaw7-dev**.

---

### Post by Icarus92 on 2012-06-11
That worked, thank you very much

---


---
title: "XvMC. How do I enable?"
date: 2009-02-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-02-07
I have an Intel 945GM running the 2.6.99 drivers.

---

### Post by taavikko on 2009-02-07
xorg.conf edit.. add 
option "XvMCSurfaces" "6" 
You could try to raise value...

and drm is vital.

Atleast this is my recollection..??
Hope this helps..
Edit, more info: [http://en.wikipedia.org/wiki/X-Video_Motion_Compensation](http://en.wikipedia.org/wiki/X-Video_Motion_Compensation)

---


---
title: "Firefox and flash movies.."
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by slakkie on 2009-09-03
Is it me or is Flash and FF3.5 a bit buggy? 

I keep getting hang ups on FF and flash movies..

---

### Post by mike555 on 2009-09-05
If it's crashing when you click to get full screen you should add 

the following to '/usr/lib/firefox/firefox.sh'

" export LD_PRELOAD=/usr/lib/libGL.so.1 "

 == if you search around you will find more info on it ...

---


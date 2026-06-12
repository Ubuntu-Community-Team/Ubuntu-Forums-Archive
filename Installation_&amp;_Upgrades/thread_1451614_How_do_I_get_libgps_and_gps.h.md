---
title: "How do I get libgps and gps.h ?"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by windlet on 2010-04-10
I have gpsd running.

gpscat -s 4800 /dev/ttyUSB0   is working... throwing out GPS sentences :
$GPGSA,A,2,,,,,,,,,,,,,0.0,20.0,0.0*01 
$PGRME,8.54,M,2.95,M,0.00,M*19 
$GPGGA,164736,4823.3362,N,12229.7686,W,1,03,20.00,-37.11,M,-17.957,M,,*55 
$GPRMC,164736,A,4823.3362,N,12229.7686,W,7.1322,141.530,100410,,*31

now I want to write a special purpose NMEA parser.  Anjuta complains it can't find the file on the statement
#include <gps.h>

I can't find gps.h nor a gps library using find.

Where do I get libgps and gps.h ?

windlet

---

### Post by SnickerSnack on 2010-04-10
You probably need libgps-dev, which is available through apt. edit:

```
sudo apt-get install libgps-dev
```

I don't know much about C, but I'd guess that gps.h is in that library.

---

### Post by windlet on 2010-04-10
THANK YOU !!

That worked.

John

---

### Post by SnickerSnack on 2010-04-10
> **windlet said:**
> THANK YOU !!

That worked.

John

No problemo.  Be sure to mark the thread as "solved" with the "thread tools" link near the top of the page.

---


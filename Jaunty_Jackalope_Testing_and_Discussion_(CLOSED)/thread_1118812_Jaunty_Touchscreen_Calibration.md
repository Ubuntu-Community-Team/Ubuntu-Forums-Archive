---
title: "Jaunty Touchscreen Calibration"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by munroe on 2009-04-07
I just upgraded to Jaunty and my Netbook touchscreen is working! I'm thrilled.

However the x/y coordinates seem to be a bit off. I'm wondering if a calibration tool exists so I can modify those points.

Any help would be appreciated.

Thanks!

---

### Post by Joeb454 on 2009-04-07
Moved to Jaunty Testing :)

I've never dabbled with a touchscreen on Linux, but are there no applications in the Repo's for this?

---

### Post by ibuclaw on 2009-04-07
A quick look in the apt-cache finds this following package:
```
libts-bin
```
Which appears to contain a set of utilities to configure the touch screen library.

And a list of programs contained in it:
```

/usr/bin/ts_test
**/usr/bin/ts_calibrate**
/usr/bin/ts_print
/usr/bin/ts_print_raw
/usr/bin/ts_harvest

```

I second to Joeb454, I don't have a touchscreen computer either, so I wouldn't know how to go about setting it up. But I hope I've nudged you in the right direction.

Regards
Iain

---


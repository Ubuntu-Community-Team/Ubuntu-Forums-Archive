---
title: "Ubuntu 11.10 - arduino sketched no longer compile"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by mlucia55 on 2011-10-16
I upgraded to 11.10 and found that even the simplest of 'example' sketches no longer compile without errors

---

### Post by Tux Aubrey on 2011-10-17
Hi mlucia55

Have you tried reinstalling the Arduino IDE?  You may have dropped some dependencies in the upgrade, especially if you were not using the version of Ardiono in the repos.

I am using v22 and didn't notice any issues after upgrading from 11.04 to 11.10.

Maybe it is time to try the Vesion 1.0 RC ([http://code.google.com/p/arduino/wiki/Arduino1](http://code.google.com/p/arduino/wiki/Arduino1)) If you do, let us know how it goes.

---

### Post by mlucia55 on 2011-10-17
Thanks for the reply - I tried removing and re-installing arduino and the avr compiler but had the same symptom.

After some additional testing, it would seem that the version I DLd from arduino exhibits the new symptom, along with the version that is launched with the icon from the menu.

If I open arduino from the command line (from usr/bin/ ) it's much happier

I will work to remove *all* versions and reinstall and see if I can clean things up a bit


To help others, here is a more complete description of the symptom:

The symptom that presents with the DLd version is with avr-gcc

In file included from /usr/lib/gcc/avr/4.5.3/../../../avr/include/util/delay.h:44:0,
                 from /usr/lib/gcc/avr/4.5.3/../../../avr/include/avr/delay.h:37,
                 from /home/mlucia/arduino-0022/hardware/arduino/cores/arduino/wiring_private.h:30,
                 from /home/mlucia/arduino-0022/hardware/arduino/cores/arduino/WInterrupts.c:34:
/usr/lib/gcc/avr/4.5.3/../../../avr/include/math.h:426:15: error: expected identifier or ‘(’ before ‘double’
/usr/lib/gcc/avr/4.5.3/../../../avr/include/math.h:426:15: error: expected ‘)’ before ‘>=’ token

---

### Post by dvberkel on 2011-10-17
Ubuntu 11.10 has arduino 0022 in the repositories. So no custom install is needed anymore.

I had the same problem as stated in this thread. I removed my custom installation and downloaded the arduino package and it's dependencies directly from the repositories. After that the compilation problems were gone.

---

### Post by xl100 on 2011-11-15
I tried installing arduino from the repositories but I still get the same error.

---

### Post by mgreensmith on 2011-11-25
This compilation error is caused by a conflict with gcc-avr math.h library.  See my blog post for a full explanation.

[http://mattgreensmith.wordpress.com/2011/11/24/installing-arduino-0023-on-ubuntu-11-10-oneiric-ocelot/](http://mattgreensmith.wordpress.com/2011/11/24/installing-arduino-0023-on-ubuntu-11-10-oneiric-ocelot/)

Easy fix: find the file ```
/hardware/arduino/cores/arduino/wiring.h
``` in your arduino install location and comment out the following line (79):

```
// #define round(x)     ((x)>=0?(long)((x)+0.5):(long)((x)-0.5))
```

---


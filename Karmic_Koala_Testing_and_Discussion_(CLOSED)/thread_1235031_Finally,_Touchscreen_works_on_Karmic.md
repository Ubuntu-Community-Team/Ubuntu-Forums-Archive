---
title: "Finally, Touchscreen works on Karmic"
date: 2009-08-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by golusweet on 2009-08-08
I have HP tx1000 series,and I installed evtouch, and calibrated.

Now, It's working great.:D

0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen

For those who wanna test their touchscreens,

Check out this bug on launchpad below 

[https://bugs.edge.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317094](https://bugs.edge.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317094)

and post your results.:P

Karmic is looking great. I wish, we could have a nice audio experience this time. :D

---

### Post by vishalrao on 2009-08-09
woot! where did you install evtouch from? standard karmic repos? does everything like tap-drag etc work? in jaunty people could tap/click but not drag/move...

btw, that bug asks to follow specific steps (and to NOT install evtouch package i believe) and my tx1000 series did NOT work so i posted the required info. hopefully it will work with evdev and standard usbtouchscreen packages without requiring the unmaintained evtouch code...

see [http://idlethread.blogspot.com/2009/08/touchscreen-fail.html](http://idlethread.blogspot.com/2009/08/touchscreen-fail.html)

---

### Post by golusweet on 2009-08-09
> **vishalrao said:**
> woot! where did you install evtouch from? standard karmic repos? does everything like tap-drag etc work? in jaunty people could tap/click but not drag/move...

btw, that bug asks to follow specific steps (and to NOT install evtouch package i believe) and my tx1000 series did NOT work so i posted the required info. hopefully it will work with evdev and standard usbtouchscreen packages without requiring the unmaintained evtouch code...

see [http://idlethread.blogspot.com/2009/08/touchscreen-fail.html](http://idlethread.blogspot.com/2009/08/touchscreen-fail.html)


I installed evtouch from karmic standard repos. Nope, drag/move is not working. I have attached mine lshal output.

still an big improvement, I can right click now as well.:P

---

### Post by vishalrao on 2009-08-09
cool. but if im not mistaken the idea was to NOT install evtouch :D (too many NOTs eh?)

---

### Post by waspbr on 2009-08-16
I noticed that too,got a tx1320us myself, I was thinking that it would be cool if the touchscreen worked, so I touched it and voila, it worked, tho I noticed that the calibration needed tweaking, the calibration seemed off by a wee bit. 

I went to the calibration administration utility to calibrate, sadly that didn't work out all that well, it got stuck in a point and wouldn't go further. But hey, progress :D

---

### Post by Harper45 on 2009-08-16
yeah u r rite man...

---

### Post by andrew frank on 2009-10-08
could somebody that has right click working under karmic post his xorg.conf?
thank you!

(i have a fujitsu p1630 - the new calibration routine produces wrong values for minY - is that only on mine?)

when does evtouch read the config file?

thanks a lot for help!
andrew

---


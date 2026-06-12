---
title: "apcupsd Fails"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by milliman on 2008-10-22
Intrepid Ibex has been working great on my platform.  I even have all of the buttons working on my Logitech MediaPlay mouse.  

This morning I noticed that apcupsd was not running.  It worked perfectly under Hardy, but now the daemon stops shortly after starting.  Nothing hardware wise has changed in my system to stop it from working.  I still have the APC supplied cable connected to my first serial port (/dev/ttyS0).  When I run apctest, I received the following output:
```
2008-10-22 09:20:37 apctest 3.14.4 (18 May 2008) debian
Checking configuration ...
Attached to driver: apcsmart
sharenet.type = DISABLE
cable.type = CUSTOM_SMART

You are using a SMART cable type, so I'm entering SMART test mode
mode.type = APCSMART_UPS
Setting up the port ...
apctest FATAL ERROR in smartsetup.c at line 171
PANIC! Cannot communicate with UPS via serial port.
Please make sure the port specified on the DEVICE directive is correct,
and that your cable specification on the UPSCABLE directive is correct.
apctest error termination completed
```
I followed the procedures in the apcupsd manual for testing the serial port and it seems present and working.  Does anyone else see such problems with apcupsd or know of what may have changed in the kernel to change how the serial port interface works?

THANKS

---


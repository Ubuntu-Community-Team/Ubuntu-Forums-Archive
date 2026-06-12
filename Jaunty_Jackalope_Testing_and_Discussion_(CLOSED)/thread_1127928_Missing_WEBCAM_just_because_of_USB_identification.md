---
title: "Missing WEBCAM just because of USB identification"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by alexhguerra on 2009-04-17
Hello folks

Im running the current Jaunty and have bought a C3 TECH webcam with the usb id 093a:2620  cam chip is PAC7311 (GSPCA drivers)

the current stable pac7311.c found on [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
have this id
USB_DEVICE(0x093a, 0x2620), .driver_info = SENSOR_PAC7302

but the pac7311.c on current Jaunty kernel source code does not have it.....   the most significant change i could saw in this driver is the add of some new ids (mine is in the new bunch) 

Is there a way possible to have the gspca driver updated to the current stable one ?  or if not is there a way to override this id 093a::(with another one like id 093a:2621 that already exists in the driver?

or even maybe forcing the driver to load with the chips id im choosing?

Thanks a lot

---

### Post by alexhguerra on 2009-04-17
Any help ? :(

---

### Post by Leathal on 2009-04-17
The dev team moved the usbserial module to the kernel so the only way you could try to substitute a device ID is by passing commands at boot through menu.lst or some such.

I have a similar problem which is screwing up my broadband modem. Apparently the team realized how shortsighted their decision was, so the usbserial module SHOULD eventually be user accessible again. I'm hoping it'll be back to normal by release, but who knows?

---


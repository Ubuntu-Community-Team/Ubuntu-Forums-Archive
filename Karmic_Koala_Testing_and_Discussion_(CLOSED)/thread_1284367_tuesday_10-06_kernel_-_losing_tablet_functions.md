---
title: "tuesday 10-06 kernel - losing tablet functions"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Roger E Critchlow Jr on 2009-10-06
The Tuesday updates broke the wacom stylus on my x200 tablet.  

The eraser side of the stylus still works.  The touch sensitivity of the tablet still works.  The trackpointer still works.  But the stylus end of the stylus is no longer a pointer device.

The following still returns three devices, as shown:

% hal-find-by-property --key input.x11_driver --string wacom
/org/freedesktop/Hal/devices/pnp_WACf008_serial_platform_0
/org/freedesktop/Hal/devices/pnp_WACf008_serial_platform_0_subdev_0
/org/freedesktop/Hal/devices/pnp_WACf008_serial_platform_0_subdev

And the three devices still have the right properties:

% for udi in `hal-find-by-property --key input.x11_driver --string wacom`; do
>    type=`hal-get-property --udi $udi --key input.x11_options.Type`
>     echo $udi has type $type
>  done
/org/freedesktop/Hal/devices/pnp_WACf008_serial_platform_0 has type stylus
/org/freedesktop/Hal/devices/pnp_WACf008_serial_platform_0_subdev_0 has type touch
/org/freedesktop/Hal/devices/pnp_WACf008_serial_platform_0_subdev has type eraser

All of my patches to make the tablet work correctly haven't worked in weeks, so I have no idea which package broke this or is supposed to be fixing it.

I'd be happy to help if I knew where to apply,

-- rec --

---


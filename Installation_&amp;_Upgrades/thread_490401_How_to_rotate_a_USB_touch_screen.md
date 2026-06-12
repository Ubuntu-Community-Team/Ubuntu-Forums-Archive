---
title: "How to rotate a USB touch screen"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by ocwo92 on 2007-07-02
I have an out-of-the-box Edgy installation and an LG Electronics L1510SF touch screen.

The touch screen appears to be detected properly, and lsmod indicates that the usbtouchscreen module is loaded. In addition, I can navigate the mouse around on the screen using a stylus, so apparently something is all right.

The problem is that apparently the touch screen pointer's orientation is different from the screen output. When I move the pointer upward, instead it goes left; when I move the pointer left, instead it goes down; etc. Apparently the mouse input is rotated 90 degrees clockwise compared with the resulting mouse movement.

I'm guessing this is a simple question of configuring something somewhere, but where and how do I fix this issue? The xorg.conf doesn't provide any indications of a touch screen, except maybe three Wacom entries that I suspect won't help me.

---

### Post by arduinowsk on 2007-11-13
i have the same problem, did you get any solution for that, i see that knowone answered you! :(

---

### Post by tanheis on 2007-12-20
> **arduinowsk said:**
> i have the same problem, did you get any solution for that, i see that knowone answered you! :(

have you tried to configure xorg.conf...

There are options to add there to input device... touch screen section...

Option "SwapX" "1"
Option "SwapY" "1"

1 = on
0 = off

Option "Calibrate" "1"
this is to calibrate the touch screen..
Put # in the front of it after calibrated... I suppose it calibrates it durring the xorg startup...

#Option "Calibrate" "1"

like this you comment it out later...


Hope these helps..

---

### Post by .neo on 2008-01-27
Has anyone PLEASEEEE :( solved this problem, since I've got the same problem with the same monitor!?

I've run lsmod and noticed that beside "usbtouchscreen" module there's an "evdev" module loaded too.

As for the xorg.conf settings, what I've seen is there is only a single section active reffering to pointer devices, and that's the "Configured mouse" section which uses driver "mouse" (not "usbtouchscreen" or "evdev")... I've tried adding Option "SwapX" "1" and Option "SwapY" "1" and even Option "SwapXY" "1" (which is what I really need, since up-down moves mouse left-right and vice versa) to section "Configured mouse" but to no avail - no change in touchscreen behaviour what so ever! ANY HELP WHAT SO EVER WOULD BE GREAT, PLEASE!!!

---

### Post by geoff.l on 2008-02-16
Not sure if you are still interested after all this time ... but the correct option to use in the InputDevice Section is:

Option "Rotate" "CCW"  

or

Option "Rotate" "CW"   

depending on which way you want it to be turned.

I have the same LG screen, and in normal "Landscape" oroientation I have to use the ClockWise rotation.

---

### Post by ocwo92 on 2008-03-23
Finally, the solution:

First, install the evtouch driver:

```
sudo apt-get install xserver-xorg-input-evtouch
```

Then uncomment the entire InputDevice section in xorg.conf that specifies the regular mouse, and add the following section:

```
Section InputDevice
        Identifier "touchscreen"
        Driver "evtouch"
        Option "Device" "/dev/input/event3"
        Option "DeviceName" touchscreen"
        Option "ReportingMode" "Raw"
        Option "SendCoreEvents"
        Option "MinX" "316"
        Option "MinY" "36"
        Option "MaxX" "3791"
        Option "MaxY" "3934"
        Option "Rotate" "cw"
        Option "SwapX" "1"
        Option "SwapY" "1"
EndSection
```

You'll probably have to experiment a bit with the proper /dev/input/eventX to use; try to enter "cat /dev/input/event0", event1, event2, etc. and touch the screen to see which one produces output.

Then in the ServerLayout section, remove the reference to the mouse, and add the following line instead:

```
        InputDevice "touchscreen" "CorePointer"
```

---

### Post by pug on 2008-03-31
Since you guys seem to have it working I'll post this question here:

I have the touch screen working perfectly, however, the "pointer" skips, e.g. if I move my finger from the left to the right the pointer jumps to one place, then waits until I move my finger like an inch, then jumps to the next spot...

E.g. there's a large area of the screen I can't hit at all... anyone else have this problem?

Hardy heron beta... everything "out of the box" except config files.

---

### Post by skmakine on 2008-04-11
Option          "MoveLimit"     "5"

---


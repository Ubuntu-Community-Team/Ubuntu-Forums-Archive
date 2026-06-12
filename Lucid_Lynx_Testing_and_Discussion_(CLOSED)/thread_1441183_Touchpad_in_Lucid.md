---
title: "Touchpad in Lucid"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ragein on 2010-03-28
I have just upgraded my macbook 2,1 running karmic to Lucid and it all seems to have gone well.  I did have to boot with nomodeset for gnome to show anything but I had to do that in karmic for everything to work properly anyway.

I am having trouble with the touchpad though, it feels sluggish and at times it takes me a couple of goes for the cursor to move having done some googleing I found the following advice on the macbook 5,1 guide.

use  xinput list to find the id of the trackpad. most  like it is named 'bcm5974' then  use xinput list-props <id>  to get a list of al the  properties, the ids and the format for the value then use  xinput set-prop <id> <property id> <value>  to change things 

This is all fine and dandy but to be honest I have no idea which property I want to be changing and for that matter how much I want to vary the value it possesses. when I list the properties of my touchpad I get 

Device '"appletouch"':
    Device Enabled (162):    1
    Device Accel Profile (280):    0
    Device Accel Constant Deceleration (281):    1.000000
    Device Accel Adaptive Deceleration (283):    1.000000
    Device Accel Velocity Scaling (284):    10.000000
    Synaptics Edges (285):    103, 1112, 48, 527
    Synaptics Finger (286):    29, 35, 300
    Synaptics Tap Time (287):    180
    Synaptics Tap Move (288):    59
    Synaptics Tap Durations (289):    180, 180, 100
    Synaptics Tap FastTap (290):    0
    Synaptics Middle Button Timeout (291):    75
    Synaptics Two-Finger Pressure (292):    330
    Synaptics Two-Finger Width (293):    7
    Synaptics Scrolling Distance (294):    26, 26
    Synaptics Edge Scrolling (295):    0, 0, 0
    Synaptics Two-Finger Scrolling (296):    1, 1
    Synaptics Move Speed (297):    0.400000, 0.700000, 0.037202, 40.000000
    Synaptics Edge Motion Pressure (298):    35, 187
    Synaptics Edge Motion Speed (299):    1, 107
    Synaptics Edge Motion Always (300):    0
    Synaptics Button Scrolling (301):    1, 1
    Synaptics Button Scrolling Repeat (302):    1, 1
    Synaptics Button Scrolling Time (303):    100
    Synaptics Off (304):    1
    Synaptics Guestmouse Off (305):    0
    Synaptics Locked Drags (306):    0
    Synaptics Locked Drags Timeout (307):    5000
    Synaptics Tap Action (308):    2, 3, 0, 0, 1, 3, 2
    Synaptics Click Action (309):    1, 3, 2
    Synaptics Circular Scrolling (310):    0
    Synaptics Circular Scrolling Distance (311):    0.100000
    Synaptics Circular Scrolling Trigger (312):    0
    Synaptics Circular Pad (313):    0
    Synaptics Palm Detection (314):    0
    Synaptics Palm Dimensions (315):    10, 234
    Synaptics Coasting Speed (316):    0.000000
    Synaptics Pressure Motion (317):    35, 187
    Synaptics Pressure Motion Factor (318):    1.000000, 1.000000
    Synaptics Grab Event Device (319):    1
    Synaptics Gestures (320):    1
    Synaptics Capabilities (321):    1, 0, 0, 1, 1
    Synaptics Pad Resolution (322):    1, 1
    Synaptics Area (323):    0, 0, 0, 0
    Synaptics Jumpy Cursor Threshold (324):    0

Any ideas would be much appreciated, thanks in advance :)

---

### Post by miegiel on 2010-03-31
> **ragein said:**
> I have just upgraded my macbook 2,1 running karmic to Lucid and it all seems to have gone well.  I did have to boot with nomodeset for gnome to show anything but I had to do that in karmic for everything to work properly anyway.

I am having trouble with the touchpad though, it feels sluggish and at times it takes me a couple of goes for the cursor to move having done some googleing I found the following advice on the macbook 5,1 guide.

use  xinput list to find the id of the trackpad. most  like it is named 'bcm5974' then  use xinput list-props <id>  to get a list of al the  properties, the ids and the format for the value then use  xinput set-prop <id> <property id> <value>  to change things 

This is all fine and dandy but to be honest I have no idea which property I want to be changing and for that matter how much I want to vary the value it possesses. when I list the properties of my touchpad I get 

Device '"appletouch"':
    Device Enabled (162):    1
    Device Accel Profile (280):    0
    Device Accel Constant Deceleration (281):    1.000000
    Device Accel Adaptive Deceleration (283):    1.000000
    Device Accel Velocity Scaling (284):    10.000000
    ...

Any ideas would be much appreciated, thanks in advance :)

You checked the speed and acceleration settings under System > Settings > Mouse > Touchpad I assume.

List of synaptics device properties: [http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4](http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4)

Some examples of commands to help you with the syntax (you might want to change the device name):
```
xinput list
xinput list-props "SynPS/2 Synaptics TouchPad"
xinput test "SynPS/2 Synaptics TouchPad"
xinput test-xi2 "SynPS/2 Synaptics TouchPad"
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 250
```

It seems [this is the way]("http://ubuntuforums.org/showthread.php?p=8997937#post8997937") to apply the settings automatically  when starting up.

---


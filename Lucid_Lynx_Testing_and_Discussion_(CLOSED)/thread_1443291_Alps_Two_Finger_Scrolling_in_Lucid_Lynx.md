---
title: "Alps Two Finger Scrolling in Lucid Lynx"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by fugrank on 2010-03-30
So two finger scrolling a pretty nifty feature that isn't officially supported with alps touchpads.  It hasn't been an easy thing to get working in the incarnations of ubuntu, but I was able to get it working with both the xorg.conf and the hal methods in the past.  However, both those avenues are no longer available in 10.04.  So how can I get it working again??

Thanks

---

### Post by fugrank on 2010-04-01
Thanks to the mod who moved my post to this subforum, otherwise I would not have known it existed.

With some help from this thread:
[http://ubuntuforums.org/showthread.php?t=1435663&highlight=scroll&page=2](http://ubuntuforums.org/showthread.php?t=1435663&highlight=scroll&page=2)

```
#!/bin/bash
#
# list of synaptics device properties http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4
# list  current synaptics device properties: xinput list-props '"AlpsPS/2 ALPS GlidePoint"'
#
sleep 5 #added delay... 
xinput --set-prop --type=int --format=32 "AlpsPS/2 ALPS GlidePoint" "Synaptics Two-Finger Pressure" 125
xinput --set-prop --type=int --format=32 "AlpsPS/2 ALPS GlidePoint" "Synaptics Two-Finger Width" 0         # Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
xinput --set-prop --type=int --format=8  "AlpsPS/2 ALPS GlidePoint" "Synaptics Two-Finger Scrolling" 1 0   # vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
exit
```

Obviously the device name needed to be changed to "AlpsPS/2 ALPS GlidePoint".  Additionally, the thresholds for pressure need to be different on Alps touchpads.  And of course, there is no width reported by Alps, so the width argument needed to be set to 0.

---

### Post by yelo3 on 2010-04-01
ALPS touchpads really sucks :P

Anyway those values won't work with my touchpad. I don't know if I have to put a higher pressure value, or a lower one...

---

### Post by cscarney on 2010-04-13
This worked for my ALPS touchpad (HP dv4) on lucid:
```
synclient VertTwoFingerScroll=1
synclient EmulateTwoFingerMinW=0
synclient EmulateTwoFingerMinZ=80
```

You might have to play around with the value of EmulateTwoFingerMinZ -- if it scrolls when you want to move the mouse pointer, set it higher; if it moves the mouse pointer when you want to scroll, set it lower.

You have to do this each time you log in, so once you find settings that work for your pad, put them in a shell script somewhere and add it to your startup applications.

---

### Post by Vladimir Hidalgo on 2010-04-18
VAIO VBPCEB15EL, none of the tricks above mentioned worked out.

*synclient -l*
> Parameter settings:
    LeftEdge                = 153
    RightEdge               = 870
    TopEdge                 = 115
    BottomEdge              = 652
    FingerLow               = 12
    FingerHigh              = 14
    FingerPress             = 127
    MaxTapTime              = 180
    MaxTapMove              = 56
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 1
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 80
    EmulateTwoFingerMinW    = 0
    VertScrollDelta         = 25
    HorizScrollDelta        = 25
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 0.4
    MaxSpeed                = 1
    AccelFactor             = 0.207
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 14
    EdgeMotionMaxZ          = 79
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 102
    EdgeMotionUseAlways     = 0
    UpDownScrolling         = 1
    LeftRightScrolling      = 1
    UpDownScrollRepeat      = 1
    LeftRightScrollRepeat   = 1
    ScrollButtonRepeat      = 100
    TouchpadOff             = 1
    GuestMouseOff           = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 1
    CircularScrolling       = 0
    CircScrollDelta         = 0.01
    CircScrollTrigger       = 8
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 99
    CoastingSpeed           = 0
    PressureMotionMinZ      = 14
    PressureMotionMaxZ      = 79
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    JumpyCursorThreshold    = 0


*grep touchpad /var/log/Xorg.0.log*
> (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
(II) Synaptics touchpad driver version 1.2.2
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(--) AlpsPS/2 ALPS GlidePoint: touchpad found


Please help!

---

### Post by Vladimir Hidalgo on 2010-04-26
Link to LaunchPad bug tracker: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/565543]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/565543")

Without this feature, navigating through sites like [http://flor360.com]("http://flor360.com") is very unlike to be pleasant, aside from the fact that VAIO E series have a rugged touchpad that's hard to the fingers!

---


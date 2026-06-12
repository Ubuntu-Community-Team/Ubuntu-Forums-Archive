---
title: "Ubuntu Jaunty how to disable mouse when writing?"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mkgkg on 2009-04-07
Hi,
Under Ubuntu Jaunty how to disable mouse when writing? I tried with syndaemon but didnt work!i looked into [https://help.ubuntu.com/community/MacBook3-1/Jaunty](https://help.ubuntu.com/community/MacBook3-1/Jaunty). I have a macbook 3,1.

```
$ syndaemon -t -d
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```
this is my xorg.conf
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1" # set to 0 if you don't want horizontal scrolling
        Option          "HorizScrollDelta"      "10"
        Option          "VertScrollDelta"       "10"
        Option          "PressureMotionMinZ"    "20"
        Option          "FingerLow"             "10"
        Option          "FingerHigh"            "20" # change to 30 or 40 if you like
        Option          "LeftEdge"              "20"
        Option          "RightEdge"             "1200"
        Option          "TopEdge"               "20"
        Option          "BottomEdge"            "370"
        Option          "MinSpeed"              "0.8" # 0.5 is very slow, 1.5 is very fast
        Option          "MaxSpeed"              "1.2" # up to 1.5 works ok
        Option          "AccelFactor"           "0.10"
        Option          "MaxTapMove"            "100"
        Option          "MaxTapTime"            "100"
        Option          "MaxDoubleTapTime"      "200"
        Option          "TapButton2"            "3"
        Option          "TapButton3"            "2"
        Option          "SHMConfig"             "on"
EndSection


```

---

### Post by skiwithpete on 2009-04-08
The real question is, why hasn't this been added as a tick box under mouse settings?

---

### Post by iheartubuntu on 2009-04-08
> **skiwithpete said:**
> The real question is, why hasn't this been added as a tick box under mouse settings?

Bingo! Yup!

---


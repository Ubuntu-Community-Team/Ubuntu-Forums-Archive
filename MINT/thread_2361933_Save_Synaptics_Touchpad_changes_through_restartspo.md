---
title: "Save Synaptics Touchpad changes through restarts/poweroffs?"
date: 2017-05-22
forum: MINT
---

### Post by RallyDarkstrike on 2017-05-22
Hi all,

Tweaking my new-to-me laptop with Linux Mint 18.1. This one has  a touchpad that I had to increase the sensitivity of by running a "sudo  xinput set-prop 12 293 8, 10, 0" command.

This works, but this  setting change DOES NOT stay through restarts or poweroffs. How would I  go about setting my Synaptics settings to save this custom change  through restarts so I don't have to enter it in Terminal when I boot my  machine?

Thanks! [IMG]https://forums.linuxmint.com/images/smilies/icon_smile.gif[/IMG]

---

### Post by ajgreeny on 2017-05-22
*Thread moved to **MINT**.* which is more appropriate and a better fit.

---

### Post by vasa1 on 2017-05-22
Have you tried putting the command into an autostart file? And do you really need *sudo*?

---

### Post by RallyDarkstrike on 2017-05-22
Figured out that I don't need sudo and I did have it as Autostart. I figured out how to use synclient to set various settings and found this link:

[http://www.techrepublic.com/article/tweak-your-touchpad-to-taste-in-linux/](http://www.techrepublic.com/article/tweak-your-touchpad-to-taste-in-linux/)

...which tells me how to create a script file to readjust my settings to my preference on startup. You would think all would be well! I followed those instructions and have a script that works perfectly from Terminal by running the *~/.touchsettings* command (the file script I created is called .touchsettings to hide it from view and is located in my Documents folder of my user folder). I set it to run in AutoStart.

HOWEVER.....I can't get it to run on startup despite the AutoStart entry...? After boot I can run it again from Terminal perfectly to get it to set my settings fine, but despite the AutoStart entry, it won't run on startup. I have it entered in AutoStart with the exact same command ( *~/.touchsettings* ) but it won't run...?

Any ideas?

---

### Post by vasa1 on 2017-05-22
Have you tried the actual path instead of "~/.touchsettings"?

---

### Post by ajgreeny on 2017-05-22
Create a folder in your home called bin (/home/username/bin) and put the script in there.  A bin folder in your home is included in the $PATH variable if it exists so you could then just use the command touchsettings.

Alternatively you must use the full pathway to the script in your startup applications list, so try that as well, ie, /home/username/Documents/touchsettings

---

### Post by RallyDarkstrike on 2017-05-22
OK - didn't try the bin folder thing yet, but did put the full path to the file in the AutoStart command (i.e. */home/username/.touchsettings* ) and with that AutoStart command enabled, the touchpad ceases to function at all....lucky I have an external mouse!

If I disable that AutoStart command with the full command line, letting the laptop redetect the touchpad on startup, it works again. I can then run the ~/.touchsettings script manually in Terminal and that works fine again as well.

Stumped as to what is going on!

Will try the bin thing and see if that does anything...?

---

### Post by RallyDarkstrike on 2017-05-22
```

#!/bin/bash

xinput set-prop "AlpsPS/2 ALPS GlidePoint" "Device Accel Constant Deceleration" 2.1

synclient LeftEdge=211
synclient RightEdge=1197
synclient TopEdge=86
synclient BottomEdge=490
synclient FingerLow=7
synclient FingerHigh=10
synclient MaxTapTime=180
synclient MaxTapMove=66
synclient MaxDoubleTapTime=100
synclient SingleTapTimeout=180
synclient ClickTime=100
synclient EmulateMidButtonTime=75
synclient EmulateTwoFingerMinZ=141
synclient EmulateTwoFingerMinW=7
synclient VertScrollDelta=30
synclient HorizScrollDelta=30
synclient VertEdgeScroll=0
synclient HorizEdgeScroll=0
synclient CornerCoasting=0
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient MinSpeed=1.18
synclient MaxSpeed=4
synclient AccelFactor=0.1
synclient TouchpadOff=1
synclient LockedDrags=0
synclient LockedDragTimeout=5000
synclient RTCornerButton=2
synclient RBCornerButton=3
synclient LTCornerButton=0
synclient LBCornerButton=0
synclient TapButton1=1
synclient TapButton2=3
synclient TapButton3=2
synclient ClickFinger1=1
synclient ClickFinger2=0
synclient ClickFinger3=0
synclient CircularScrolling=0
synclient CircScrollDelta=0.1
synclient CircScrollTrigger=0
synclient CircularPad=0
synclient PalmDetect=0
synclient PalmMinWidth=10
synclient PalmMinZ=100
synclient CoastingSpeed=20
synclient CoastingFriction=50
synclient PressureMotionMinZ=15
synclient PressureMotionMaxZ=80
synclient PressureMotionMinFactor=1
synclient PressureMotionMaxFactor=1
synclient ResolutionDetect=1
synclient GrabEventDevice=0
synclient TapAndDragGesture=1
synclient AreaLeftEdge=0
synclient AreaRightEdge=0
synclient AreaTopEdge=0
synclient AreaBottomEdge=0
synclient HorizHysteresis=7
synclient VertHysteresis=7
synclient ClickPad=0
```

That is the contents of my script in case I've made any errors that I am not aware of :(

---

### Post by RallyDarkstrike on 2017-05-22
Managed to solve this tonight inadvertently with your help! I realized  that my script was running xinput and synclient commands to adjust my  touchpad on Startup but that ONLY the xinput command was working! I  replaced all the synclient commands in my script with their xinput  equivalents and all is now well, thanks so much! [IMG]https://forums.linuxmint.com/images/smilies/icon_biggrin.gif[/IMG]

---


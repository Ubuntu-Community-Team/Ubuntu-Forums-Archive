---
title: "waltop weirdness"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by icodemonkey on 2010-10-12
picking up from here [http://ubuntuforums.org/showpost.php?p=9957261&postcount=23](http://ubuntuforums.org/showpost.php?p=9957261&postcount=23)

---

### Post by Favux on 2010-10-12
Good.  Let me know when you've reinstalled the driver and the wizardpen.conf and if that did anything.

One nice thing about starting this new thread is there is a possibility we could compile a patched waltop kernel driver for Maverick that would actually work with wacom X driver.  Like I said there are patches to fix it.  I maybe know enough to help compile it.  We just need an experienced linux user, who hopefully knows more than me, and also has a Waltop tablet to see if it is possible.

---

### Post by icodemonkey on 2010-10-12
well that didnt work still thinks the tip is pressed (as seen in screenshot)
should i remove the wacom driver?

---

### Post by Favux on 2010-10-12
What we really need to see is the list-props command again to see what driver is claiming the tablet.  The wacom driver shouldn't be doing anything.

I'll also need to see your wizardpen.conf and Xorg.0.log in /var/log.

Oh wait a minute!!  You're in Maverick.  Slap forehead.  They changed the location of the xorg.conf.d .conf files from Lucid.  Add the modified 70-wizardpen.conf to /usr/share/X11/xorg.conf.d:
```
gksudo gedit /usr/share/X11/xorg.conf.d/70-wizardpen.conf
```
You might want to check first and see if the wizardpen.conf is there and is still numbered 70.

---

### Post by icodemonkey on 2010-10-12
> **Favux said:**
> What we really need to see is the list-props command again to see what driver is claiming the tablet.  The wacom driver shouldn't be doing anything.

I'll also need to see your wizardpen.conf and Xorg.0.log in /var/log.

Oh wait a minute!!  You're in Maverick.  Slap forehead.  They changed the location of the xorg.conf.d .conf files from Lucid.  Add the modified 70-wizardpen.conf to /usr/share/X11/xorg.conf.d:
```
gksudo gedit /usr/share/X11/xorg.conf.d/70-wizardpen.conf
```You might want to check first and see if the wizardpen.conf is there and is still numbered 70.

list-props
```
Device 'WALTOP International Corp. Slim Tablet':
    Device Enabled (134):    1
    Coordinate Transformation Matrix (136):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (267):    0
    Device Accel Constant Deceleration (268):    1.000000
    Device Accel Adaptive Deceleration (269):    1.000000
    Device Accel Velocity Scaling (270):    10.000000
    Evdev Reopen Attempts (251):    10
    Evdev Axis Inversion (271):    0, 0
    Evdev Axis Calibration (272):    <no items>
    Evdev Axes Swap (273):    0
    Axis Labels (274):    "Abs X" (254), "Abs Y" (255), "Abs Pressure" (286), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
    Button Labels (275):    "Button Left" (137), "Button Middle" (138), "Button Right" (139), "Button Wheel Up" (140), "Button Wheel Down" (141), "Button Horiz Wheel Left" (142), "Button Horiz Wheel Right" (143), "Button Side" (284), "Button Extra" (285), "Button Unknown" (252), "Button Unknown" (252), "Button Unknown" (252), "Button Unknown" (252)
    Evdev Middle Button Emulation (276):    2
    Evdev Middle Button Timeout (277):    50
    Evdev Wheel Emulation (278):    0
    Evdev Wheel Emulation Axes (279):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (280):    10
    Evdev Wheel Emulation Timeout (281):    200
    Evdev Wheel Emulation Button (282):    4
    Evdev Drag Lock Buttons (283):    0
```

your 70-wizardpen.conf
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
#        Option  "TopX"  "775"
#        Option  "TopY"  "726"
#        Option  "BottomX"  "19237"
#        Option  "BottomY"  "11614"
#        Option  "TopZ"  "20"  # minimum pressure, default is 20
#        Option  "BottomZ"  "1023"  # maximum pressure
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```

attached is the Xorg.0.log

---

### Post by Favux on 2010-10-12
Hi icodemonkey,

And all of this was before putting the wizardpen.conf in the correct location?

---

### Post by icodemonkey on 2010-10-12
no wizardpen was in right place ie /usr/lib/X11/xorg.conf.d/70-wizardpen.conf
content before your .conf
```

Section "InputClass"
   Identifier      "wizardpen"
   MatchIsTablet   "on"
   MatchDevicePath "/dev/input/event*"
   MatchTag        "wizardpen"
   Driver          "wizardpen"
EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchDevicePath "/dev/input/mouse*"
   MatchTag        "wizardpen"
   Driver          "mouse"
   Option          "MouseSpeed" "16"
   Option          "ignore"     "true"
EndSection

```

---

### Post by Favux on 2010-10-12
Nope, that's the right place for Lucid not Maverick.

```
Lucid
gksudo gedit /usr/lib/X11/xorg.conf.d/70-wizardpen.conf

Maverick
gksudo gedit /usr/share/X11/xorg.conf.d/70-wizardpen.conf
```
The file should have been empty when you used the "gksudo gedit etc." command.  When in fact there should have been content.

---

### Post by icodemonkey on 2010-10-12
alright it works

---

### Post by Favux on 2010-10-12
Boy, I hope so.  We still might want to look at list-props to see if we can fine tune it.

Unless they renumbered the wizardpen.conf.  That's why I want you to check on it before using the edit command.  Check with Places (Nautilus) that it's there and has 70 as the number.  Otherwise use the number it has.

---

### Post by icodemonkey on 2010-10-12
> **Favux said:**
> Boy, I hope so.  We still might want to look at list-props to see if we can fine tune it.

Unless they renumbered the wizardpen.conf.  That's why I want you to check on it before using the edit command.  Check with Places (Nautilus) that it's there and has 70 as the number.  Otherwise use the number it has.
it has a 70- in front and if i change that to say a 50- i get no joy but if it stays as 70- then no worries plus works better now then in vista

---

### Post by Favux on 2010-10-12
Outstanding!  :)  Thanks for the number info.  That's what determines the order the .conf files are executed in, as I'm sure you realized.

Can you give me the list-props output so I can eyeball it?

---

### Post by Favux on 2010-10-12
For folks following this thread this is the 70-wizardpen.conf we've modified for the Waltop tablets:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
#        Option  "TopX"  "775"
#        Option  "TopY"  "726"
#        Option  "BottomX"  "19237"
#        Option  "BottomY"  "11614"
#        Option  "TopZ"  "20"  # minimum pressure, default is 20
#        Option  "BottomZ"  "1023"  # maximum pressure
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```

---

### Post by icodemonkey on 2010-10-12
> **Favux said:**
> Outstanding!  :)  Thanks for the number info.  That's what determines the order the .conf files are executed in, as I'm sure you realized.

Can you give me the list-props output so I can eyeball it?

eyeballs away
```
Device 'WALTOP International Corp. Slim Tablet':
    Device Enabled (134):    1
    Coordinate Transformation Matrix (136):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (267):    0
    Device Accel Constant Deceleration (268):    1.000000
    Device Accel Adaptive Deceleration (269):    1.000000
    Device Accel Velocity Scaling (270):    10.000000

```remember folks the file HAS to be in /usr/share/X11/xorg.conf.d/ or it wont work

---

### Post by keevee09 on 2010-10-12
Wow, thanks! I'm changing from 9.10 to 10.10 and the lack of a working tablet was slowing the shift.
Both buttons work (separately!) in Gimp and the smooth speed is impressive.

One Q?: is there a configuration utility to adjust pressure like with wacomcmpl? It was handy to keep open on a second workspace to adjust pressure settings quickly to suit different brushes.

Thank you both icedmonkey and Favux again for a clear (SOLVED!) thread
:guitar:

---

### Post by Favux on 2010-10-12
Hi keevee09,

Pressure is one of the things I was hoping to find out about in the list-props.

You could try adding back in:
```
#        Option  "TopZ"  "20"  # minimum pressure, default is 20
#        Option  "BottomZ"  "1023"  # maximum pressure

```
by removing the comments (#).  If your Waltop tablet has 1024 pressure levels.  Then repeat the list-props command and see if something new pops up.  The other thing to check is to see if there is a WizardPen manual.  In a terminal:
```
man wizardpen
```
Post it if there is.

No configuration utility.  Unfortunately wacomcpl went away for wacom tablets in Lucid, and is no more.  :(  So even Wacom lacks a configuration utility at this point.

---

### Post by keevee09 on 2010-10-13
Hi Favux,
Below is the manpage for wizardpen:
The pressure is at a nice setting (under 9.10 with wacom driver it was a little to weak on default) but the Top/Bottom X/Y settings will need adjusting to reach the corners of my screen correctly.... ....just found wizard-calibrate using TAB (autocomplete) in the terminal it requires an event-device

sudo wizardpen-calibrate /dev/input/event0

This should set the screen edges but pressing the corners activates the Trash/Desktop/Application menu etc so I will try uncommenting the TopX etc 
using

sudo gedit /usr/share/X11/xorg.conf.d/70-wizardpen.conf

thanks,
keevee09

THE MANPAGE FOR WIZARDPEN:

                                                     WizardPen(4)

NAME
       wizarpen - WizardPen tablet input driver

SYNOPSIS
       Section "InputDevice"
         Identifier "Tablet"
         Driver "wizardpen"
         Option "Device"   "devpath"
         ...
       EndSection
         ...
       Section "ServerLayout"
         ...
         InputDevice  "Tablet"
         ...
       EndSection

DESCRIPTION
       wizardpen is an Xorg input driver for WizardPen Tablet devices...

       The  wizardpen  driver  functions as a pointer input device, and may be
       used as the X server's core pointer.  THIS MAN PAGE NEEDS TO BE  FILLED
       IN.

SUPPORTED HARDWARE
       What is supported...
       WizardPen tablets

CONFIGURATION DETAILS
       Please  refer to xorg.conf(5) for general configuration details and for
       options that can be used with all input  drivers.   This  section  only
       covers configuration details specific to this driver.

       Option "TopX"  "val"
       Allows the use of an alternative left edge location.

       val should be equal to the x value of the new left edge

       Option "TopY"  "val"
       Allows the use of an alternative top edge location.

       val should be equal to the y value of the new top edge

       Option "TopZ"  "val"
       Allows the use of an alternative minimum pressure.

       val should be equal to the value of the new minimum pressure

       Option "BottomX"    "val"
       Allows the use of an alternative right edge location.

       val should be equal to the x value of the new right edge
       
       Option "BottomY"    "val"
       Allows the use of an alternative bottom edge location.

       val should be equal to the y value of the new bottom edge

       Option "BottomZ"    "val"
       Allows the use of an alternative maximum pressure.

       val should be equal to the value of the new maximum pressure

SEE ALSO
       Xorg(1), xorg.conf(5), xorgconfig(1), Xserver(1), X(7).

AUTHORS
       Authors include...  Edouard TISSERANT Zachary Cornelius

X Version 11                    wizardpen 0.7.4                   WizardPen(4)

---

### Post by Favux on 2010-10-13
A calibrator is a nice feature.  From the manual it doesn't look like there are too many parameters to play with.

You can look at 'man xinput'.  There are a few parameters that may be applicable:
>        xinput get-feedbacks device_name
               Display  the  feedbacks  of  device_name. Uses XGetFeedbackCon&#8208;
               trol(3).

       xinput set-pointer device_name
               Switch device_name  in  core  pointer.  Uses  XChangePointerDe&#8208;
               vice(3).

       xinput set-mode device_name ABSOLUTE|RELATIVE
               Change the mode of device_name. Uses XSetDeviceMode(3).

       xinput set-ptr-feedback device_name threshold num denom
               Change  the  acceleration of device_name. Uses XChangeFeedback&#8208;
               Control(3).

       xinput set-integer-feedback device_name index value
               Change the value of an integer feedback  of  device_name.  Uses
               XChangeFeedbackControl(3).

       xinput set-button-map device_name map button 1 [map button 2 [...]]
               Change  the  button mapping of device_name. Uses XSetDeviceBut&#8208;
               tonMapping(3).

       xinput set-int-prop device_name property format value
               Sets an integer property for the  device.   Appropriate  values
               for format are 8, 16, or 32, depending on the property.

       xinput test [-proximity] device_name
               Register all extended events from device_name and enter an end&#8208;
               less loop displaying events  received.  If  the  -proximity  is
               given, ProximityIn and ProximityOut are registered.

Depends on how the driver interacts I'd suspect.  It would require a fair amount of experimentation.  And I could always ask too.  ;)

---

### Post by keevee09 on 2010-10-13
Correction:
sudo wizardpen-calibrate /dev/input/by-id/usb-WALTOP_International_Corp._Slim_Tablet-event-mouse

'worked' but the output gave Top/Bottom values for X/Y that didn't work:(

The original values didn't either :)

I've rebooted after commenting out the OPTIONS in 
/usr/share/X11/xorg.conf.d/70-wizardpen.conf and it is working again.

It must be getting screen area from xinput yes?

I'll play around with xinput and its options and get back with any joy/sorrow.

At this stage though I'm very happy with the results achieved by you and icodemonkey. I'm just curious to know if it can further tuned.

---

### Post by keevee09 on 2010-10-13
So here are some details from xinput:

from terminal: xinput get-feedbacks "WALTOP International Corp. Slim Tablet"
1 feedback class
PtrFeedbackClass id=0
	accelNum is 2
	accelDenom is 1
	threshold is 4

from terminal: xinput list-props "WALTOP International Corp. Slim Tablet"
Device 'WALTOP International Corp. Slim Tablet':
	Device Enabled (147):	1
	Coordinate Transformation Matrix (149):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (265):	0
	Device Accel Constant Deceleration (266):	1.000000
	Device Accel Adaptive Deceleration (267):	1.000000
	Device Accel Velocity Scaling (268):	10.000000

I ran: xinput test "WALTOP International Corp. Slim Tablet" > tablet_feedback.txt

The text file was quite long :) but scrolling through I found it gave max/min values for 
                   a[0] of 9496/500      # x values I guess
                   a[1] of 5932/312      # y values
                   a[2] of 1023/0        # z values - pressure

---

### Post by icodemonkey on 2010-10-13
i just use the tool dialogue in gimp to adjust the pressure work well IMHO but as with all advice YMMV

---

### Post by keevee09 on 2010-10-13
Yep, and MyPaint has a useful control too. I've just got stuck in my ways but made use of Gimp's pressure setting yesterday, although it doesn't seem to have the range I could achieve with the wacomcmpl slider - it could be my inexperience though 
:)
PS - G'day from the Land Down Under The Land Down Under ;)

---

### Post by Favux on 2010-10-13
Hi guys,

I'm busy pulling out what look like the available Options from the source code.

You're right, Wacom uses a bezier curve (0,0,100,100) which offers more nuanced pressure settings.


Edit:  I have them in my new Waltop HOW TO:  [http://ubuntuforums.org/showpost.php?p=9966110&postcount=1](http://ubuntuforums.org/showpost.php?p=9966110&postcount=1)

---

### Post by Favux on 2010-10-24
Hi icodemonkey, keevee09, and everyone,

It looks like the Waltop tablet now works on the wacom driver in Maverick.  See the [Waltop HOW TO]("http://ubuntuforums.org/showpost.php?p=9966110&postcount=1").  That will let you use the more sophisticated wacom bezier pressure curve and other xsetwacom commands for your stylus.

---

### Post by icodemonkey on 2010-10-25
> **Favux said:**
> Hi icodemonkey, keevee09, and everyone,

It looks like the Waltop tablet now works on the wacom driver in Maverick.  See the [Waltop HOW TO]("http://ubuntuforums.org/showpost.php?p=9966110&postcount=1").  That will let you use the more sophisticated wacom bezier pressure curve and other xsetwacom commands for your stylus.

just giving some feedback on the new wacom / waltop snippet.

all features work, pen tracking is smoother and more accurate then with wizardpen.

---

### Post by Favux on 2010-10-25
Great!  I really appreciate the feedback.  :)

---

### Post by keevee09 on 2010-11-05
Great news! Thank you. I've been working 12 hour days, weekends included for the last 6 weeks so haven't had much time to check forums etc. I'll look at installing and testing the driver tonight.

---

### Post by keevee09 on 2010-11-15
Hi Favux, icodemonkey and all,
I've got the wacom driver working but the toggle button is now only reading as a single button :( I'm sure it was working for both until I installed the KDE desktop. It's not a huge problem but both buttons were useful in MYPaint - '2' moved the picture and '3' selected the colour history.
The tip is definitely smoother with the bezier curve however.

---

### Post by Favux on 2010-11-15
Hi keevee09,

> I've got the wacom driver working...The tip is definitely smoother with the bezier curve however. 
Good.

I'm ready to believe going from the Gnome Desktop to KDE affects the stylus buttons, but I'm not sure how.  If the driver doesn't work I haven't had much luck trying xinput button mapping for stylus buttons (as opposed to mouse buttons).

---

### Post by icodemonkey on 2010-11-16
> **keevee09 said:**
> Hi Favux, icodemonkey and all,
I've got the wacom driver working but the toggle button is now only reading as a single button :( I'm sure it was working for both until I installed the KDE desktop. It's not a huge problem but both buttons were useful in MYPaint - '2' moved the picture and '3' selected the colour history.
The tip is definitely smoother with the bezier curve however.

yeah the toggle button does default to functioning as a single button. But don't worry you get used it very quickly.

hey Favux any ideas on how we get the rocker switch showing up as two separate buttons?

---

### Post by keevee09 on 2010-11-24
There was mention of QT libraries messing up the buttons on the KDE forums (sorry, I can't quote the address)
But here is a very interesting blog at the coal-face so to speak:

[http://who-t.blogspot.com/2010/09/wacom-support-in-linux.html](http://who-t.blogspot.com/2010/09/wacom-support-in-linux.html)

Reading down I see there is a repository for a configuration gui:

[http://gtk-apps.org/content/show.php?content=104309](http://gtk-apps.org/content/show.php?content=104309)

Just tried it and it doesn't recognise my Waltop. Perhaps if I reboot...

---

### Post by VinzC on 2011-01-08
Hi folks.

First off thanks for your investigations on Waltop tablets. I am running Gentoo Linux and this is here that I found the most relevant information about this tablet. Thanks to your tips, I've finally got it to work. Just note I've had to switch to Xorg server 1.9 and update all my input drivers but that was worth the effort.

Now I still have a few issues. It looks like the buttons on the stylus first send a simple click event before any other event. So when I use the stylus buttons in Gimp (say the selected tool is the brush) I first get a dot (a "paint" event in Gimp) on the canvas then a middle click event (lower button pressed). In short, I can drag the canvas using the lower button, for instance, but I get a painted dot on the canvas beforehand. My main concern is that Gimp cannot undo that particular "paint" action (it doesn't appear i the Undo stack), making the buttons useless.

So is there a fix for that or have I missed something? I'd also like to know if there's a way to use the wheels on the tablet as well as the shortcut places (K1-K34).

My WALTOP tablet is a TB-7300. I'm using kernel **2.6.37** and *xf86-input-wacom* is version **0.10.8**. Both kernel modules **wacom.ko** and **hid_waltop.ko** are loaded.

Thanks for any hint/suggestion.

---

### Post by Favux on 2011-01-09
Hi VinzC,

That's a little disappointing.  I was hoping that the 2.6.37 kernel had Nikolai Kondrashov's patches to hid_waltop.c in it and that would make it work better with the wacom driver.  If they're there it sounds like some work has to be done on xf86-input-wacom too.

We can try and see what's going on.  Use:
```
xinput --list
```
in a terminal and look at its output to find the "Device name" of your stylus.  Then enter in a terminal:
```
xinput list-props "Device name"
```
and lets see what properties the Xserver says are available.
> I'd also like to know if there's a way to use the wheels on the tablet as well as the shortcut places (K1-K34).
That isn't supported by the wacom driver.  There was someone who did preliminary work on it and said it didn't look too hard to support.  I think he was getting values with xxd or evtest.  But after he said he was diving into it he never reported back.  This was 2 to 3 months ago I think.

---

### Post by VinzC on 2011-01-10
Thanks a lot Favux. Here's the info:
```
~ $ xinput list-props "WALTOP International Corp. Media Tablet stylus"
Device 'WALTOP International Corp. Media Tablet stylus':
	Device Enabled (137):	1
	Coordinate Transformation Matrix (139):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (259):	0
	Device Accel Constant Deceleration (260):	1.000000
	Device Accel Adaptive Deceleration (261):	1.000000
	Device Accel Velocity Scaling (262):	10.000000
	Wacom Tablet Area (269):	0, 0, 16383, 16383
	Wacom Rotation (270):	0
	Wacom Pressurecurve (271):	0, 0, 100, 100
	Wacom Serial IDs (272):	1280, 0, 2, 0
	Wacom TwinView Resolution (273):	0, 0, 0, 0
	Wacom Display Options (274):	-1, 0, 1
	Wacom Screen Area (275):	0, 0, 1920, 1080
	Wacom Proximity Threshold (276):	42
	Wacom Capacity (277):	-1
	Wacom Pressure Threshold (278):	27
	Wacom Sample and Suppress (279):	2, 4
	Wacom Enable Touch (280):	0
	Wacom Hover Click (281):	1
	Wacom Enable Touch Gesture (282):	0
	Wacom Touch Gesture Parameters (283):	50, 20, 250
	Wacom Tool Type (284):	"STYLUS" (258)
	Wacom Button Actions (285):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
```
My Trust tablet is hence seen as a "*WALTOP International Corp. Media Tablet stylus*"

As for the wheels, the wheels worked when the HID generic driver was catching the event. Just that I could only use them as a regular mouse wheel; the tablet's scroll/zoom selectors were ignored, of course. I thought if the hid_waltop kernel driver could also "hook" into **/dev/input/mice** that'd be a nice start. But I'm no kernel specialist.

---

### Post by Favux on 2011-01-10
It looks like the stylus buttons are on the Wacom driver like you would expect.  So I don't think we'll be able to modify them with xinput.  But you could take a look at it.

From 'man xinput':
>        --set-button-map device map_button_1 [map_button_2 [...]]
               Change  the button mapping of device. The buttons are specified in physical order (starting with button 1) and are mapped to the logical button provided. 0 disables a button. The default button mapping for a device is
               1 2 3 4 5 6 etc.

This described on the WizardPen wiki in the "Configuring the buttons on the pen" section:  [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)
> xinput set-button-map "WizardPen Tablet" 1 3 2
We've tried this a couple of times and it doesn't seem to work.  Probably because the Wacom driver has control.  But I've wondered if the Wacom driver isn't internally reassigning the buttons, so that say 2 & 3 are being seen by it as 5 & 6 or something and that's why it hasn't worked.

Do you see a signal/keycode in xev with the scroll wheels or tablet buttons?  If Wacom was seeing your tablet buttons you'd have a line in the 'xinput --list' output with something like:
> "WALTOP International Corp. Media Tablet pad"
in it.  Wacom calls tablet buttons 'pad'.

---

### Post by VinzC on 2011-01-13
Sorry for the long delay; I have been busy at something else in the meantime.

I only have the "stylus" item in **xinput --list**:
```
$ xinput --list | grep WALTOP
&#9116;   &#8627; WALTOP International Corp. Media Tablet stylus	id=15	[slave  pointer  (2)]
```
As you can see: no "pad" :( .

Here's the current button map:
```
$ xinput get-button-map "WALTOP International Corp. Media Tablet stylus"
1 3 2 4 5 6 7 8 9
```
To fix my parasitic "tap" event I've tried to zero all buttons 3-9 but in vain:
```
$ xinput set-button-map "WALTOP International Corp. Media Tablet stylus" 1 3 0 0 0 0 0 0 0
```

However I'm not sure it can be fixed that way as I'm almost certain it's a bug. Here's what happens exactly when I use the pen buttons over my Xfce background (i.e. over the desktop area). If I press the lower button long enough, Xfce desktop context menu appears but when I close the context menu (pressing the ESC key) I can see the rectangular selection box too, as if I had pressed the pen (at the same time!) onto the background to select icons.

I haven't been able to get rid of that parasitic "tap" or "click" whatever it is called. Hence I can't use the pen button in Gimp either, otherwise I paint a dot and that action cannot be undone.

> **Favux said:**
> Do you see a signal/keycode in xev with the scroll wheels or tablet buttons?
No, I don't :( .

Is it hopeless, doctor?

---

### Post by VinzC on 2011-01-16
Hi Favux.

Hi have checked my tablet under Windows and I now can tell the parasitic "click" event that I see under Linux is not a driver bug. It also occurs under Windows: when I press the bottom pen button [over Windows' desktop], the context menu is displayed but as soon as it's closed the selection box also appears, exactly like what I'm experiencing under Linux.

The trick is when I run Gimp there's not paint event sent. When I press the bottom pen button in Gimp under Windows, only Gimp's context menu is shown and nothing is painted on the canvas. I don't know what needs to be concluded upon this but I'm really puzzled and annoyed.

[rant]In the end, I'd rather pay 300 euros for a Cintiq (just an example), which I know is or will be supported instead of a low-price lambda hardware... Lesson learnt.[/rant]

---

### Post by Favux on 2011-01-16
Hi VinzC,

Nice work.  Verifying the hardware in Windows was on the check list.

It could just be a defective stylus with a short somewhere.  Can you get a hold of another one to test?  I've forgotten if the Waltop stylus uses a battery.
> The trick is when I run Gimp there's not paint event sent. When I press the bottom pen button in Gimp under Windows, only Gimp's context menu is shown and nothing is painted on the canvas. I don't know what needs to be concluded upon this but I'm really puzzled and annoyed.
Not sure what to make of that.  Are you saying in Windows the two stylus buttons behave differently, like they are suppose to, unlike in linux on the Wacom driver?

---

### Post by VinzC on 2011-01-17
> **Favux said:**
> It could just be a defective stylus with a short somewhere.

Ow, I hope not... It's just a brand new tablet :D . If I wanted to be refunded, I'm afraid it's too late (the seven days trial period is history now :() .

> **Favux said:**
> Can you get a hold of another one to test?  I've forgotten if the Waltop stylus uses a battery.

Unfortunately no, I can't. The stylus uses a battery. It's also a brand new battery (it was shipped with the box). Maybe I could just try with another battery.

> **Favux said:**
> Not sure what to make of that.  Are you saying in Windows the two stylus buttons behave differently, like they are suppose to, unlike in linux on the Wacom driver?

I wouldn't say they behave differently in Linux than in Windows. Now I could check that, I think the buttons send the same events that the Windows driver seems to be able to filter (or is it the applet that runs in the tray?) but there's still that parasitic event that Gimp seems to discard when it runs in Windows.

If we talk about mouse clicks, the bottom button (which is supposed to send the equivalent of a right click through the setup) sends both a right and a left click events at the same time. That happens in Linux and Windows, just that it seems it's less of a problem in Windows.

---

### Post by VinzC on 2011-01-17
I'm sorry, I must rectify myself: you *can* use the left *and* right buttons to select icons on a Windows desktop so what I exposed previously was just **plain wrong** as far as Windows is concerned. So yes, the driver behaves as expected under Windows and incorrectly under Linux.

Now I have changed the battery in the pen and the issue remains. [Now when I think of it, having a battery in the stylus... wtf? :D]

---


---
title: "Touchpad Issues after new lucid wubi installation from daily iso"
date: 2010-04-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by josephdaniel on 2010-04-04
Hi,

I have just installed lucid 32bit daily build using wubi on a Dell Latitude E6400. My touchpad previously had worked out of the box including vertical scrolling and I had the option to manipulate its settings from the touchpad tab in System>Preferences>Mouse.

However, after this lucid installation I no longer has the touchpad tab and scrolling don't work. Trying to execute syndaemon from a terminal gives me the error: "Unable to find a synaptics device." I also tried installing the package gpointing-device-settings and restarting but it made no difference.

Could somebody guide me to what I should try to get scrolling working as well as changing other touchpad settings?

Thanks in advance,
Joseph

---

### Post by miegiel on 2010-04-04
> **josephdaniel said:**
> Hi,

I have just installed lucid 32bit daily build using wubi on a Dell Latitude E6400. My touchpad previously had worked out of the box including vertical scrolling and I had the option to manipulate its settings from the touchpad tab in System>Preferences>Mouse.

However, after this lucid installation I no longer has the touchpad tab and scrolling don't work. Trying to execute syndaemon from a terminal gives me the error: "Unable to find a synaptics device." I also tried installing the package gpointing-device-settings and restarting but it made no difference.

Could somebody guide me to what I should try to get scrolling working as well as changing other touchpad settings?

Thanks in advance,
Joseph

[This]("http://ubuntuforums.org/showthread.php?t=1419833") is a method to _simulate_ two finger scrolling, you can use it as a temporary workaround.

---

### Post by josephdaniel on 2010-04-05
Thanks for your help but unfortunately this didn't work.

running any of the instructed commands fails with the following error

> unable to find device "SynPS/2 Synaptics TouchPad"

I tried checking the name of my device through running "xinput list" and I got the following output:

> &#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 ALPS DualPoint TouchPad            	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HID 413c:8157                           	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=14	[slave  keyboard (3)]

So I tried changing the device name in the command to "PS/2 ALPS DualPoint TouchPad" but still I get the error

> unable to find device "PS/2 ALPS DualPoint TouchPad"

I am no expert so please instruct me if I am doing something wrong.

Joe

---

### Post by miegiel on 2010-04-05
> **josephdaniel said:**
> Thanks for your help but unfortunately this didn't work.

running any of the instructed commands fails with the following error



I tried checking the name of my device through running "xinput list" and I got the following output:



So I tried changing the device name in the command to "PS/2 ALPS DualPoint TouchPad" but still I get the error



I am no expert so please instruct me if I am **doing something wrong**.

Joe

For starters ;) Put code in code boxes not in quote boxes (the **#** button at the top of the post editor). Not that is really matters in your post, but code boxes have a max width and length and prevent smilies in the code.
> :KS:popcorn::guitar::mad::lolflag::p;)
```
:KS:popcorn::guitar::mad::lolflag::p;)
```

Now the "real" problem. Some time last month the way devices are passed onto *xinput* has changed. Make sure you wrote the device name as *[COLOR="red"]"[/COLOR]PS/2 ALPS DualPoint TouchPad[COLOR="red"]"[/COLOR]* and not as *[COLOR="red"]'"[/COLOR]PS/2 ALPS DualPoint TouchPad[COLOR="red"]"'[/COLOR]*.

Also, judging by the name of your touchpad, it seems to be a real multi-touch-pad. So you might have a bug that needs to be splat. You can still use this simulation method, but true multitouch does work better than the simulation. Keep an eye on *System>Preferences>Mouse* and if the two finger scrolling setting reappears turn off the 2 finger simulation. And of course see if there is a bug report for your touchpad.

2 typos and 1 correct as an example:
```
user@machine:~$ xinput list-props "SynPS/2 Synaptics TouchP[COLOR="Red"]a"[/COLOR]
unable to find device SynPS/2 Synaptics TouchP[COLOR="red"]a[/COLOR]

user@machine:~$ xinput list-props [COLOR="Red"]'"S[/COLOR]ynPS/2 Synaptics TouchPa[COLOR="red"]d"'[/COLOR]
unable to find device [COLOR="red"]"S[/COLOR]ynPS/2 Synaptics TouchPa[COLOR="red"]d"[/COLOR]

user@machine:~$ xinput list-props "SynPS/2 Synaptics TouchPad"
Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (145):	1
	Device Accel Profile (261):	0
	Device Accel Constant Deceleration (262):	1.000000
	Device Accel Adaptive Deceleration (264):	1.000000
	Device Accel Velocity Scaling (265):	10.000000
	Synaptics Edges (266):	1752, 5192, 1620, 4236
	Synaptics Finger (267):	24, 29, 255
	Synaptics Tap Time (268):	180
	Synaptics Tap Move (269):	221
	Synaptics Tap Durations (270):	180, 180, 100
	Synaptics Tap FastTap (271):	0
	Synaptics Middle Button Timeout (272):	75
	Synaptics Two-Finger Pressure (273):	4
	Synaptics Two-Finger Width (274):	8
	Synaptics Scrolling Distance (275):	100, 100
	Synaptics Edge Scrolling (276):	0, 0, 0
	Synaptics Two-Finger Scrolling (277):	1, 0
	Synaptics Move Speed (278):	0.400000, 0.700000, 0.009952, 40.000000
	Synaptics Edge Motion Pressure (279):	29, 159
	Synaptics Edge Motion Speed (280):	1, 401
	Synaptics Edge Motion Always (281):	0
	Synaptics Button Scrolling (282):	1, 1
	Synaptics Button Scrolling Repeat (283):	1, 1
	Synaptics Button Scrolling Time (284):	100
	Synaptics Off (285):	0
	Synaptics Guestmouse Off (286):	0
	Synaptics Locked Drags (287):	0
	Synaptics Locked Drags Timeout (288):	5000
	Synaptics Tap Action (289):	0, 0, 0, 0, 2, 8, 0
	Synaptics Click Action (290):	1, 1, 1
	Synaptics Circular Scrolling (291):	0
	Synaptics Circular Scrolling Distance (292):	0.100000
	Synaptics Circular Scrolling Trigger (293):	0
	Synaptics Circular Pad (294):	0
	Synaptics Palm Detection (295):	0
	Synaptics Palm Dimensions (296):	10, 199
	Synaptics Coasting Speed (297):	0.000000
	Synaptics Pressure Motion (298):	29, 159
	Synaptics Pressure Motion Factor (299):	1.000000, 1.000000
	Synaptics Grab Event Device (300):	1
	Synaptics Gestures (301):	1
	Synaptics Capabilities (302):	1, 1, 1, 0, 0
	Synaptics Pad Resolution (303):	124, 76
	Synaptics Area (304):	0, 0, 0, 0
	Synaptics Jumpy Cursor Threshold (305):	250
```

---


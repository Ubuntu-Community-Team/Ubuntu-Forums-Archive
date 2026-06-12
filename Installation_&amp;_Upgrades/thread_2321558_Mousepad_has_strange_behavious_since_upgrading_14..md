---
title: "Mousepad has strange behavious since upgrading 14.04 to 16.04"
date: 2016-04-23
forum: Installation &amp; Upgrades
---

### Post by neu2buntu on 2016-04-23
Hi, I decided to do a distribution upgrade from 14.04 to 16.04 and everything seems to have went smoothly except for 2 finger mousepad control.
Before I upgraded the mousepad was working perfectly, now I seem to have 2 bugs :-

(1) The pointer will random jump to the bottom left of the screen when clicking or trying to scroll and click in any program.

(2) The mousepad will only work if I time my 2 fingers to make contact on the mousepad at the exact same time or strangely with the right side of the pad being contacted 1st, but the scrolling action loses focus again if the right side contact finger is lifted off.

This is on my HP Pavilion 15 notebook. thanks :)

Output from xinput --list-props 11  ( 11 is the ID of my touchpad )

```
Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (142):	1
	Coordinate Transformation Matrix (144):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (268):	1
	Device Accel Constant Deceleration (269):	2.500000
	Device Accel Adaptive Deceleration (270):	1.000000
	Device Accel Velocity Scaling (271):	12.500000
	Synaptics Edges (272):	1629, 5353, 1445, 4467
	Synaptics Finger (273):	25, 30, 0
	Synaptics Tap Time (274):	180
	Synaptics Tap Move (275):	245
	Synaptics Tap Durations (276):	180, 100, 100
	Synaptics ClickPad (277):	1
	Synaptics Middle Button Timeout (278):	0
	Synaptics Two-Finger Pressure (279):	282
	Synaptics Two-Finger Width (280):	7
	Synaptics Scrolling Distance (281):	111, 111
	Synaptics Edge Scrolling (282):	1, 1, 0
	Synaptics Two-Finger Scrolling (283):	0, 0
	Synaptics Move Speed (284):	1.000000, 1.750000, 0.035874, 0.000000
	Synaptics Off (285):	2
	Synaptics Locked Drags (286):	0
	Synaptics Locked Drags Timeout (287):	5000
	Synaptics Tap Action (288):	2, 3, 0, 0, 1, 3, 0
	Synaptics Click Action (289):	1, 3, 0
	Synaptics Circular Scrolling (290):	0
	Synaptics Circular Scrolling Distance (291):	0.100000
	Synaptics Circular Scrolling Trigger (292):	0
	Synaptics Circular Pad (293):	0
	Synaptics Palm Detection (294):	0
	Synaptics Palm Dimensions (295):	10, 200
	Synaptics Coasting Speed (296):	20.000000, 50.000000
	Synaptics Pressure Motion (297):	30, 160
	Synaptics Pressure Motion Factor (298):	1.000000, 1.000000
	Synaptics Resolution Detect (299):	1
	Synaptics Grab Event Device (300):	0
	Synaptics Gestures (301):	1
	Synaptics Capabilities (302):	1, 0, 0, 1, 1, 1, 1
	Synaptics Pad Resolution (303):	58, 41
	Synaptics Area (304):	0, 0, 0, 0
	Synaptics Soft Button Areas (305):	3491, 0, 4079, 0, 0, 0, 0, 0
	Synaptics Noise Cancellation (306):	27, 27
	Device Product ID (262):	2, 7
	Device Node (263):	"/dev/input/event5"

```

---


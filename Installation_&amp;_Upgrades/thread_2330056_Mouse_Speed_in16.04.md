---
title: "Mouse Speed in16.04"
date: 2016-07-07
forum: Installation &amp; Upgrades
---

### Post by fjgaude on 2016-07-07
Is there a way to control the mouse speed in 16.04.  The way it is is fixed and too fast for the mouse I use.

Thanks!

---

### Post by QDR06VV9 on 2016-07-07
What is the output from this:
```
apt-cache policy gpointing-device-settings
```

---

### Post by QDR06VV9 on 2016-07-07
There is also hand editing...to achieve the desired speed.
To manually set your mouse speed with xinput
First locate the ID for your mouse
```
xinput list
```
Find the current Accel speed with:
```
xinput list-props 10 
```(with the #10 being the device ID for your mouse
Mine shows this
x```
input list-props 8
Device 'Logitech M510':
    Device Enabled (151):    1
    Coordinate Transformation Matrix (153):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (281):    0
    Device Accel Constant Deceleration (282):    1.000000
    Device Accel Adaptive Deceleration (283):    1.000000
    Device Accel Velocity Scaling (284):    10.000000
    Device Product ID (270):    1133, 4133
    Device Node (271):    "/dev/input/event1"
    Evdev Axis Inversion (285):    0, 0
    Evdev Axes Swap (287):    0
    Axis Labels (288):    "Rel X" (161), "Rel Y" (162), "Rel Horiz Wheel" (279), "Rel Vert Wheel" (280)
    Button Labels (289):    "Button Left" (154), "Button Middle" (155), "Button Right" (156), "Button Wheel Up" (157), "Button Wheel Down" (158), "Button Horiz Wheel Left" (159), "Button Horiz Wheel Right" (160), "Button Side" (274), "Button Extra" (275), "Button Forward" (276), "Button Back" (277), "Button Task" (278), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273), "Button Unknown" (273)
    Evdev Scrolling Distance (290):    1, 1, 1
    Evdev Middle Button Emulation (291):    1
    Evdev Middle Button Timeout (292):    50
    Evdev Third Button Emulation (293):    0
    Evdev Third Button Emulation Timeout (294):    1000
    Evdev Third Button Emulation Button (295):    3
    Evdev Third Button Emulation Threshold (296):    20
    Evdev Wheel Emulation (297):    0
    Evdev Wheel Emulation Axes (298):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (299):    10
    Evdev Wheel Emulation Timeout (300):    200
    Evdev Wheel Emulation Button (301):    4
    Evdev Drag Lock Buttons (302):    0
[me@Silversurfer ~]$ 
```


The property you are interested in is "Device Accel Constant Deceleration (267)". To slow your mouse down, the value must be increased by running xinput set-prop <your device id> <property id> <value>:
Example:
```
$ xinput set-prop 10 267 5.0
```

---

### Post by fjgaude on 2016-07-07
Oh wow, thank you for the reply... will let you know now it goes for me.

frank

---

### Post by QDR06VV9 on 2016-07-07
Please do!;)
Thanks Frank...it is good to see your smiley face still here.

---

### Post by fjgaude on 2016-07-07
Where did the 267 come from?

---

### Post by QDR06VV9 on 2016-07-07
Just an example!
You need to increase that number to slow your mouse.

---

### Post by fjgaude on 2016-07-07
I only get this:

```
frank@flash:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v6.0	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v6.0	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                      	id=13	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft® 2.4GHz Transceiver v6.0	id=10	[slave  keyboard (3)]

```

I've tried many IDs but no change in mouse speed or accel.

frank

---

### Post by QDR06VV9 on 2016-07-07
Lets see what this show us
```
xinput 
```

---

### Post by fjgaude on 2016-07-07
Exactly the same thing.

---

### Post by QDR06VV9 on 2016-07-07
Ok Great now we see how it is set up:
```
xinput list-props 2
```
Paste back the input

---

### Post by fjgaude on 2016-07-07
I replaced the wireless mouse with a usb one and in the mouse menu it shows speed control, which works.

Oh boy!

---

### Post by QDR06VV9 on 2016-07-07
If your happy I am happy:D
Take Care Frank

---

### Post by fjgaude on 2016-07-07
I rather like the wireless! I'm not really happy!

In 14.04.3 wireless works at a normal speed but still there is no item for speed in the mouse and touchpad menu.

Thanks for all your replies.

---

### Post by QDR06VV9 on 2016-07-07
Well we can still finish this if you want to.

---

### Post by fjgaude on 2016-07-07
Give me your ideas, as you wish.

---

### Post by QDR06VV9 on 2016-07-07
We just need to see the output of this still
```
xinput list-props 2
```
Which will show how the mouse speed is set and then we can slow it down.

---

### Post by fjgaude on 2016-07-07
```
frank@flash:~$ xinput list-props 2
Device 'Virtual core pointer':
	Device Enabled (131):	1
	Coordinate Transformation Matrix (133):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
```

Here it be!

---

### Post by QDR06VV9 on 2016-07-07
Ok Try this setting to see if you like this speed
```
xinput set-prop 2 131 5.0
```
Increase the Value 5.0 higher to slow it down even more if needed.

---

### Post by fjgaude on 2016-07-07
I went up to 20.0 without any change in speed.

---

### Post by fjgaude on 2016-07-07
I think is speed may be okay it's the acceleration that is very fast.

---

### Post by QDR06VV9 on 2016-07-08
To be clear for me...Speed=Acceleration.
We are talking about how fast the mouse moves with your finger moving across and up and down.
Is this how you see it also?

---


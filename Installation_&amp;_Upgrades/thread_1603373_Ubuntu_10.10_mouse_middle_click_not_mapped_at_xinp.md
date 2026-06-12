---
title: "Ubuntu 10.10 mouse middle click not mapped at xinput test"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by jhoms on 2010-10-22
Hi,

after migrating my Ubuntu box from 10.4 to 10.10 my middle click button does not work.

If I test using ...

```
xinput test <device id>
```

... all my buttons are mapped but one (the middle click): when I use it nothing is logged in the console.

This is the ouput of my mouse properties:

```
~$ xinput list-props 8
Device 'Razer DeathAdder':
	Device Enabled (117):	1
	Coordinate Transformation Matrix (119):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (243):	0
	Device Accel Constant Deceleration (244):	1.000000
	Device Accel Adaptive Deceleration (245):	1.000000
	Device Accel Velocity Scaling (246):	10.000000
	Evdev Reopen Attempts (236):	10
	Evdev Axis Inversion (247):	0, 0
	Evdev Axes Swap (249):	0
	Axis Labels (250):	"Rel X" (127), "Rel Y" (128)
	Button Labels (251):	"Button Left" (120), "Button Middle" (121), "Button Right" (122), "Button Wheel Up" (123), "Button Wheel Down" (124), "Button Horiz Wheel Left" (125), "Button Horiz Wheel Right" (126), "Button Side" (238), "Button Extra" (239), "Button Forward" (240), "Button Back" (241), "Button Task" (242), "Button Unknown" (237), "Button Unknown" (237), "Button Unknown" (237), "Button Unknown" (237)
	Evdev Middle Button Emulation (252):	2
	Evdev Middle Button Timeout (253):	50
	Evdev Wheel Emulation (254):	0
	Evdev Wheel Emulation Axes (255):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (256):	10
	Evdev Wheel Emulation Timeout (257):	200
	Evdev Wheel Emulation Button (258):	4
	Evdev Drag Lock Buttons (259):	0
```

I use middle click frequently (opening links in new tabs in Firefox or Copy&Paste in terminal) and now that I cannot I feel frustrated.

Thanks in advance.

---

### Post by jhoms on 2010-10-23
It turned to be a hardware problem. I noticed after booting Windows and confirming the same issue there. So nothing to do with Ubuntu or the upgrade to 10.10.

---

### Post by morad on 2010-10-27
I have got the same problem and I have checked and my middle click works perfectly in windows and 10.04 ( I checked it again through reinstalling it ).
Any ideas how this can be fixed?

---

### Post by jhoms on 2010-10-27
Have you tried the command xinput test <device_id>?
You can get the id of your mouse executing
```
xinput list
```
After that, you can execute
```
xinput test <device_id>
```
and see the code shown when you move your mouse or click any button. In my case (and because the hardware problem) when I was pressing the middle button nothing was echoed.

---

### Post by morad on 2010-10-30
I have actually and the outcome is quite interesting.
When I tried it in Kernel 2.6.32.25 the outcome was :

```
morad@hamdam2:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=15    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=17    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; HID 413c:8157                               id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_2M                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=16    [slave  keyboard (3)]
morad@hamdam2:~$ xinput test 14
button press   1 
button release 1 
button press   2 
button release 2 
button press   3 
button release 3
```but when I did it with the new Kernel (2.6.35.22) which came with 10.10 it has assigned mouse click 1 to the middle mouse button as well.

```

morad@hamdam2:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=12    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; HID 413c:8157                               id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_2M                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=16    [slave  keyboard (3)]
morad@hamdam2:~$ xinput test 14
button press   1 
button release 1 
button press   1 
button release 1 
button press   3 
button release 3 
```Is there any way to assign the right value to the middle mouse button here?

---

### Post by morad on 2010-10-30
Have a look at the following link.
It seems to be way to go but I have not been able to fix it because although in xinput test I get 1 for the middle button but when I get the mapping it is set to 2 which should be fine.

[https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

---

### Post by jhoms on 2010-11-01
I did some tests.

If I use xinput get-button-map I get a sequence from 1 to 16: 1 2 3 4 ...
I guess you get something similar.

I tried to map middle button to the same code as left button by doing this:
```
xinput set-button-map 9 1 1 3
```

(9 is my device_id at the moment)

After that, testing with xinput test printed 1 whenever I pressed the left or the middle button.

I returned to the normal behavior setting the right map back.
```
xinput set-button-map 9 1 2 3
```

I assume you get 1 always for the middle button despite the value you give it with set-button-map, right?

I am sorry if not helping a lot but I opened this thread looking for help either because I am not an expert.

---

### Post by deus_zeus on 2010-11-22
I have a similar issue - I  have a standard PS2 mouse - same deal. The middle scroll wheel will paste from clipboard when I press it within a terminal session, but doesn't scroll at all. 
I've tried in browsers, terminals, and an open office doc. Most frustrating of all is that this was working fine on 10.4. 
Below, button two is when I press the mouse wheel, but if I scroll, nothing happens in xinput:
FYI - it's not a hardware issue - scrolling works perfectly in XP, Vista, and WIN7 - mouse is only 4 weeks old.
-------------------------

root@deus4679:~# xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USBPS2                                      id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; USBPS2                                      id=8    [slave  keyboard (3)]
root@deus4679:~# xinput test 9
button press   2 
button release 2 
button press   1 
button release 1 
button press   3 
button release 3 
motion a[0]=357 a[1]=827 
motion a[0]=353 a[1]=829 
motion a[0]=350 a[1]=831 
motion a[0]=347 a[1]=833 
motion a[0]=346 a[1]=834 
button press   1 
button release 1 
button press   2 
button release 2 
button press   2 
button release 2 
button press   2 
button release 2 
button press   1 
button release 1 
button press   2 
button release 2 
button press   3 
button release 3 
button press   1 
button release 1 
button press   1 
button release 1 
------------------
What gives? Surely I can't be the only one having this issue?

---

### Post by meltindar on 2010-11-25
I have the same issue. After upgrading from 10.04 to 10.10 my middle click on touchpad (HP nc8430) has the same function as left click.
Here's the output of xinput:

```
melt@shadow:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Logitech Logitech USB Headset           	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=13	[slave  keyboard (3)]
melt@shadow:~$ xinput test 11
button press   1 
button release 1 
button press   1 
button release 1 
button press   3 
button release 3 
```

I've also tried some things from posts above as well as:

```
xmodmap -e "pointer = 1 2 3 4 5"
```

from [this]("http://art.ubuntuforums.org/showthread.php?p=9920677") thread but without success. Someone with any ideas?

---

### Post by andreselsuave on 2010-11-28
I am having the same issue since 10.10. 
```
andreselsuave@andreselsuave-HP-EliteBook:~$ xinput test 12
button press   1 
button release 1 
button press   1 
button release 1 
button press   3 
button release 3 
```

I am suscribing to the thread in case some solution is found :)

---

### Post by jhoms on 2010-11-28
It seems like someone filled a BUG related to this issue:

[https://bugs.launchpad.net/bugs/676898]("https://bugs.launchpad.net/bugs/676898")

---

### Post by deus_zeus on 2010-12-08
Working now - but not sure why.
My PS2 kbd and mouse are connected via a KVM, but as my new desktop didn't have dual PS2 plugs, I was using a belkin dual PS2 to USB adapter - I never thought to check this, because everything always worked fine when switching to my other machines. Anyway, I tested using a wireless mouse, and everything worked ok. I unplugged the belkin USB adapter, and plugged it into a different USB port - lo and behold, all my mouse functions now work. I can't explain why this worked, I'm just happy  it does now.

---

### Post by meltindar on 2010-12-09
Yes, it works now after the latest update.

---


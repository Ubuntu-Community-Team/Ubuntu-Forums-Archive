---
title: "Enabling 2 finger scroll"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by myddewji13 on 2010-03-21
Lucid looks great! After a bit of fooling around I managed to fix sleep (@#$@#$@ ATI drivers) and sound. The one thing that I cannot fix is my beloved 2 finger scroll. I could make love to it if it had a physical form. Unfortunately for me, I can't seem to get it to work. (2 finger scroll is greyed under mouse-touchpad preferences, gpointing device settings did not work). Anyway, posted below is my lspci output (I don't know if it'll help but I'll post anyway)

```
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
02:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
02:00.1 Audio device: ATI Technologies Inc RV710/730
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
06:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

```

Help please?

PS 2 finger vertical + horizontal scroll works in Windows 7. So does 2,3 (and I think 4 but not sure) finger taps.

---

### Post by phillw on 2010-03-21
Hi,

this thread *may* give you some leads

[http://ubuntuforums.org/showthread.php?t=1330618](http://ubuntuforums.org/showthread.php?t=1330618)

Regards,

Phill.

---

### Post by myddewji13 on 2010-03-21
All the posts are using Hal which if I'm not mistaken has been completely removed from Lucid. Also, the files mentioned do not exist. 

Another interesting thing, I cannot run 'synclient -m 300':

```
myd@GODSREMOTE:~$ synclient -m 300
Can't access shared memory area. SHMConfig disabled?

```

Any ideas why/what is going on?

---

### Post by miegiel on 2010-03-21
> **myddewji13 said:**
> All the posts are using Hal which if I'm not mistaken has been completely removed from Lucid. Also, the files mentioned do not exist. 

Another interesting thing, I cannot run 'synclient -m 300':

```
myd@GODSREMOTE:~$ synclient -m 300
Can't access shared memory area. SHMConfig disabled?

```

Any ideas why/what is going on?

Simulating 2 finger scrolling might be a viable workaround, it might not be. But still it's no true 2 finger scrolling and a bit of a waste since your touchpad does seem to support it.

I'm simulating 2 finger scrolling without using hal. [Here is how, if you want to try.]("http://ubuntuforums.org/showthread.php?t=1419833")

Some useful commands : [COLOR="Red"](replace with your device name)[/COLOR] **edited because of a recent change to xinput.**
```
xinput list
xinput list-props [COLOR="red"]"SynPS/2 Synaptics TouchPad"[/COLOR]
xinput test [COLOR="Red"]"SynPS/2 Synaptics TouchPad"[/COLOR]
xinput test-xi2 [COLOR="red"]"SynPS/2 Synaptics TouchPad"[/COLOR]
```

---

### Post by myddewji13 on 2010-03-21
Pardon me if this is a stupid question, but how exactly do I go about figuring out what my device name is?

---

### Post by nubalci on 2010-03-21
System>Preferences>Mouse>Touchpad

select the "Two-finger scrolling" button.

That's it.

---

### Post by myddewji13 on 2010-03-21
As seen in the screenshot, I can't do that....

---

### Post by HoboJ on 2010-03-21
I don't have a touchpad to play with so I don't know if this will work. You can try using gconf-editor to change it to two finger scrolling.

Desktop > gnome > peripherals > touchpad > change scroll_method to 2

I'd expect that should turn on two finger scrolling.

---

### Post by myddewji13 on 2010-03-21
> **HoboJ said:**
> I don't have a touchpad to play with so I don't know if this will work. You can try using gconf-editor to change it to two finger scrolling.

Desktop > gnome > peripherals > touchpad > change scroll_method to 2

I'd expect that should turn on two finger scrolling.

This results in no scrolling at all.... :-(

---

### Post by myddewji13 on 2010-03-21
> **miegiel said:**
> Simulating 2 finger scrolling might be a viable workaround, it might not be. But still it's no true 2 finger scrolling and a bit of a waste since your touchpad does seem to support it.

I'm simulating 2 finger scrolling without using hal. [Here is how, if you want to try.]("http://ubuntuforums.org/showthread.php?t=1419833")

Some useful commands : [COLOR="Red"](replace with your device name)[/COLOR]
```
xinput list
xinput list-props '[COLOR="red"]"SynPS/2 Synaptics TouchPad"[/COLOR]'
xinput test '[COLOR="Red"]"SynPS/2 Synaptics TouchPad"[/COLOR]'
xinput test-xi2 '[COLOR="red"]"SynPS/2 Synaptics TouchPad"[/COLOR]'
```


I went to the thread you specified, It worked, I'm gonna try using the script to make this permanent.... will update thread to solved if it works.

---

### Post by myddewji13 on 2010-03-21
I took your script and modified it:

```
#!/bin/bash
#
# list of synaptics device properties http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4
# list  current synaptics device properties: xinput list-props '"SynPS/2 Synaptics TouchPad"'
#
xinput --set-prop --type=int --format=32 '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Pressure" 4
xinput --set-prop --type=int --format=32 '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Width" 7         # Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
xinput --set-prop --type=int --format=8  '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Scrolling" 1 1   # vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
xinput --set-prop --type=int --format=8  '"SynPS/2 Synaptics TouchPad"' "Synaptics Edge Scrolling" 0 0 0       # vertical, horizontal, corner - values: 0=disable  1=enable
xinput --set-prop --type=int --format=32 '"SynPS/2 Synaptics TouchPad"' "Synaptics Jumpy Cursor Threshold" 250 # stabilize 2 finger actions - value=pad-pixels
exit
```

But I cannot get it to run at startup. Can someone tell me how?
I tried adding it to startup applications by using '/home/$username$/touchpad.sh' after setting permissions to allow the script to execute but no luck :(.

---

### Post by myddewji13 on 2010-03-22
Interesting... 

I modified the script to startup firefox. So the script does run on login, and firefox starts. But scrolling isn't affected at all. However, if I manually run the script, 2 finger scroll is enabled... 

Any idea why? I'm guessing something else runs and resets the scroll configs. Any way to add a delay to the script to ensure its the last thing that runs?

---

### Post by myddewji13 on 2010-03-22
Problem fixed by adding a delay. Script is now as follows: 
```
#!/bin/bash
#
# list of synaptics device properties http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4
# list  current synaptics device properties: xinput list-props '"SynPS/2 Synaptics TouchPad"'
#
sleep 5 #added delay... 
xinput --set-prop --type=int --format=32 '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Pressure" 4
xinput --set-prop --type=int --format=32 '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Width" 7         # Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
xinput --set-prop --type=int --format=8  '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Scrolling" 1 1   # vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
xinput --set-prop --type=int --format=8  '"SynPS/2 Synaptics TouchPad"' "Synaptics Edge Scrolling" 0 0 0       # vertical, horizontal, corner - values: 0=disable  1=enable
xinput --set-prop --type=int --format=32 '"SynPS/2 Synaptics TouchPad"' "Synaptics Jumpy Cursor Threshold" 250 # stabilize 2 finger actions - value=pad-pixels
exit
```

So problem solved :D. Thanks guys.

---

### Post by miegiel on 2010-03-22
> **myddewji13 said:**
> Pardon me if this is a stupid question, but how exactly do I go about figuring out what my device name is?

The 1st command in the list ;)
```
xinput list
```
Good to see you got it working. I start the script by adding to [I]"Session and Startup" :
[/I]```
sh touchpad.sh
```

---

### Post by myddewji13 on 2010-03-22
Update:

After sleeping the computer the script stops working and need to be rerun to enable 2 finger scroll. Does anyone know why/workarounds?

---

### Post by miegiel on 2010-03-22
> **myddewji13 said:**
> Update:

After sleeping the computer the script stops working and need to be rerun to enable 2 finger scroll. Does anyone know why/workarounds?

Sorry, no. Suspend doesn't work on this machine, it suspends but it won't wake up. So I never noticed that or had to fix it.

---

### Post by myddewji13 on 2010-03-22
I had that problem too! (not waking up)...its an issue with my ATI drivers, the open source version doesnt work with suspend...

---

### Post by rickwood on 2010-03-24
> **myddewji13 said:**
> Update:

After sleeping the computer the script stops working and need to be rerun to enable 2 finger scroll. Does anyone know why/workarounds?

Yeah, I've got the same issue. The script works fantastic, I just need to find out how to add it to the list of things run when the computer comes out of sleep.  Haven't tried it with hibernation yet, but sleep is generally more convenient for me.

---

### Post by myddewji13 on 2010-03-24
When you find out please let us know! Or if anyone else knows how to get it to run coming out of sleep...

---

### Post by miegiel on 2010-03-24
Since yesterday my suspend works \\:D/ and I'm happy to say I've got no touchpad problems after resuming. The funny thing is that the fix for my suspend issue might also help with the touchpad.

I had to add *i8042.reset=1* to the kernel line in grub (check [here for instructions]("http://ubuntuforums.org/showthread.php?t=1165087&page=74")). If *i8042.reset=1* doesn't do the trick, try *i8042.nomux=1* instead. As I only faguely grasp what *i8042.reset=1* and *i8042.nomux=1* do: [COLOR="Red"]*Try at your own risk!*[/COLOR]

---

### Post by sgosnell on 2010-03-24
I fixed my suspend by installing the 2.6.33 kernel.  It worked immediately.  System/Preferences/Mouse/2-finger scroll also worked.

EEE PC 900

---

### Post by Starks on 2010-04-02
> **myddewji13 said:**
> Problem fixed by adding a delay. Script is now as follows: 
```
#!/bin/bash
#
# list of synaptics device properties [http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4](http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4)
# list  current synaptics device properties: xinput list-props '"SynPS/2 Synaptics TouchPad"'
#
sleep 5 #added delay... 
xinput --set-prop --type=int --format=32 '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Pressure" 4
xinput --set-prop --type=int --format=32 '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Width" 7         # Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
xinput --set-prop --type=int --format=8  '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Scrolling" 1 1   # vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
xinput --set-prop --type=int --format=8  '"SynPS/2 Synaptics TouchPad"' "Synaptics Edge Scrolling" 0 0 0       # vertical, horizontal, corner - values: 0=disable  1=enable
xinput --set-prop --type=int --format=32 '"SynPS/2 Synaptics TouchPad"' "Synaptics Jumpy Cursor Threshold" 250 # stabilize 2 finger actions - value=pad-pixels
exit
```So problem solved :D. Thanks guys.

Be careful with your string usage. You used double quotes.

```
#!/bin/bash
#
# list of synaptics device properties [http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4](http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4)
# list  current synaptics device properties: xinput list-props "SynPS/2 Synaptics TouchPad"
#
sleep 5 #added delay... 
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 4
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 7         # Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 1   # vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 0 0 0       # vertical, horizontal, corner - values: 0=disable  1=enable
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 250 # stabilize 2 finger actions - value=pad-pixels
exit
```

---

### Post by miegiel on 2010-04-02
> **Starks said:**
> Be careful with your string usage. You used double quotes.

That's a recent change to xinput. I guess they realized *'"devicename"'* was a bit over the top and changed it to *"devicename"*.

---

### Post by myddewji13 on 2010-04-02
That explains why my script stopped working....

---

### Post by rickwood on 2010-04-03
Thanks for the info - I've updated my scripts now to get this functioning again. I run this script on startup:

```
#!/bin/bash
#
# list of synaptics device properties http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4
# list  current synaptics device properties: xinput list-props '"SynPS/2 Synaptics TouchPad"'
#
sleep 5 #added delay... 
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 4
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 7         # Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 1   # vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 0 0 0       # vertical, horizontal, corner - values: 0=disable  1=enable
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 250 # stabilize 2 finger actions - value=pad-pixels
exit
```

That works great. But when my computer sleeps, I loose 2-finger scroll on resume. So I use the following script and assign F3 as a hotkey to activate it.  This kills 2 birds with 1 stone - quick access to re-enable 2-finger scrolling, and an easy way to turn on or off the touchpad on my Asus Eee 1005PE. So when the computer resumes, I just hit F3 twice and all is good again.

```
#!/bin/bash
#
# list of synaptics device properties http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4
# list  current synaptics device properties: xinput list-props '"SynPS/2 Synaptics TouchPad"'
#
if xinput list-props "SynPS/2 Synaptics TouchPad" | grep "Device Enabled" | grep 0
then 
#	sleep 2 #added delay...
	xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 1
	xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 4
	xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 7         # 	Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
	xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 1   # 	vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
	xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 0 0 0       # 	vertical, horizontal, corner - values: 0=disable  1=enable
	xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 250 # 	stabilize 2 finger actions - value=pad-pixels
else
	xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 0	
fi
exit
```

---

### Post by fallingleaf on 2010-04-03
I've been trying the various scripts and can't get 2 button working. Here's my info before running the script:

```
$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=15	[s[CODE]
```lave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=17	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HID 413c:8157                           	id=10	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_2M             	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=16	[slave  keyboard (3)]
[/CODE]
```
$ xinput list-props "AlpsPS/2 ALPS GlidePoint" 
Device 'AlpsPS/2 ALPS GlidePoint':
	Device Enabled (123):	1
	Device Accel Profile (243):	0
	Device Accel Constant Deceleration (244):	1.000000
	Device Accel Adaptive Deceleration (246):	1.000000
	Device Accel Velocity Scaling (247):	10.000000
	Synaptics Edges (261):	153, 870, 115, 652
	Synaptics Finger (262):	12, 14, 127
	Synaptics Tap Time (263):	128
	Synaptics Tap Move (264):	50
	Synaptics Tap Durations (265):	180, 180, 100
	Synaptics Tap FastTap (266):	0
	Synaptics Middle Button Timeout (267):	75
	Synaptics Two-Finger Pressure (268):	139
	Synaptics Two-Finger Width (269):	7
	Synaptics Scrolling Distance (270):	25, 25
	Synaptics Edge Scrolling (271):	1, 1, 1
	Synaptics Two-Finger Scrolling (272):	0, 0
	Synaptics Move Speed (273):	0.400000, 0.700000, 0.039124, 40.000000
	Synaptics Edge Motion Pressure (274):	14, 79
	Synaptics Edge Motion Speed (275):	1, 102
	Synaptics Edge Motion Always (276):	0
	Synaptics Button Scrolling (277):	1, 1
	Synaptics Button Scrolling Repeat (278):	1, 1
	Synaptics Button Scrolling Time (279):	100
	Synaptics Off (280):	0
	Synaptics Guestmouse Off (281):	0
	Synaptics Locked Drags (282):	0
	Synaptics Locked Drags Timeout (283):	5000
	Synaptics Tap Action (284):	2, 3, 0, 0, 1, 3, 2
	Synaptics Click Action (285):	1, 1, 0
	Synaptics Circular Scrolling (286):	0
	Synaptics Circular Scrolling Distance (287):	0.100000
	Synaptics Circular Scrolling Trigger (288):	0
	Synaptics Circular Pad (289):	0
	Synaptics Palm Detection (290):	0
	Synaptics Palm Dimensions (291):	10, 99
	Synaptics Coasting Speed (292):	0.000000
	Synaptics Pressure Motion (293):	14, 79
	Synaptics Pressure Motion Factor (294):	1.000000, 1.000000
	Synaptics Grab Event Device (295):	1
	Synaptics Gestures (296):	1
	Synaptics Capabilities (297):	1, 1, 1, 0, 0
	Synaptics Pad Resolution (298):	1, 1
	Synaptics Area (299):	0, 0, 0, 0
	Synaptics Jumpy Cursor Threshold (300):	0

```


And after running the script:
```

$ xinput list-props "AlpsPS/2 ALPS GlidePoint" 
Device 'AlpsPS/2 ALPS GlidePoint':
	Device Enabled (123):	1
	Device Accel Profile (243):	0
	Device Accel Constant Deceleration (244):	1.000000
	Device Accel Adaptive Deceleration (246):	1.000000
	Device Accel Velocity Scaling (247):	10.000000
	Synaptics Edges (261):	153, 870, 115, 652
	Synaptics Finger (262):	12, 14, 127
	Synaptics Tap Time (263):	128
	Synaptics Tap Move (264):	50
	Synaptics Tap Durations (265):	180, 180, 100
	Synaptics Tap FastTap (266):	0
	Synaptics Middle Button Timeout (267):	75
	Synaptics Two-Finger Pressure (268):	4
	Synaptics Two-Finger Width (269):	7
	Synaptics Scrolling Distance (270):	25, 25
	Synaptics Edge Scrolling (271):	0, 0, 0
	Synaptics Two-Finger Scrolling (272):	1, 1
	Synaptics Move Speed (273):	0.400000, 0.700000, 0.039124, 40.000000
	Synaptics Edge Motion Pressure (274):	14, 79
	Synaptics Edge Motion Speed (275):	1, 102
	Synaptics Edge Motion Always (276):	0
	Synaptics Button Scrolling (277):	1, 1
	Synaptics Button Scrolling Repeat (278):	1, 1
	Synaptics Button Scrolling Time (279):	100
	Synaptics Off (280):	0
	Synaptics Guestmouse Off (281):	0
	Synaptics Locked Drags (282):	0
	Synaptics Locked Drags Timeout (283):	5000
	Synaptics Tap Action (284):	2, 3, 0, 0, 1, 3, 2
	Synaptics Click Action (285):	1, 1, 0
	Synaptics Circular Scrolling (286):	0
	Synaptics Circular Scrolling Distance (287):	0.100000
	Synaptics Circular Scrolling Trigger (288):	0
	Synaptics Circular Pad (289):	0
	Synaptics Palm Detection (290):	0
	Synaptics Palm Dimensions (291):	10, 99
	Synaptics Coasting Speed (292):	0.000000
	Synaptics Pressure Motion (293):	14, 79
	Synaptics Pressure Motion Factor (294):	1.000000, 1.000000
	Synaptics Grab Event Device (295):	1
	Synaptics Gestures (296):	1
	Synaptics Capabilities (297):	1, 1, 1, 0, 0
	Synaptics Pad Resolution (298):	1, 1
	Synaptics Area (299):	0, 0, 0, 0
	Synaptics Jumpy Cursor Threshold (300):	250
```

It looks to be enabled but when I try 2 fingers it just acts the same as 1 finger.  Any ideas?

---

### Post by miegiel on 2010-04-03
> **fallingleaf said:**
> ...  Any ideas?
You could try to set something else than two finger scrolling to test if the touch pad "listens" to any of the script's commands. For example: middle botton in the top left corner and right button in the bottom left.```
xinput --set-prop --type=int --format=8  "AlpsPS/2 ALPS GlidePoint" "Synaptics Tap Action" 0 0 2 3 1 2 0
```

Not sure if this helps, but try running 
```
xinput test "AlpsPS/2 ALPS GlidePoint"
```

When scrolling with 2 fingers without the script, I get the same output as with 1 finger, it looks like :
```
motion a[0]=2917 a[1]=2733 
motion a[0]=2924 a[1]=2760 
motion a[0]=2929 a[1]=2786 
motion a[0]=2934 a[1]=2812 
motion a[0]=2940 a[1]=2838 
motion a[0]=2947 a[1]=2863 
motion a[0]=2960 a[1]=2886 
motion a[0]=2977 a[1]=2909
```
and with the script the output is (4 is up, 5 is down) :
```
button release 4 
button press   4 
button release 4 
button press   4 
button release 4 
button press   5 
button release 5 
button press   5 
button release 5 
button press   5 
```
And there is also the ```
xinput test-xi2 "AlpsPS/2 ALPS GlidePoint"
``` test.

That said, I'm not sure this works on the alps pads. You should look into that ;) You also need to keep in mind that this method _simulates_ 2 finger scrolling by using the width value of a touch. A touch wider than the set value in the *[COLOR="Blue"]xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 8[/COLOR]* line of the script is treated as 2 fingers, touches less wide as 1 finger. This way you can still scroll with 2 fingers on "gesture type touchpads" that don't support 2 finger scrolling. Basically the pads are the same as the 2 finger scrolling pads, but the pad's firmware only passes on the width value and not the number of fingers. Older pads don't even pass on the width value and can't use this trick to simulate 2 finger scrolling.

---

### Post by fallingleaf on 2010-04-04
Thanks miegiel,

According to [this thread]("http://swiss.ubuntuforums.org/showthread.php?p=8949067") width detection does _not_ work with Alps pads, but they managed to fake two fingers by using pressure instead.  Any idea how to do this without HAL?

---

### Post by miegiel on 2010-04-04
> **fallingleaf said:**
> Thanks miegiel,

According to [this thread]("http://swiss.ubuntuforums.org/showthread.php?p=8949067") width detection does _not_ work with Alps pads, but they managed to fake two fingers by using pressure instead.  Any idea how to do this without HAL?

Try increasing the value in the 
```
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 4
```
line. You probably also need to set the width in the next line to 0 or 1. I know a pressure of 4 is hanging my finger about 5mm above _my pad_. You can just run the *xinput* command in a terminal with different values. After some trail and error you should find the right pressure value to distinguish between 1 and 2 fingers.

---

### Post by viniosity on 2010-04-10
> **sgosnell said:**
> I fixed my suspend by installing the 2.6.33 kernel.  It worked immediately.  System/Preferences/Mouse/2-finger scroll also worked.

EEE PC 900

Out of curiosity, which method did you use to install 2.6.33? Did you use the PPA or build from scratch?  Using 2.6.33 from PPA didn't solve this for me on my Vostro V13

---

### Post by sgosnell on 2010-04-10
I just installed with gdebi, using the .deb file from [here](http://kernel.ubuntu.com/~kernel-ppa/mainline/).  I know nothing about Vostro, never even saw one.

---


---
title: "2 finger scrolling with Alps touchpad"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by myddewji13 on 2009-10-13
Hi,

I previously had 2 finger scrolling emulated in Jaunty using the instructions present here:
[http://ubuntuforums.org/showthread.php?t=1055168&highlight=finger+scroll](http://ubuntuforums.org/showthread.php?t=1055168&highlight=finger+scroll)

Ever since I upgraded to Karmic (clean install 64bit), I have been unable to get 2 finger scrolling working. After some research, I've found that this is probably due to hal regressions in Karmic (correct me if I'm wrong).

My question is this:

Is there anyway to get my 2 finger scroll back? If so how?

And before you ask, I already tried the mouse config under System->preferences-> mouse.

---

### Post by miegiel on 2009-10-13
> **myddewji13 said:**
> Hi,

I previously had 2 finger scrolling emulated in Jaunty using the instructions present here:
[http://ubuntuforums.org/showthread.php?t=1055168&highlight=finger+scroll](http://ubuntuforums.org/showthread.php?t=1055168&highlight=finger+scroll)

Ever since I upgraded to Karmic (clean install 64bit), I have been unable to get 2 finger scrolling working. After some research, I've found that this is probably due to hal regressions in Karmic (correct me if I'm wrong).

My question is this:

Is there anyway to get my 2 finger scroll back? If so how?

And before you ask, I already tried the mouse config under System->preferences-> mouse.

You mean you put a .fdi file in /etc/hal/fdi/policy/ ? That method works for me in karmic. Maybe there's something in your .fdi file that's done different now. It would help if you post the file ;)

---

### Post by seamuso on 2009-10-13
it should just be in system -> preferences -> mouse

on the touchpad tab you have the option for 2 finger up/down and horizontal scrolling

---

### Post by myddewji13 on 2009-10-13
This is the contents of my "/etc/hal/fdi/policy/11-x11-synaptics.fdi":

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLES:
        Switch on shared memory, enables the driver to be configured at runtime
	<merge key="input.x11_options.SHMConfig" type="string">true</merge>

	Maximum movement of the finger for detecting a tap
	<merge key="input.x11_options.MaxTapMove" type="string">2000</merge>

	Enable vertical scrolling when dragging along the right edge
	<merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>

	Enable vertical scrolling when dragging with two fingers anywhere on the touchpad
	<merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>

	Enable horizontal scrolling when dragging with two fingers anywhere on the touchpad
	<merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>

	If on, circular scrolling is used
	<merge key="input.x11_options.CircularScrolling" type="string">true</merge>

	For other possible options, check CONFIGURATION DETAILS in synaptics man page
        -->
	<merge key="input.x11_options.SHMConfig" type="string">On</merge>
        <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">90</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>

        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="Inspiron 1011">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">90</merge>
        </match>
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="Inspiron 1012">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">90</merge>
        </match>
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="HP MiniNote 1000">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">200</merge>
        </match>
    </match>
  </device>
</deviceinfo>
```

And as I stated before, I already tried to enable 2 finger scrolling from the mouse preferences....

---

### Post by miegiel on 2009-10-13
Try adding the [COLOR="Red"]red[/COLOR] line. 7 not be the right value for your fingers, you might want to change that. With *synclient -m 10* you can find the right value for you, see the **w** column.

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLES:
        Switch on shared memory, enables the driver to be configured at runtime
	<merge key="input.x11_options.SHMConfig" type="string">true</merge>

	Maximum movement of the finger for detecting a tap
	<merge key="input.x11_options.MaxTapMove" type="string">2000</merge>

	Enable vertical scrolling when dragging along the right edge
	<merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>

	Enable vertical scrolling when dragging with two fingers anywhere on the touchpad
	<merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>

	Enable horizontal scrolling when dragging with two fingers anywhere on the touchpad
	<merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>

	If on, circular scrolling is used
	<merge key="input.x11_options.CircularScrolling" type="string">true</merge>

	For other possible options, check CONFIGURATION DETAILS in synaptics man page
        -->
[COLOR="Blue"]	<merge key="input.x11_options.SHMConfig" type="string">On</merge>[/COLOR]
        <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">90</merge>
[COLOR="Red"]        <merge key="input.x11_options.EmulateTwoFingerMinW" type="string">7</merge>[/COLOR]
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>

        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="Inspiron 1011">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">90</merge>
        </match>
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="Inspiron 1012">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">90</merge>
        </match>
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="HP MiniNote 1000">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">200</merge>
        </match>
    </match>
  </device>
</deviceinfo>
```
btw, in karmic you don't need the [COLOR="Blue"]blue[/COLOR] line anymore to change mose settings (you do need it to run*synclient -m 10*). It's also a security risk, though a minor one I believe.

---

### Post by myddewji13 on 2009-10-13
I tried adding the line, No luck :(.... (after a full reboot)

---

### Post by myddewji13 on 2009-10-13
Also when I run synclien -m 10 ...the w value sits at 0 at all times...

---

### Post by miegiel on 2009-10-13
> **myddewji13 said:**
> Also when I run synclien -m 10 ...the w value sits at 0 at all times...

What about the f value ?

---

### Post by myddewji13 on 2009-10-13
it alternates betwee 0 and 1

---

### Post by miegiel on 2009-10-13
> **myddewji13 said:**
> it alternates betwee 0 and 1

If you have a 2 finger (or more) touchpad the f value should go to 2 when you touch it with 2 fingers (or 3 or more). 

Maybe (if you have a true multitouch touchpad) the 2 finger emulation is getting in the way. Try removing the *EmulateTwoFingerMinZ* and *EmulateTwoFingerMinW* lines.

You only need to use those 2 lines to emulate 2 finger touch on pads that can't register 2 fingers, but can register the width of a touch (2 fingers are wider than 1).

As an after thought :D check */etc/hal/fdi/policy/* for any other *.fdi* files with mouse settings in them. Also you could try not using a .fdi file at all, Maybe you don't need it in karmic anymore.

---

### Post by myddewji13 on 2009-10-13
I know I have an alps touchpad which doesn't support multitouch. In the past I've always emulated the 2 finger scroll.(I already tried removing the added lines and enabling 2 finger scroll in the mouse preferences with no luck) .

---

### Post by miegiel on 2009-10-14
I'm really puzzled by this. If with *synclient -m 10* the w column never goes up from 0 you can't emulate 2 finger touch. But then how could it have worked in jaunty? Maybe something changed in the driver and in jaunty the w column did go up from 0?

I definitely feel your pain, once you're used to 2 finger scrolling it's no fun to do without.

---

### Post by Zorael on 2009-10-14
Can you set it via xinput, perhaps? No need to enable shared memory then.

```
$ xinput list | grep -i pad
$ xinput list-props *(id of the touchpad as reported by above command)*
```
Synaptics example;
```
$ xinput list-props 7                                
Device 'SynPS/2 Synaptics TouchPad':                               
        Device Enabled (90):            1                          
        Synaptics Edges (237):          1632, 5312, 1575, 4281     
        Synaptics Finger (238):         24, 29, 255                
        Synaptics Tap Time (239):               180                
        Synaptics Tap Move (240):               221                
        Synaptics Tap Durations (241):          180, 180, 100      
        Synaptics Tap FastTap (242):            0                  
        Synaptics Middle Button Timeout (243):          75         
        Synaptics Two-Finger Pressure (244):            280        
        Synaptics Scrolling Distance (245):             100, 100   
        Synaptics Edge Scrolling (246):         1, 0, 0            
        **Synaptics Two-Finger Scrolling (247)**:           1, 0
        Synaptics Edge Motion Pressure (248):           29, 159
        Synaptics Edge Motion Speed (249):              1, 401
        Synaptics Edge Motion Always (250):             0
        Synaptics Button Scrolling (251):               1, 1
        Synaptics Button Scrolling Repeat (252):                1, 1
        Synaptics Button Scrolling Time (253):          100
        Synaptics Off (254):            0
        Synaptics Guestmouse Off (255):         0
        Synaptics Locked Drags (256):           0
        Synaptics Locked Drags Timeout (257):           5000
        Synaptics Tap Action (258):             2, 3, 0, 0, 1, 2, 3
        Synaptics Click Action (259):           1, 1, 1
        Synaptics Circular Scrolling (260):             0
        Synaptics Circular Scrolling Trigger (261):             0
        Synaptics Circular Pad (262):           0
        Synaptics Palm Detection (263):         0
        Synaptics Palm Dimensions (264):                10, 199
        Synaptics Pressure Motion (265):                29, 159
        Synaptics Grab Event Device (266):              1
```
Perhaps your Alps pad has an equavilent of Synaptics Two-Finger Scrolling.

---


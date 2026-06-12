---
title: "Mouse button mapping"
date: 2008-09-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by lucazade on 2008-09-27
Hi all!

I would like to map mouse-events (for a logitech mx revolution) in intrepid like i did in the previous releases of xorg:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection


I read something about hal but i get no success in configuring it.
Any suggestion?

---

### Post by Delvien on 2008-09-29
bump-  i would like to know as well, since BTNX is no longer going to be developed.

---

### Post by MaX on 2008-09-29
X is using env (or something like that) now instead of the Mouse driver.

You are supposed to be able to map infinite number of buttons with it.
Just do a search on the forum and you'll find the instructions.

---

### Post by Wise Ferret on 2008-09-29
> **lucazade said:**
> 
I read something about hal but i get no success in configuring it.
Any suggestion?

The driver used now is called evdev, and as far as I know (and was told by developers) it cannot be configured using xorg.conf.

What can be used though is the command xinput. Use:
xinput list //to list your configurable devices and their id's.
xinput list-props <dev-id> //to list the properties you can set for the device.
xinput set-int-prop <dev-id> <"property-name"> <format> <new-value>  //to set a new value to property.

I, for example, use the following command on startup to set 3 button emulation of my mouse (id 5) to zero using 8-bit format:
xinput set-int-prop 5 "Middle Button Emulation" 8 0 

See the man page for more details. I hope it helps.

---

### Post by lucazade on 2008-09-30
> What can be used though is the command xinput. Use:
xinput list //to list your configurable devices and their id's.

I get this output:

```
"Virtual core keyboard"	id=0	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Virtual core pointer"	id=1	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
"Logitech USB Receiver"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
"Logitech USB Receiver"	id=3	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"AT Translated Set 2 keyboard"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=5	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

```

> xinput list-props <dev-id> //to list the properties you can set for the device.

```
Device 'Logitech USB Receiver':
	Device Enabled:		1
	Middle Button Emulation:		2
		valid values: 0 1 2 
	Middle Button Timeout:		50
	Wheel Emulation:		0
		valid values: 1 0 
	Wheel Emulation X Axis:		0, 0
	Wheel Emulation Y Axis:		4, 5
	Wheel Emulation Inertia:		10
	Wheel Emulation Timeout:		200
	Wheel Emulation Button:		4
	Drag Lock Buttons:		0

```


I would like to map the search-button of my logitech mx revolution as a button2 (or middle button) since i have to press both button1 and button3 to get a button2 event.


If use xev i get this output clicking the search button:

```
KeyPress event, serial 35, synthetic NO, window 0x2c00001,
    root 0x1a6, subw 0x2c00002, time 4141769, (29,48), root:(31,90),
    state 0x10, keycode 225 (keysym 0x1008ff1b, XF86Search), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x2c00001,
    root 0x1a6, subw 0x2c00002, time 4141933, (29,48), root:(31,90),
    state 0x10, keycode 225 (keysym 0x1008ff1b, XF86Search), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```


This it what i get with cat /proc/bus/input/devices

```

I: Bus=0003 Vendor=046d Product=c51a Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-8/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=17
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0003 Vendor=046d Product=c51a Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-8/input1
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=1f
B: KEY=837fff 2c3027 bf004444 0 0 1 f84 8a27c000 667bfa d9415fed 8e0000 0 0 0
B: REL=40
B: ABS=1 0
B: MSC=10

```


How can i set xinput to work in the proper way?
Or should i use revoco or xmodmap or anything else? :)

Thanks in advance

---

### Post by Wise Ferret on 2008-09-30
I'm sorry, I have no experience in button re-mapping. But this, I believe, is the direction to research.

---

### Post by lucazade on 2008-10-04
> **Wise Ferret said:**
> I'm sorry, I have no experience in button re-mapping. But this, I believe, is the direction to research.

Thanks anyway!

The only way i've found is to launch xmodmap and map a side button as button2, still finding a better solution!

xmodmap -e "pointer = 1 8 3 4 5 6 7 2"

xkbset is able to map the search button better but sometimes it changes the behaviour of the keypad :O

---

### Post by cnolanAU on 2008-10-14
Hi, I've run across the same issue, but I found a neater solution at:

[https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)

---

### Post by dondad on 2008-10-15
> **lucazade said:**
> I get this output:

```
"Virtual core keyboard"	id=0	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Virtual core pointer"	id=1	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
"Logitech USB Receiver"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
"Logitech USB Receiver"	id=3	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"AT Translated Set 2 keyboard"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=5	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

```



```
Device 'Logitech USB Receiver':
	Device Enabled:		1
	Middle Button Emulation:		2
		valid values: 0 1 2 
	Middle Button Timeout:		50
	Wheel Emulation:		0
		valid values: 1 0 
	Wheel Emulation X Axis:		0, 0
	Wheel Emulation Y Axis:		4, 5
	Wheel Emulation Inertia:		10
	Wheel Emulation Timeout:		200
	Wheel Emulation Button:		4
	Drag Lock Buttons:		0

```


I would like to map the search-button of my logitech mx revolution as a button2 (or middle button) since i have to press both button1 and button3 to get a button2 event.


If use xev i get this output clicking the search button:

```
KeyPress event, serial 35, synthetic NO, window 0x2c00001,
    root 0x1a6, subw 0x2c00002, time 4141769, (29,48), root:(31,90),
    state 0x10, keycode 225 (keysym 0x1008ff1b, XF86Search), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x2c00001,
    root 0x1a6, subw 0x2c00002, time 4141933, (29,48), root:(31,90),
    state 0x10, keycode 225 (keysym 0x1008ff1b, XF86Search), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```


This it what i get with cat /proc/bus/input/devices

```

I: Bus=0003 Vendor=046d Product=c51a Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-8/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=17
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0003 Vendor=046d Product=c51a Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-8/input1
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=1f
B: KEY=837fff 2c3027 bf004444 0 0 1 f84 8a27c000 667bfa d9415fed 8e0000 0 0 0
B: REL=40
B: ABS=1 0
B: MSC=10

```


How can i set xinput to work in the proper way?
Or should i use revoco or xmodmap or anything else? :)

Thanks in advance

I have gotten everything to work so far except for the search button (a different handler?) and revoco. I used xbindkeys to map the buttons to key presses. You can identify the button numbers by running xev from a terminal. I have a copy of some stuff that I found long ago to do some of this, but it is for much earlier versions of Ubuntu and I had to pick and choose what to actually do in Intrepid. You need to install xvkbd, xbindkeys, and xmacro and then up a xbindkeysrc file to identify the actions. No changes to xorg files needed. It really is fairly simple. I am putting the info I have in a code block, but since intrepid already uses evdev, you can ignore everything except the installation requirements and the xbindkeysrc structure.
```

Install the necessary packages

In a terminal (you will need the universe repository enabled):

sudo apt-get install xvkbd xbindkeys xmacro








 

 
Set up Firefox

    *

      Now let's tell firefox we want it to use sidescroll.
          o

            Enter about:config in your address bar in firefox and press enter.
          o

            Change the value of mousewheel.horizscroll.withnokey.action to 0.
          o

            Change mousewheel.horizscroll.withnokey.sysnumlines to true

            IconHint2.png Alternatively, you may leave this setting as false and use mousewheel.horizscroll.withnokey.numlines to specify a custom number.

IconNote.png At this point your mouse should have side scroll and cruise control working. Go ahead and try it in firefox if you'd like. However, the side buttons won't go back and forward in your history and the cruise control will highlight text as it scrolls vertically. We are going to take care of those problems now.
Side buttons and Nautilus, Epiphany, Konqueror
Set up xbindkeys

      In a terminal:

      gedit ~/.xbindkeysrc

    *

      Paste the following into your new file:

      "/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
        b:8
      "/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
        b:9
      "echo ButtonRelease 11 ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
        b:11
      "echo ButtonRelease 12 ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
        b:12
      "echo ButtonRelease 13 ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
        b:13
      "echo ButtonRelease 14 ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
        b:14

    *

      Save your changes and exit.
    *

      Add xbindkeys to your startup programs in the System -> Preferences -> Sessions -> Startup Programs

IconHint2.png So that you don't have to reboot, you can just run xbindkeys & in a terminal. 

running "xev" in terminal will id buttons

#Next
"xvkbd -xsendevent -text "\[Control]\[Prior]""
   m:0x0 + b:4
#Prior
"xvkbd -xsendevent -text "\[Control]\[Next]""
   m:0x0 + b:5
#Left
"xvkbd -xsendevent -text "\[Meta_L]\[Left]""
   m:0x0 + b:8
#Right
"xvkbd -xsendevent -text "\[Meta_L]\[Right]""
   m:0x0 + b:9
#Kill
"xvkbd -xsendevent -text "\[Control]\[w]""
   m:0x0 + b:10
#Next
"xvkbd -xsendevent -text "\[Prior]""
   m:0x0 + b:11
#Prior
"xvkbd -xsendevent -text "\[Next]""
   m:0x0 + b:12

This is my xbindkeysrc in case this helps someone.  I like having the center thumb button be control-w, which closes xwindow,firefox tab, whatever running in x --- very convenient.  

Instead of horizontal scrolling with the y axis of the wheel (which i rare use) i prefer to have my y axis be next and prior so that I can skip move between tabs on firefox/mozilla effortlessly.  

And for buttons 4 and 5 that are above and below the scroll wheel i have that set to go up one page and down one page per click on the browser with the control-next and control-prior.



```
I cannot remember where I found this to give credit, but it worked for me.

---

### Post by jbg7474 on 2008-10-23
I have a Microsoft Comfort Optical Mouse 3000, and it has 8 buttons: left, scroll button, right, scroll up, scroll down, scroll left, scroll right, side button.  

I messed around with xorg.conf and screwed something up so that the mapping I was getting became goofy--repeated changes to xorg.conf didn't fix it.  xev was reporting scroll left as button 8, and scroll right as button 9.

I used:
```
xinput list
```
to find the mouse, which was device 7.  Then I used:
```
xinput set-button-map 7 1 2 3 4 5 6 7 8 9
```
to get it straightened out.  Now xev reported my side button as button 9, but I wanted it as button 8 so I can use it for "back" in Firefox.  So I then used:
```
xinput set-button-map 7 1 2 3 4 5 6 7 9 8
```

And now I'm squared away--my side button works as "back" in Firefox, and my scroll left and scroll right work too!

Forgot to mention: I didn't need to install anything to make this work.

Edit: unfortunately, this solution doesn't stick--I have to redo it every time the mouse is detected again.  There is now a way to do xorg.conf like things with .fdi files in /etc/hal/fdi/policy, but I'm still working on understanding that.

---

### Post by Unicast on 2008-10-25
Just in case this helps someone else out.....

Managed to get my mouse wheel scroll left / right behaviour changed to back/forward history in firefox:

Changed the following in **about:config** in firefox:
```
mousewheel.horizscroll.withnokey.action             2
mousewheel.horizscroll.withnokey.numlines           -1
mousewheel.horizscroll.withnokey.sysnumlines        false
```

The default behaviour in firefox under Hardy was back/foward history, but someone decided to change this under Intrepid - shame on you whoever you are!! :p

---

### Post by codedmin on 2008-10-29
Hy there.

I'm in the same boat :(

I put this as my .Xmodmap
> pointer = 1 2 3 4 5 8 9 10 11 12 13 14 15 16 17 6 7 

With that i have the buttons as i want! Main scroll left/right work as back/forward in firefox. The thumb scroll is to rotate the cube (in compiz manager i set the buttons manually)

The only thing i can't fix is the search button to react as wheel click... anyone?

Thanks

---

### Post by codedmin on 2008-10-29
Ok, i solve it

[http://ubuntuforums.org/showpost.php?p=1617137&postcount=1](http://ubuntuforums.org/showpost.php?p=1617137&postcount=1) I this post, scroll down and follow the search for

Optional tips and tricks:

Search button-> mouse wheel click

The only thing i have change is the number of pointer, **225 not 122** and must activate the mouse keys in the keyboard preferences.

Cheers

---


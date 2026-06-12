---
title: "[SOLVED] Scrolling with the Thinkpad Trackpoint"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wenuswilson on 2008-10-16
I am have trouble getting the center button scroll feature to work in Ibex. I'm running and x64 upgraded system from Hardy. I've gone to [this site telling me what to do]("http://psung.blogspot.com/2008/09/scrolling-with-thinkpads-trackpoint-in.html"). I followed the directions, restarted my system and still no scrolling. Hardy's scroll was much easier to fix [I went here]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61#TrackPoint") to solve that but now nothing I seem to do gives me a scroll.

---

### Post by ccc1 on 2008-10-16
> **wenuswilson said:**
> I am have trouble getting the center button scroll feature to work in Ibex. I'm running and x64 upgraded system from Hardy. I've gone to [this site telling me what to do]("http://psung.blogspot.com/2008/09/scrolling-with-thinkpads-trackpoint-in.html"). I followed the directions, restarted my system and still no scrolling. 

yeah this method stopped working. open a terminal and type:
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Wheel Emulation" 8 1
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Wheel Emulation Button" 8 2


this should do the trick. at least it worked on my x200. a pity that it doesn't work out of the box ...

---

### Post by dstaudt on 2008-10-16
It appears that as part of the the Xorg improvements, the input settings are no longer read from the xorg.config file, but are issued as dynamic commands to the X server.

After some research I was able to get this to work with the following commands:

```
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Wheel Emulation" 8 1
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Wheel Emulation Button" 8 2
```

(I have a T43p)

I added the commands to a small script that runs with my Sessions command list.

This thread has a bit more, as well as what looks like a config-file oriented alternative: [http://mvogt.wordpress.com/2008/08/15/xorg-evdev-and-emulatewheel/](http://mvogt.wordpress.com/2008/08/15/xorg-evdev-and-emulatewheel/)

---

### Post by wenuswilson on 2008-10-16
I put those commands into my terminal and the problem still exists.

---

### Post by wenuswilson on 2008-10-17
A sad, pitiful, "I can't figure this out" bump...

---

### Post by dstaudt on 2008-10-17
Try the xinput 'list' command, to check if your device's name is different from "TPPS/2 IBM TrackPoint".  

```
xinput list
```

Modify the above commands accordingly.  The man pages for xinput provide more detail on how to discover your input devices, query their capabilities, and change settings.

```
man xinput
```

Hopefully soon a GUI for confuring this easily will be developed.

---

### Post by wenuswilson on 2008-10-18
My output-- > "Virtual core keyboard"	id=0	[XKeyboard]
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
"Generic Keyboard"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Trackpoint"	id=3	[XExtensionPointer]
	Num_buttons is 9
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
"Synaptics Touchpad"	id=4	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
"Macintosh mouse button emulation"	id=5	[XExtensionPointer]
	Num_buttons is 4
	Num_axes is 2
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"TPPS/2 IBM TrackPoint"	id=6	[XExtensionPointer]
	Num_buttons is 4
	Num_axes is 2
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"AT Translated Set 2 keyboard"	id=7	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=8	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=9	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255


Where exactly would the problem be, if any?
Thanks.

---

### Post by wenuswilson on 2008-10-21
Alright for those who may be in the same boat as I was -- I solved it.

In Admin -> Software Sources -> Third-party Updates -> Unsupported updates. Make sure it's checked. That was you can get all of the updates. And everything that I had problems with will go away. My mistake.

---

### Post by Murrquan on 2008-10-25
> **dstaudt said:**
> I added the commands to a small script that runs with my Sessions command list.


How does one do this? I'm not familiar with the procedure.

---

### Post by wgrant on 2008-10-25
> **wenuswilson said:**
> Alright for those who may be in the same boat as I was -- I solved it.

In Admin -> Software Sources -> Third-party Updates -> Unsupported updates. Make sure it's checked. That was you can get all of the updates. And everything that I had problems with will go away. My mistake.

I can assure you that that didn't fix it - that repository is empty.

We had other miscellaneous fixes in this area that probably fixed it for you.

---


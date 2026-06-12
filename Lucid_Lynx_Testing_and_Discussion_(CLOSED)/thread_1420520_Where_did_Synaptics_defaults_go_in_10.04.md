---
title: "Where did Synaptics defaults go in 10.04?"
date: 2010-03-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by B.W. on 2010-03-03
Where are the options (defaults?) of Synaptics touchpad in NBR 10.04 Lucid Lynx?
They are gone from /etc/hal (obviously).
The trick with  /*lib*/*udev*/rules.d/66-xorg-*synaptics*.rules doesn't seem to work at all.
synclient applies the changes but only for duration of the session...

In particular, I want to switch 2-finger and 3-finger tap actions to their old defaults: 2=middle button, 3=right button, from the current reverse.[INDENT]synclient TapButton2=2
synclient TapButton3=3
[/INDENT]works
[INDENT]ENV{x11_options.TapButton2}="2"  
ENV{x11_options.TapButton3}="3" 
[/INDENT]added to /lib/udev/rules.d/66-xorg-synaptics.rules - doesn't.

---

### Post by B.W. on 2010-03-06
...bump?

---

### Post by B.W. on 2010-03-13
Was switching the tapping standard originated by the same person who  decided moving the window buttons to the left corner is a good idea?

---

### Post by korg91 on 2010-03-21
same problem...up

---

### Post by jfrorie on 2010-03-24
I believe that xorg.conf is the proper location now.

---

### Post by B.W. on 2010-03-26
It doesn't exist in the standard distribution. How do I get X to generate one? (...or whatever is the correct method to get it in place without breaking working defaults?)

---

### Post by jfrorie on 2010-03-26
> **B.W. said:**
> It doesn't exist in the standard distribution. How do I get X to generate one? (...or whatever is the correct method to get it in place without breaking working defaults?)


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"on"
EndSection

"man synaptics"  should give you the rest of the options.

I THINK this is right.  In theory you can also create evdev rules, but TPTB on the xorg list stated xorg is the way to do it.

---

### Post by yelo3 on 2010-03-26
All those properties are also available throuth xinput. Maybe there's a way to store them somewhere.

---

### Post by lazerscience on 2010-04-07
tried to play around with the udev files like you did, also no result!
also i think i need to enable shmconfig, but no idea how to do that in lucid! any help is appreciated!

---

### Post by Mr. Picklesworth on 2010-04-07
A made a post about this yesterday: [http://ubuntuforums.org/showpost.php?p=9086064&postcount=5](http://ubuntuforums.org/showpost.php?p=9086064&postcount=5)

Hope it helps!

---

### Post by rifak on 2010-04-15
hey everyone,
just installed the beta last night and after the fresh install, the trackpad was working great (2 finer tap=right click, 3 finger=middle) and 2 finger scrolling. however, after the initial set of updates, they have been reversed. now, 2 finger=middle and 3 finger=right click. any ideas? i tried using xinput, but nothing is changing when changing the properties.

---

### Post by rifak on 2010-04-15
alright, well i just solved it. using xinput, i changed the "Synaptics Tap Action" property to the value of 2, 3, 0, 0, 1, 3, 2 and the "Synaptics Click Action" to values of 1, 2, 3,. this has retrieved the 2 finger right click and 3 finger middle click. pretty much just got lucky trying different combinations. is there any more documentation for xinput explaining the values and stuff, just for future reference.

---

### Post by rifak on 2010-04-15
sooo an update to the situation. the most recent xorg-synaptics package resolved the issue completely...no need to manually adjust anymore.

---


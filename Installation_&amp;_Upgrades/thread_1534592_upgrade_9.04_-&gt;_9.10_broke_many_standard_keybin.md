---
title: "upgrade 9.04 -&gt; 9.10 broke many standard keybindings"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by jessj on 2010-07-19
Hi all,

I recently upgraded from 9.04 to 9.10, and the standard keybindings are now only working intermittently.

Here are some example outputs from 

xev | sed -n 's/^.*state \([0-9].*\), keycode *\([0-9]\+\) *\(.*\), .*$/keycode \2 = \3, state = \1/p'

Pressing ' worked for a while, but then I started to get this for one keypress of '

keycode 64 = (keysym 0xffe9, Alt_L), state = 0x10
keycode 48 = (keysym 0x27, apostrophe), state = 0x18
keycode 64 = (keysym 0xffe9, Alt_L), state = 0x18
keycode 48 = (keysym 0x27, apostrophe), state = 0x10


Pressing 0 gives this:

keycode 19 = (keysym 0x30, 0), state = 0x10

but also opens the Take Screenshot Dialog which was previously bound to the PrintScreen key. Note that there is only one line of output; there should be two - one for pressing and the other for depressing the key.



Pressing Printscreen gives the same output as pressing 0:

keycode 19 = (keysym 0x30, 0), state = 0x10

And also tries to do a screengrab.


Pressing /

keycode 108 = (keysym 0xffea, Alt_R), state = 0x10
keycode 61 = (keysym 0x2f, slash), state = 0x18
keycode 108 = (keysym 0xffea, Alt_R), state = 0x18
keycode 61 = (keysym 0x2f, slash), state = 0x10


Sometimes I also have problems with the emacs shortcuts Ctrl-s and Ctrl-. but I didnt catch those problems with xev to see what is happening.


I have a generic usb Spanish keyboard, but I have always used the US layout.

Im not sure where to go from here.  Any ideas how I might solve this

Thanks in advance for any help.

Jess

---

### Post by jessj on 2010-07-21
Bump.

---


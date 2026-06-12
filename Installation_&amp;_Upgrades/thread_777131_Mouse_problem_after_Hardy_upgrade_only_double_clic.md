---
title: "Mouse problem after Hardy upgrade: only double clicks"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by perenti on 2008-05-01
After upgrading from 7.10 to Hardy Heron all clicks with my mouse (USB Logitech MX700) are regarded as double clicks. Moreover, left-clicking on the icons in the menu panel has no effect anymore.

This is my /etc/X11/xorg.conf:


Section "InputDevice"
	Identifier 	"Configured Mouse"
	Driver 		"mouse"
	Option		"Dev Name"	"Logitech, Inc. MX-700 Cordless Mouse Receiver"
#	Option 		"CorePointer"
	Option 		"Device" 	"/dev/input/mice"
	Option 		"Protocol" 	"ExplorerPS/2"
	Option 		"ZAxisMapping" 	"6 7"
	Option 		"ButtonMapping" "1 2 3 4 5 "
	Option 		"Resolution" 	"800"
	Option 		"Buttons" 	"10"
EndSection

---

### Post by perenti on 2008-05-01
For the record, I fixed this by removing the hash before Option "CorePointer" ...

---

### Post by PS5000 on 2008-06-22
On Kubuntu Hardy KDE 3 x64, I experience this double click issue intermittently: sometimes my mouse clicks are interpreted as double clicks.

As you can see, the "CorePointer" option is uncommented in my xorg.conf file.

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Is anyone experiencing this problem?  Has anyone found a different solution that works?

---

### Post by roadmouse on 2008-07-14
I'm having the same problems, and have not been able to solve them yet.

Tried the above, and this:
[http://ubuntuforums.org/showthread.php?t=285041]("http://ubuntuforums.org/showthread.php?t=285041")

But no improvement yet. :?

Has anyone managed to fix this another way?

Suggestions are welcome. :)

---

### Post by PS5000 on 2008-07-14
Try this:

```
# Mouse fix as per bug 196711
Section "InputDevice"
	Identifier	"CorePointer"
	Driver		"mouse"
EndSection
```

Let me know if this works for you.

---


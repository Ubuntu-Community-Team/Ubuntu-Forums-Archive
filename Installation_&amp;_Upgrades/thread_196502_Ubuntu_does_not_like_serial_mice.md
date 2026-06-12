---
title: "Ubuntu does not like serial mice"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by nowheretoturn on 2006-06-14
I had the hoary release installed and it did not work with my serial mouse. I decided to install Dapper from scratch using the alternate installation and now I find out that I am no further ahead with Dapper than I was with Hoary. The mouse (2 button Mtisumi serial mouse) is dead in X-Windows. It is not the mouse since a new install of Mandriva on the same computer works fine. What is it with Mandriva and serial mice? How can I get X Windows to cooperate with a serial mouse?

---

### Post by rcarring on 2006-06-14
I don't think Dapper supports serial mice as the only choices in xorg-conf are ps2 mice.

---

### Post by mindwarp on 2006-06-14
Ok guys quick lessons:

Dapper supports almost exactly the same hardware as all other distributions.  So if the serial mouse worked in mandrake, it works here.  Lets not go propagating this around the boards.

As for serial mouse configuration, 
```

~sudo gedit /etc/X11/xorg.conf

```

And find the mouse section
Make it look like this:
```

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/ttyS0"
Option "Protocol" "microsoft"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

```

You may need to change the protocol setting depending on the type of mouse, and you can take out the ZAxis line if you don't have a scroll wheel.

---

### Post by rcarring on 2006-06-14
I stand corrected. Sorry.

---

### Post by nowheretoturn on 2006-06-14
[QUOTE=mindwarp]Ok guys quick lessons:

Dapper supports almost exactly the same hardware as all other distributions.  So if the serial mouse worked in mandrake, it works here.  Lets not go propagating this around the boards.

As for serial mouse configuration, 
```

~sudo gedit /etc/X11/xorg.conf

```
[/quote]

When I try to issue this command and enter the password for root I get:

"cannot open display: (null)
run 'gedit --help' for a complete list of options

I issued this command in one of the virtual console screens since XWindows is not usuable.

---

### Post by mindwarp on 2006-06-14
Ah well if you need to edit from the console, hopefully nano will be easy enough to use.  In the bottom of nano where the menu bar is, the ^ sign means CTRL + the key.  To save and exit in nano, hit CTRL-O then CTRL-X

```

sudo nano /etc/X11/xorg.conf

```

---

### Post by nowheretoturn on 2006-06-14
[QUOTE=mindwarp]Ah well if you need to edit from the console, hopefully nano will be easy enough to use.  In the bottom of nano where the menu bar is, the ^ sign means CTRL + the key.  To save and exit in nano, hit CTRL-O then CTRL-X

```

sudo nano /etc/X11/xorg.conf

```[/QUOTE]


Thanks a lot for the help. I now have mouse control. Why is it that Ubuntu assumes that one is using a PS/2 mouse rather than perhaps prompting the user for the answer?

---

### Post by mindwarp on 2006-06-14
I think it is just due to being practical, since I would guess at this point less than .05% of users have a serial mouse.  PS/2 was the standard for quite some time, and now it is uncommon to see anything but a USB or Bluetooth mouse.  Supporting serial by default would almost being analogous to adding choices for CGA and EGA displays, and at some point you run into a definite clutter issue in menu dialogs.  Also serial devices can be a big pain to autodetect, and the distro's that do autodetect them don't always work depending on the mouse etc.

At any rate, glad it fixed the problem!

---

### Post by yossman on 2006-07-30
i posted this yesterday to the ubuntu how-to forum, but it hasn't been cleared yet i guess. ;-)

this afternoon i got help from a friend of mine who knows more about Xorg than i do to assist me in getting a serial mouse working on COM1, while leaving my laptop's trackpoint enabled at the same time.  i had succeeded in getting the serial mouse to replace the trackpoint, but i didn't want it to be an either-or solution.  i'm using a no-name serial mouse with 2 buttons.

i used 'mdetect -v' to ensure that it was seeing the mouse connected to COM1, which is /dev/ttyS0; moving the serial mouse around while mdetect is running is recommended.  our solution requires editing /etc/X11/xorg.conf, and as usual you should make a backup of it first.  using terminal:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.working
sudo gedit /etc/X11/xorg.conf &

```

this opens gedit to edit the xorg.conf file.  my suggestion is to scroll down this file until you see a section for your "Configured Mouse", and remember, not everyone's "Configured Mouse" section is going to look the same.  mine looks like this:

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

```

underneath this 'section', you're going to put a new section:

```

Section "InputDevice"
	Identifier	"Generic Serial Mouse"
	Driver		"mouse"
	Option		"Device"		"/dev/ttyS0"
	Option		"Protocol"		"Microsoft"
	Option		"Emulate3Buttons"	"true"
	Option		"SendCoreEvents"	"true"
EndSection

```

now, further down this same xorg.conf file, there is a section called "ServerLayout".  you need to tell this section about the new mouse you just added.  my "ServerLayout" section looks like this, with the "Generic Serial Mouse" added already:

```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	InputDevice	"Generic Serial Mouse"
EndSection

```

note, you may not have all those entries in your ServerLayout list; the important one in the list above that i added is the line that says 'InputDevice "Generic Serial Mouse"'.

at this point, you should save the xorg.conf file, and close gedit.  if you want to see if your changes worked right away, close all the windows you're working on, then hit 'ctrl-alt-backspace' keyboard combination.  this temporarily shuts down the X interface; you will momentarily see a black screen with a "login:" prompt.  wait a few seconds for X to come back up, which will then present you with your standard graphical login prompt.

at this point, you should be able to move your serial mouse, and it should be moving the cursor.  you should also be able to continue using whatever other mice or pointing devices you had connected to the system at the same time.

i know serial mice are a legacy device that most people do not use anymore.  to me, this isn't so much about 'geez go buy a $5 USB mouse', it's more about getting legacy hardware to work if there isn't anything wrong with it, or if it's the only option you have.  many older systems out there, including laptops, do NOT have USB ports on them; if they also don't have a PS/2 port, or the PS/2 port isn't working, a serial mouse could conceivably be the only pointing device that would work.  luckily, almost every single old laptop/system has at least one serial port on it. ;-)


yossman

---

### Post by nj_86 on 2006-08-05
Hi,
I would like to thank yossman a lot,Even my 6 yr old serial mouse is working fine FINALLY.now i can use linux properly:D 
Regards

---


---
title: "I broke my Ubuntu When I upgraded to Karmic"
date: 2009-09-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Zaney Zebra on 2009-09-10
I'm pretty sure I know what I did wrong buy I don't know how to fix it. ](*,)

I had the ATI drivers installed and forgot to roll back to vga before the upgrade. 

here is part of my xorg.cnfg

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

I have 8.04 on a different drive in the same box so I'm still able to use my system. and see the drive with karmic on it. 

So How do I get the one of the other xorg files to load.. like maybe xorg.conf.failsafe 

Or am I wrong, and need to do something else?


John

---

### Post by overdrank on 2009-09-10
Moved to Karmic Koala Testing and Discussion

---

### Post by kerry_s on 2009-09-10
bummer, it happens, thats why it's alpha.

```
Section "Device"
Identifier "aticonfig-Device[0]-0"
Driver "fglrx"
BusID "PCI:1:5:0"
EndSection

```

to

```
Section "Device"
Identifier "aticonfig-Device[0]-0"
Driver "**vesa**"
BusID "PCI:1:5:0"
EndSection

```

---

### Post by Zaney Zebra on 2009-09-11
When I try to save the edited file I get the message that I do not have permission,  Why not I ask it's my computer! ;).  I'm sure I'm doing this the wrong way. I mounted the drive and clicked over to the xorg file and tried to edit it.

---

### Post by autocrosser on 2009-09-11
try doing:  sudo gedit/"name_of_your_install"/etc/X11/xorg.conf     Remember you need to be the root user to edit that file.

If you can't fix a b0rked install you might wait until it is released--there will plenty of "learning" chances as Karmic is still Alpha..........

---

### Post by Zaney Zebra on 2009-09-11
I'm willing to try to fix it. 

I could take the easy way out and start over but where's the fun in that?

I know it's Alpha. Thats why I have it on a seperate drive so I don't goof up the working stuff

---

### Post by Zaney Zebra on 2009-09-11
well I booted to the root shell and used nano to edit the file.

Thanks  problem solved  using Karmic now! :popcorn:

---


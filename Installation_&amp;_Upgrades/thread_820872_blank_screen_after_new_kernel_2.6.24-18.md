---
title: "blank screen after new kernel 2.6.24-18"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by giovaea on 2008-06-06
I've installed new kernel 2.6.24-18-generic. In previous kernel  2.6.24-16 I have manually installed ATI driver and everything worked OK and now, after reboot : **blank screen**.

I've restarted old kernel.
What have I to do?
    
This is is my  fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 XT AGP
OpenGL version string: 2.1.7415 Release


and /etc/X11/xorg.conf

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "it"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "MaxGARTSize" "256"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


Thank you

---

### Post by ohiomoto on 2008-06-06
I just posted this in another thread, but it might work for you too.  I went through hell trying to clear up my -18 issues. Step one was the key to clearing up my problem. (See link below for more information.)

You can use Synaptic Manager.  Be careful with -18...a lot of us had problems with it.  I kept having strange issues with headers in -18.

Here is what worked for me:

1. Clean out the package cache and history in Synaptic by going to "Synaptic->Settings->Preferences->Files".  Hopefully this will make sure you avoid any issues.  

2.  Go down the list and mark the following packages for installation:```
linux-image-2.6.22-18-generic
linux-headers-2.6.22-18-generic
linux-restricted-modules-2.6.22-18-generic
linux-ubuntu-modules-2.6.22-18-generic
```

If you encounter any problems go back and try removing the installed packages.

Here is a link to my post describing the -18 issues I encountered and the help that I received: [http://ubuntuforums.org/showthread.php?t=818241](http://ubuntuforums.org/showthread.php?t=818241)

---

### Post by giovaea on 2008-06-09
In these days I have tryed to reinstall packages by Synaptic: nothing to do, a blank screen again.
Hi

---


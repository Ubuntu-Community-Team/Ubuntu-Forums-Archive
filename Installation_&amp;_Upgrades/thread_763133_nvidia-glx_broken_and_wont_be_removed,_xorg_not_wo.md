---
title: "nvidia-glx broken and wont be removed, xorg not working properyl"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by Epicuros on 2008-04-22
I upgraded from 6.* to the 8.04 hardy heron. After upgrading I got the message that nvidia-glx was broken. So I tried to remove it for it to be reinstalled and got:
----------------------
dpkg-divert: error checking `/usr/X11R6/lib/libGL.so.1': No such file or directory
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)
-----------------------

Automatic updates is popping up all the time trying to upgrade nvidia-glx but gets:
-----------------------
Could not install '/var/cache/apt/archives/nvidia-glx_1%3a96.43.05+2.6.24.12-16.34_i386.deb'

The upgrade will continue but the '/var/cache/apt/archives/nvidia-glx_1%3a96.43.05+2.6.24.12-16.34_i386.deb' package may be in a not working state. Please consider submitting a bugreport about it.

subprocess pre-installation script returned error exit status 2
-----------------------

And then the automatics updates wants to upgrade it again with same result....

I'm currently using a generic driver for my card (got a nvidia 6600), but would like to be able to use the nvidia drivers..

Before when I had a driver problems I always did 'sudo dpkg-reconfigure -phigh xserver-xorg' which opened a program that guided me through the driver process, but when I do this now I get only:
-------------------------
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080423010644
--------------------------


How shall I do to be able to fix these problems and use my nvidia drivers?
Right now my xorg seems pretty thin =/ :
--------------------------------
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
--------------------------

'sudo dpkg-reconfigure -phigh xserver-xorg' or 'sudo dpkg-reconfigure xserver-xorg' seems to not be working properly since it used to write the xorg.conf properly but now doesnt. Any ideas?

---

### Post by Vic Morgan on 2008-04-23
I've got my own similar problem which seem to be about loading Xorg.conf rather than with Nvidia drivers.To load Nvidia drivers without hassle, use EnvyNG.

---

### Post by Vic Morgan on 2008-04-23
I've got my own similar problem which seem to be about loading Xorg.conf rather than with Nvidia drivers.To load Nvidia drivers without hassle, use EnvyNG. Then look at xorg.conf before you reboot to see the changes that have been made. In my case they are wiped every boot-up.

---

### Post by Dark Horse on 2008-04-23
I am experincing what look to be the same problem Only mine is a fresh install on a new formated partition. I created an iso from the current build the day after the release canadate became available. I can only get a low resoulition 600x800. when I try to install the driver I get the same result that you describe.
My distro is ubuntu Studio hardy 8.4.If that matters. The system is a gigabyte board with nvida gpu built on the board and an amd 2k Processor 3.5gig of memory.
I hope some one knows what to do to fix this.:-k

---

### Post by Epicuros on 2008-04-23
I've found another package called nvidia-glx-new which seems to be some kind of replacement for the nvidia-glx. I'm wondering why they created another glx-package with this suffix, but it might be because of something related to this problem perhaps.

Succesfully installed nvidia-glx-new and its -dev. Still not managed to remove the old nvidia-glx tho and xorg is still not working properly.

---

### Post by Epicuros on 2008-04-23
Correction: nvidia-glx-new doesnt seem to be installed either. It said so first in the synaptic that it was. Later I tried to reach nvidia-xconfig by console, and then got the message that it wasnt installed. Furthermore I then also relized that the nvidia-glx-new wasnt installed either. When I tried to do sudo apt-get install nvidia-glx-new it needed to first remove nvidia-glx in order to do this. The action to remove nvidia-glx was, as before, blocked and so now I'm stuck in a neverending circle of not even being able to install nvidia drivers at all. :(

---

### Post by Epicuros on 2008-04-23
problem solved

1) create an empty /usr/X11R6/lib/libGL.so.1
2) then remove the nvidia-glx as before
3) delete xorg.conf
4) run nvidia-xconfig
5) restart comp (not only x)



tadaaa

---

### Post by Dark Horse on 2008-04-23
[B]that is great![B]I will try that on my computer when I get home tonight. ( if i can figure out how I am still really new at this I hav only had linux about a month):)

---

### Post by Epicuros on 2008-04-23
oh forgot, between 2) and 3): install nvidia-glx-new

---


---
title: "nvidia-glx &quot;GLX not available&quot; (Xubuntu)"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by Dragonfi on 2007-11-11
I tried nearly every way to install the nvidia-glx driver, now I have GUI ,but still cannot use 3D applications, I'm running cicles with it now. 
I'm using Xubuntu.
I get the error message in nvidia-settings, OpenGL/GLX information:
                >    GLX not available: either the GLX extension is not  available on this X server, or there was a proble retrieving GLX information from the X server.
      
This is what my xorg.conf  contain (only the sections I think have an issue with the problem):
   >        

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"Általános videó kártya"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection


Also when I try to  use google earth for example,I get the following:
    > Xlib:  extension "GLX" missing on display ":0.0".
Hope you know a solution to my problem.
Thanks in advance.
and sorry if my english is not perfect.

---

### Post by Dragonfi on 2007-11-11
Problem solved by upgrading to the 7.10 version, possibly  the upgrade replaced the software I messed up....

---


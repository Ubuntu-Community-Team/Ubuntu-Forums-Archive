---
title: "Early install problems"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by phuxed on 2008-01-31
First off I've tried installing from inside windows, on a fresh hard drive, and via direct cd boot, all deriving to the same problem.

Basically the chain of events goes I boot the cd, select install or run ubuntu. it starts its loading process, after it "loads" I get to a black screen and this pops up:

Starting deferred execution scheduler atd [OK]

Starting periodic command scheduler crond [OK]

Checking battery state [OK]

Running local boot scripts (/ect/rc.local) [OK]

--

After this the screen flashes a few times, GUI acts like it is going to load, instead a pop up that says to run in low graphics mode loads up, I can either press continue, or configure the graphics to my drivers. Either one brings me back to the aforementioned black screen above, with the same stuff.

Once I get back to that window for the final time it does nothing, regardless of how long I wait. I can type in this window so I assumed it was a terminal but I couldn't get any commands to execute

Trying to shut down the pc causes a lot of kernel errors to display so I know it isn't locking up.. there has to be an error somewhere.

I tried installing on a virtual machine and everything worked perfectly. I don't know if it's this PC or not, I'm assuming it is. I could make sure by trying it on another pc but I figured I'd post here first to see if the problem is easily fixed.


Thanks in advance, :)

---

### Post by phidia on 2008-01-31
From your desription it sounds like the graphics card isn't being identified. If you try to configure video you should get a program that lets you chose your video card.you can also try to manually edit /etc/X11/xorg.conf. In that file there will be a section that looks like this:

> Section "Device"
	Identifier	"nVidia Corporation NVIDIA Default Card"
	Driver		"nvidia"
	Busid		"PCI:0:18:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
Above is my xorg.conf used as an example.
You want to put something after "Driver" that will work with your card.
You can try the vesa driver but better is what is made to work with your card, and you and the people looking at this thread need to know what that is.

---


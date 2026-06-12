---
title: "Reinstall Ubuntu Feisty"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by Neuralgia on 2007-04-27
somehow trying to install beryl, I crashed ubuntu (I had it working 100% in edgy, but after upgrading to Feisty
 it's down) 

i get a blue screen with lots of letters, saying something about X, and nothing happens.

I can load in recovery mode, but since I'm a complete n00b, don't know what to do.

I though there is a way to REINSTALL ubuntu... there has to be a way, and if there isn't, it SUCKS.

As of now, I'm downloading the Feisty CD (since I upgraded I don't have it)... thought that would work.

---

### Post by zvacet on 2007-04-27
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")


You don´t need to type sudo because in recovvery modde you are root allready.

---

### Post by Neuralgia on 2007-04-28
thanks... I knew my kernel was working ok, but GNOME was the one having problems.

NOw I just have to find the perfect config and install all drivers for my ATI x300 card and my dell monitor.

EDIT: my ati card is working perfectly, but my monitor is having some trouble. Before, I had my screen resolution with 1280x1024 and 75Hz of refresh rate... now my resoultion is back to normal BUT, my refresh rate is stucked at 60Hz...

How do I change this?

---

### Post by fwojciec on 2007-04-28
I assume that you fixed the problem by doing dpkg-reconfigure... That probably set your monitor settings to default.  The easiest thing is to manually edit /etc/X11/xorg.conf file and enter the correct refresh rate ranges for your monitor (you'll have to find out what these are, for my monitor I just go to the Viewsonic webpage and look up the spec sheet for VA902B).  Below is the relevant section from my xorg.conf - you'll have to edit the values in bold.

> Section "Monitor"
	Identifier	"ViewSonic VA902B"
	Option		"DPMS"
	[B]HorizSync	30-82
	VertRefresh	50-85[/B]
EndSection

---

### Post by Neuralgia on 2007-04-28
actually i fixed it running again dpkg-reconfigure, and placing the settings of my Dell 173FP monitor.

Did the xorg.conf edit to double check if everything was OK

---


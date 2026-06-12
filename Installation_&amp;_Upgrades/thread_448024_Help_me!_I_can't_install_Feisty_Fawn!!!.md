---
title: "Help me! I can't install Feisty Fawn!!!"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by chevanton87 on 2007-05-18
At first, excuse me for my bad english. I'm new in the great world of linux and Ubuntu 7.04 is the first version of linux's distro that I'm trying to install. Now, the problem: I insert the CD in my reader (at the boot) and speedly appears a choice screen (firstly I must say that the cd works fine). I choose the first option ("Start and Install"). After few seconds appears a blue screen (with strange symbols, like an error's screen) which informs me that the server X can't be loaded and appears the problem too: "fatal error, no screens found". Then I can only utilize the shell.
I've seen in other forums, but it might strange (accourding to users of much forums) that I neither can't use the 
the live cd version mode. Help me. I Remember to you that I've an Amilo Pi1536 Core Do with a graphicboard Mobility Radeon X1400. I write this 'couse I think that the graphicboard is the problem, but I don't know what I must do.
HELP ME!

---

### Post by merlinus on 2007-05-18
Did you try "Safe Mode" at the first prompt?

-merlin

---

### Post by stchman on 2007-05-18
> **chevanton87 said:**
> At first, excuse me for my bad english. I'm new in the great world of linux and Ubuntu 7.04 is the first version of linux's distro that I'm trying to install. Now, the problem: I insert the CD in my reader (at the boot) and speedly appears a choice screen (firstly I must say that the cd works fine). I choose the first option ("Start and Install"). After few seconds appears a blue screen (with strange symbols, like an error's screen) which informs me that the server X can't be loaded and appears the problem too: "fatal error, no screens found". Then I can only utilize the shell.
I've seen in other forums, but it might strange (accourding to users of much forums) that I neither can't use the 
the live cd version mode. Help me. I Remember to you that I've an Amilo Pi1536 Core Do with a graphicboard Mobility Radeon X1400. I write this 'couse I think that the graphicboard is the problem, but I don't know what I must do.
HELP ME!

Sounds like you downloaded a bad .iso.  Try downloading the .iso again and burn at a slow speed like 16X.

---

### Post by chevanton87 on 2007-05-18
I've tryed the safe mode. Moreover the cd is ok 'couse i've try the same one on another pc and it works correctly. it's very strange!!!

---

### Post by chevanton87 on 2007-05-19
up

---

### Post by Ub1476 on 2007-05-19
This is a known bug.. It should be posted a sticky or something about this, since it after all makes many newb unable to install Ubuntu.

Anyways bug discussed here:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853)

Guide to fix the problem here:
[https://bugs.launchpad.net/ubuntu/+s...945/comments/1](https://bugs.launchpad.net/ubuntu/+s...945/comments/1)

**How to fix it:**

When you have gotten the error message, click no to view details so you'll end up in the terminal. Press enter to log in. Write:

```
sudo nano /etc/X11/xorg.conf
```

In the "Monitor" section add the following lines:

```
HorizSync                36-52
VertRefresh              36-60
```

It should look like this:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	36-52
	Vertrefresh	36-60
EndSection
```

Now go to the "Screen" section. Remove all other resolution than "640x480". So it will look like this:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"640x480"
	EndSubSection
EndSection
```

Click F2 to save and quit. Now write:
```
sudo killall gdm
sudo gdm
``` Ubuntu should now start. Install Ubuntu. When Ubuntu is installed go to terminal and write: 

```
sudo apt-get update
sudo apt-get upgrade
```

Now go to System>Administration>Enable Restricted Drivers Manager. Check the unchecked graphic driver. Go back to the terminal and write

```
sudo gedit /etc/X11/xorg.conf
```

Add your default resolution you removed earlier in the guide. If 1280x800 is your resolution it should look like this:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x800"    "640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x800"    "640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x800"    "640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x800"    "640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x800"    "640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x800"    "640x480"
	EndSubSection
EndSection
```

Click on save and exit. Restart Ubuntu, and everything should be working _perfect_ now. Hope this helps:)

---

### Post by chevanton87 on 2007-05-19
I MUST build a gold statue in the first square of my city for you!!! Now all works correctly!!! Thanks you!:lolflag:

---

### Post by Ub1476 on 2007-05-19
No problem. Glad to help:)

---

### Post by Mr_Congeniality on 2007-05-22
Won't restarting Ubuntu get rid of this configuration when it isn't installed?

---


---
title: "OpenOffice + Nvidia driver = broken for me"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Hatfield on 2008-10-24
I still consider myself a  Linux noob although I'm definitely getting more fluent.

Backstory: 2 days ago I did a clean install of Kubuntu Ibex Beta on my homegrown PC(P5NEsli, C2D E6650, 4GB RAM, [Nvidia 7600GT](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130062)).  I did not initially activate any Nvidia driver or try desktop effects.  When I would open OpenOffice without any Nvidia driver activated, it would open fine and not mess anything up.

I decided to try desktop effects although I have never had much luck with it on various machines.  I just haven't delved far enough into it.

So I activated the Version 177(Recommended) Nvidia driver.   Then when I would open and maximize OpenOffice, whenever I drag my cursor over the task bar, parts of it(background, K icon, home folder, programs, blocks of background, etc) would disappear/reappear/flash/etc.   And they would reappear(or some of it) when I dragged my cursor off the taskbar.  I would minimize OpenOffice to the tray and everything would revert to normal behavior and work fine.  Tried just minimizing the OpenOffice window to a smaller size and my desktop starts acting up too(Desktop window and Notes Plasmoid turn kind of psychedelic and sometimes the wallpaper disappears entirely only to show a black screen.)

Tried Version 173 Nvidia driver with the same effect.

Tried Version 93 Nvidia driver and the system would only reboot into recovery console.  Installed envyng-gtk from the recovery console and ran it from the text format to reinstall Version 177 driver and I'm right back where I started.

The problem seems to be limited to OpenOffice.
Any ideas?  Any help is appreciated.

---

### Post by FuturePilot on 2008-10-24
I have a feeling this may be related to this:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904")

---

### Post by Hatfield on 2008-10-24
> **FuturePilot said:**
> I have a feeling this may be related to this:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904")

Yahtzee!  Guess I just have to wait for a fix.

---

### Post by Hatfield on 2008-10-24
I took a screenshot to show everyone my problem.

---

### Post by FuturePilot on 2008-10-24
Hmmm. Maybe it's not that bug. Not sure really, that is very odd though.

---

### Post by Hatfield on 2008-10-24
> **FuturePilot said:**
> Hmmm. Maybe it's not that bug. Not sure really, that is very odd though.

I know, right?
And it doesn't happen until I activate an Nvidia driver.  Right after a fresh install(2 in the last 2 weeks) and before activating an Nvidia driver, I do not have this problem with OpenOffice.  It's only after I go into Hardware Drivers and activate Version 173 or 177 that I get this problem.  (Version 96 leads to incomplete boot and Recovery Console).

And the problem is ONLY with OpenOffice word processor.  Not spreadsheet or presentation.

---

### Post by Hatfield on 2008-10-24
Hmmmmm.  I'm wondering.  Could it be that I have outdated Java or something?

```
hatfield@homegrown:~$ java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) 64-Bit Server VM (build 11.0-b15, mixed mode)
hatfield@homegrown:~$

```

Or is that Java up-to-date?

---

### Post by Cenotaph on 2008-10-24
Try the following to see if it helps.

Edit your /etc/X11/xorg.conf file

and add the line

Option	"RenderAccel"	"False"

in the nvidia driver section.

---

### Post by Hatfield on 2008-10-24
> **Cenotaph said:**
> Try the following to see if it helps.

Edit your /etc/X11/xorg.conf file

and add the line

Option	"RenderAccel"	"False"

in the nvidia driver section.
Would that be under Section "Device" at the bottom just under Driver "nvidia"?
```
hatfield@homegrown:~$ kate /etc/X11/xorg.conf
```
```

........
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier     "Configured Monitor"
EndSection

Section "Screen"
	Identifier     "Default Screen"
	Device         "Configured Video Device"
	Monitor        "Configured Monitor"
	Option         "NoLogo" "True"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
		Modes      "nvidia-auto-select"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "keyboard"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
	Identifier     "Configured Video Device"
	Driver	"nvidia"
EndSection

```

---

### Post by Cenotaph on 2008-10-24
I think so, im not sure as that xorg.conf is quite different than mine. If it doesn't work try in the screen section below "NoLogo" "true" option

---

### Post by Hatfield on 2008-10-24
> **Cenotaph said:**
> I think so, im not sure as that xorg.conf is quite different than mine. If it doesn't work try in the screen section below "NoLogo" "true" option

We may be on to something.  I put that line at the very end below Driver	"nvidia"
and I must admit that the problem is not as bad or as frequent as before.  But it is still there.

And just so I understand, what did I do by adding that line?

---

### Post by Cenotaph on 2008-10-24
You disabled Render Acceleration, it's supposed to make GUI rendering faster in X with nvidia driver, but seems to be still a little buggy as i was experiencing a problem in the window decoration when using compiz, which is why i suggested it.

But if it still happens that shouldn't be the problem, at least not the only one, in your case.

---

### Post by Hatfield on 2008-10-25
That line caused my Flash to flake out and it didn't seem to fix anything so I removed it.
Found the actual bug reports:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/253844](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/253844)
[http://bugs.kde.org/show_bug.cgi?id=157017](http://bugs.kde.org/show_bug.cgi?id=157017)

Glad to know I'm not the only one.  And it's not the Ubuntu developers' problem, but Nvidia's problem.  The Nvidia drivers cause Plasma to go nutty.

---


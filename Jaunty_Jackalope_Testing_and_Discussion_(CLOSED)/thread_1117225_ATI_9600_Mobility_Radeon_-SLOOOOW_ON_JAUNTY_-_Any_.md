---
title: "ATI 9600 Mobility Radeon -SLOOOOW ON JAUNTY - Any Suggestions?"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by crjackson on 2009-04-05
Wow... I installed Jaunty on my older laptop and boy is the video performance poor.  Does anyone have advice on how to pep it up a little?

Thanks

2Ghz Athlon 64, 1.25MB Ram, 7200 RPM HD, ATI Mobility Radeon 9600

---

### Post by crjackson on 2009-04-05
Any One?

---

### Post by crjackson on 2009-04-06
... kerplunk!

---

### Post by krazyd on 2009-04-06
> **crjackson said:**
> ... video performance poor.What do you mean? Compared to intrepid? Video playback, window resizing or 3d? KDE or Gnome? fglrx driver or radeon?

Let's get some specifics! :D

---

### Post by crjackson on 2009-04-07
> **krazyd said:**
> What do you mean? Compared to intrepid? Video playback, window resizing or 3d? KDE or Gnome? fglrx driver or radeon?

Let's get some specifics! :D

* Video Playback - Slow, Choppy, Tearing

* Window Resizing - Slow, Tearing on moving a window

* Anything 3D - Slow, Choppy, Tearing

* Gnome

* Open source ATI driver I'm guessing- There is no proprietary driver for this card in Intrepid or Jaunty.

---

### Post by psyke83 on 2009-04-07
> **crjackson said:**
> * Video Playback - Slow, Choppy, Tearing

* Window Resizing - Slow, Tearing on moving a window

* Anything 3D - Slow, Choppy, Tearing

* Gnome

* Open source ATI driver I'm guessing- There is no proprietary driver for this card in Intrepid or Jaunty.

You still didn't answer whether it's slow in general or slow compared to Intrepid.

Anyway, the information you need can be found in "man radeon".

I suggest you start with these tweaks to your xorg.conf:

```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"exa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"AccelDFS"		        "true"
EndSection
```

---

### Post by krazyd on 2009-04-07
@psyke: I think that in Jaunty [EXA is enabled by default]("https://lists.ubuntu.com/archives/jaunty-changes/2008-December/002069.html").

And in fact, this might be your problem crjackson. 

> **crjackson said:**
> * Video Playback - Slow, Choppy, Tearing

* Window Resizing - Slow, Tearing on moving a window

* Anything 3D - Slow, Choppy, Tearing

* Gnome

I have heard that the older radeons like yours have some problems with EXA. Try adding to the Device section of your xorg.conf (remove any other AccelMethod lines):
```
AccelMethod    "XAA"
```

> **crjackson said:**
> 
* Open source ATI driver I'm guessing- There is no proprietary driver for this card in Intrepid or Jaunty.
Ah yes, I had forgotten that.

---

### Post by crjackson on 2009-04-07
> **psyke83 said:**
> You still didn't answer whether it's slow in general or slow compared to Intrepid.

Anyway, the information you need can be found in "man radeon".

I suggest you start with these tweaks to your xorg.conf:

```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"exa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"AccelDFS"		        "true"
EndSection
```

Slow compared to Hardy. I couldn't run Intrepid due to the same slowness. I'll try  your suggestions,  that's  what I was looking for.

---

### Post by crjackson on 2009-04-07
> **krazyd said:**
> @psyke: I think that in Jaunty [EXA is enabled by default]("https://lists.ubuntu.com/archives/jaunty-changes/2008-December/002069.html").

And in fact, this might be your problem crjackson. 


I have heard that the older radeons like yours have some problems with EXA. Try adding to the Device section of your xorg.conf (remove any other AccelMethod lines):
```
AccelMethod    "XAA"
```


Ah yes, I had forgotten that.

I'll try that too. Thanks much.

---

### Post by crjackson on 2009-04-09
Thanks for the suggestions. I tried both methods and saw no difference between them.

However... I installed 207 updates today and I did notice a SLIGHT improvement.

If you think of anything else I might try let me know. I would really love to run Jaunty on this system if possible.

---

### Post by simonjp on 2009-04-10
> **crjackson said:**
> Wow... I installed Jaunty on my older laptop and boy is the video performance poor.  Does anyone have advice on how to pep it up a little?

Thanks

2Ghz Athlon 64, 1.25MB Ram, 7200 RPM HD, ATI Mobility Radeon 9600

I have an old HP NC8000 with Radeon Mobility 9600 and upgrading from Intrepid to Jaunty has resulted in slower graphical redraws compared to Intrepid.

Mainly simple things like minimising and maximising windows and clicking on the menu bar drop down lists - there is a one or two second delay after clicking the mouse (no problems in 8.10).  Although strangely video playback is fine but I have lost all audio.

I tend to just check for updates every day to see if a fix has been released.

---

### Post by crjackson on 2009-04-10
> **simonjp said:**
> I have an old HP NC8000 with Radeon Mobility 9600 and upgrading from Intrepid to Jaunty has resulted in slower graphical redraws compared to Intrepid.

Mainly simple things like minimising and maximising windows and clicking on the menu bar drop down lists - there is a one or two second delay after clicking the mouse (no problems in 8.10).  Although strangely video playback is fine but I have lost all audio.

I tend to just check for updates every day to see if a fix has been released.

And Intrepid is MUCH slower than Hardy on this machine. I plan to play with Jaunty for a while, then I'll probably go back to Hardy unless someone comes up with a way to speed this thing up.

---

### Post by mkulke on 2009-04-20
> **psyke83 said:**
> You still didn't answer whether it's slow in general or slow compared to Intrepid.

Anyway, the information you need can be found in "man radeon".

I suggest you start with these tweaks to your xorg.conf:

```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"exa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"AccelDFS"		        "true"
EndSection
```

thanks, i have an "ati mobility radeon 9200" and this actually helped somewhat (= made gnome usable in jaunty again).

---

### Post by tanari on 2009-04-20
I have Radeon HD3200
I have the same problem, but only with video :(.

I reported bug to launchpad
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/363613](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/363613)

---

### Post by crjackson on 2009-04-20
> **mkulke said:**
> thanks, i have an "ati mobility radeon 9200" and this actually helped somewhat (= made gnome usable in jaunty again).

Actually I believe those are supposed to be the default settings already. I'll try again with your exact entries and see what happens.

---

### Post by psyke83 on 2009-04-20
> **crjackson said:**
> Actually I believe those are supposed to be the default settings already. I'll try again with your exact entries and see what happens.

The "EXAOptimizeMigration" option isn't default for the vanilla Xorg server, though Ubuntu may have patched it. Nevertheless, I notice that the "greedy" MigrationHeuristic is faster anyway.
```

Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"exa"
	Option		"MigrationHeurisitc"		"greedy"
	Option		"AccelDFS"		        "true"
EndSection
```

---

### Post by crjackson on 2009-04-20
> **psyke83 said:**
> The "EXAOptimizeMigration" option isn't default for the vanilla Xorg server, though Ubuntu may have patched it. Nevertheless, I notice that the "greedy" MigrationHeuristic is faster anyway.
```

Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"exa"
	Option		"MigrationHeurisitc"		"greedy"
	Option		"AccelDFS"		        "true"
EndSection
```

Okay, I'll paste this in and see what happens. Is there any tool I can use to get a benchmark of before /  after. I realize that glxgears is pretty useless except to see if you actually have 3D working, so I wonder if there is something else I can use to compare.

---

### Post by psyke83 on 2009-04-20
> **crjackson said:**
> Okay, I'll paste this in and see what happens. Is there any tool I can use to get a benchmark of before /  after. I realize that glxgears is pretty useless except to see if you actually have 3D working, so I wonder if there is something else I can use to compare.

EXA deals mostly with 2D acceleration - tasks like scrolling a website in Firefox are good tests.

Otherwise, you can try PlanetPenguin Racer for 3D performance (turn on the FPS counter).

---

### Post by crjackson on 2009-04-20
> **psyke83 said:**
> EXA deals mostly with 2D acceleration - tasks like scrolling a website in Firefox are good tests.

Otherwise, you can try PlanetPenguin Racer for 3D performance (turn on the FPS counter).

Great. I can't wait to get home from work and try this out.

---

### Post by raido357 on 2009-04-20
Option      "AccelDFS" "on"
    Option      "AccelMethod"  "XAA"
    Option      "MigrationHeuristic"  "smart" # "greedy" works well also
    Option      "EnablePageFlip"  "on"
    Option      "EnableDepthMoves"  "on"
    Option      "ColorTiling"  "on"
    Option      "FBTexPercent"  "0"
    Option      "RenderAccel"  "on"

Radeon 9600 here too (HP NC6000) // those settings fixed it, glxgears 1040fps after those lines 1500 fps and 2D smooth.

---

### Post by crjackson on 2009-04-20
> **raido357 said:**
> Option      "AccelDFS" "on"
    Option      "AccelMethod"  "XAA"
    Option      "MigrationHeuristic"  "smart" # "greedy" works well also
    Option      "EnablePageFlip"  "on"
    Option      "EnableDepthMoves"  "on"
    Option      "ColorTiling"  "on"
    Option      "FBTexPercent"  "0"
    Option      "RenderAccel"  "on"

Radeon 9600 here too (HP NC6000) // those settings fixed it, glxgears 1040fps after those lines 1500 fps and 2D smooth.

Nice - This thread is really starting to produce some good pointers. I'll be hitting all of them shortly and post back with the results. The worst thing about all of this is that I too, used to use glxgears as a basic benchmark. This thing used to give me over 3000 fps in Hardy.

Now I just want it to be smooth when using, the numbers be damned.

---

### Post by crjackson on 2009-04-21
> **psyke83 said:**
> The "EXAOptimizeMigration" option isn't default for the vanilla Xorg server, though Ubuntu may have patched it. Nevertheless, I notice that the "greedy" MigrationHeuristic is faster anyway.
```

Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"exa"
	Option		"MigrationHeurisitc"		"greedy"
	Option		"AccelDFS"		        "true"
EndSection
```

Okay, this was a good boost. Even glxgears agrees showing 1800fps.

---

### Post by crjackson on 2009-04-21
> **raido357 said:**
> Option      "AccelDFS" "on"
    Option      "AccelMethod"  "XAA"
    Option      "MigrationHeuristic"  "smart" # "greedy" works well also
    Option      "EnablePageFlip"  "on"
    Option      "EnableDepthMoves"  "on"
    Option      "ColorTiling"  "on"
    Option      "FBTexPercent"  "0"
    Option      "RenderAccel"  "on"

Radeon 9600 here too (HP NC6000) // those settings fixed it, glxgears 1040fps after those lines 1500 fps and 2D smooth.

This was a HUGE boost! glxgears now just under 3000fps.

These are the settings I'll keep. Full screen flash is still SLIGHTLY choppy but I can live with it. As time and fixes march on, who knows, it may smooth all the way out.

This is where I'm locking it down, I've now decided to keep Jaunty on this particular notebook.  Thanks to everyone for all the suggestions.

---

### Post by Jingo on 2009-04-21
I think its this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/363238](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/363238)

Please add some comments there.

---

### Post by tanari on 2009-04-22
I have also another bug, don't know how to describe it well:
videos are not sync (video can blink, top and bottom halfs of video are little bit different for second). 
In previous ubuntu I simply set "vsync=on" in compiz, but in 9.04 it doesn't help.

---

### Post by crjackson on 2009-04-22
> **tanari said:**
> I have also another bug, don't know how to describe it well:
videos are not sync (video can blink, top and bottom halfs of video are little bit different for second). 
In previous ubuntu I simply set "vsync=on" in compiz, but in 9.04 it doesn't help.

I suggest you start a separate thread for this, and be more specific about your hardware and the problem.

---

### Post by ssam on 2009-04-22
glxgears is a bad benchmark.
[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

try gktperf for 2d, and ppracer for 3d

for me on a radeon hd 3650 the opensource drivers are pretty smooth for 2d and 720p video in jaunty. video was a bit jerky in intrepid.

---


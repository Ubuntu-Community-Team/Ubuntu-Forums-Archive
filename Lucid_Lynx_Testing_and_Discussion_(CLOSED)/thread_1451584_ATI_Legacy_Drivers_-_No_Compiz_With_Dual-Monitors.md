---
title: "ATI Legacy Drivers - No Compiz With Dual-Monitors"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by The Recorder on 2010-04-10
Compiz will not start with the dual-monitor, 2048x768 setup I have. When I use only one screen (monitor), compiz works perfectly.  THIS WAS NOT THE CASE UNTIL THE BETA 2 COMPIZ UPGRADES.  I have a legacy ATI Radeon legacy card (X700) and am using the Radeon legacy drivers.

Odd thing is that the compiz script, "compiz-check", done under the dual-monitor setup, returns the following:

*************

Gathering information about your system...

Distribution: Ubuntu 10.04
Desktop environment: GNOME
Graphics chip: ATI Technologies Inc RV410 [Radeon X700 (PCIE)]
Driver in use: radeon
Rendering method: AIGLX

Checking if it's possible to run Compiz on your system...

Checking for texture_from_pixmap... [ OK ]
Checking for non power of two support... [ OK ]
Checking for composite extension... [ OK ]
Checking for FBConfig... [ OK ]
Checking for hardware/setup problems... [ OK ]

*************

Anyone have any ideas/suggestions?

Thanks...

---

### Post by The Recorder on 2010-04-10
Difficult to believe that there is no one out there using the Legacy Radeon Driver on dual-monitors.  Can't one of these nonexistent people at least tell me if they're not having any problem - Give me some hope...  Please...

---

### Post by Longinus00 on 2010-04-11
I have no idea what you're talking about with regards to legacy drivers but I suspect you actually mean the the really good actively being developed and supports kms open source drivers. Anyway, your card doesn't support a texture larger than 2048x2048 and compiz doesn't have any way of working around a limitation like that.

If this used to work in previous versions of compiz then you really ought to try hunting down the changelog and see what was edited to make your setup not work anymore. A change which reduces the max texture size by 1 would be enough to give you a problem.

---

### Post by The Recorder on 2010-04-11
The following are the results from three queries that I make before attempting to start compiz:


FIRST-
arthur@arthur-desktop:~$ xdpyinfo  | grep 'dimensions:'
  dimensions:    2048x768 pixels (542x203 millimeters)


SECOND-
arthur@arthur-desktop:~$ xrandr | grep '*'
   1024x768       75.1     75.0     70.1     60.0* 
   1024x768       75.1*    70.1     60.0  


THIRD-
arthur@arthur-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV410 [Radeon X700 (PCIE)]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


AFTER THE ABOVE CHECKS, THIS IS WHAT I GET IF I ATTEMPT TO START COMPIZ WITHOUT CHECKS:
arthur@arthur-desktop:~$ SKIP_CHECKS=yes compiz --replace &
[1] 2442
arthur@arthur-desktop:~$ compiz (core) - Warn: Exceeded max texture size

Launching fallback window manager


AFTER THE ABOVE CHECKS, WHAT I GET IF I ATTEMPT TO START COMPIZ THE NORMAL WAY, THROUGH "APPEARANCE PREFERENCES" > "VISUAL EFFECTS" IS:

If I check "Normal" > "Searching for available drivers"; "Keep settings?" (With no visible changes made); and then the eventual freezing of the "Keep settings?" dialog box, whether I click on "Keep settings", or not.

If I check "Extra" > Either the same as "Normal", or a "Desktop effects could not be enabled" box.

Any more ideas?

Thanks

---

### Post by Longinus00 on 2010-04-11
> **The Recorder said:**
> 
arthur@arthur-desktop:~$ compiz (core) - Warn: Exceeded max texture size


I already told you your card can't support anything more than 2048x2048 and I'm not sure how it handles the borderline cases. If you reduced the resolution of one of your monitors you'll find that it'll work perfectly. Has compiz ever worked at this resolution before?

---

### Post by The Recorder on 2010-04-11
As I stated above, I am running less than 2048x2048. I am runniing 2048x768!

FIRST-
arthur@arthur-desktop:~$ xdpyinfo | grep 'dimensions:'
dimensions: 2048x768 pixels (542x203 millimeters)

And, as I stated at the beginning of my initial post:

"Compiz will not start with the dual-monitor, 2048x768 setup I have. When I use only one screen (monitor), compiz works perfectly. THIS WAS NOT THE CASE UNTIL THE BETA 2 COMPIZ UPGRADES."

I have been using this setup for at least the last two years.

---

### Post by The Recorder on 2010-04-11
Just got a reply in a thread I satrted in the Compiz Community Forums that this is an Ubuntu bug that has been fixed - Too bad it hasn't fixed it for me.

[http://forum.compiz.org/viewtopic.php?f=86&t=12476](http://forum.compiz.org/viewtopic.php?f=86&t=12476)

[http://changelogs.ubuntu.com/changelogs/pool/main/c/compiz/compiz_0.8.4-0ubuntu15/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/c/compiz/compiz_0.8.4-0ubuntu15/changelog)

---

### Post by The Recorder on 2010-04-11
But, perhaps the solution to this bug will be my solution...  I can only hope

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/554106](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/554106)

---

### Post by Longinus00 on 2010-04-12
> **The Recorder said:**
> As I stated above, I am running less than 2048x2048. I am runniing 2048x768!

FIRST-
arthur@arthur-desktop:~$ xdpyinfo | grep 'dimensions:'
dimensions: 2048x768 pixels (542x203 millimeters)

And, as I stated at the beginning of my initial post:

"Compiz will not start with the dual-monitor, 2048x768 setup I have. When I use only one screen (monitor), compiz works perfectly. THIS WAS NOT THE CASE UNTIL THE BETA 2 COMPIZ UPGRADES."

I have been using this setup for at least the last two years.

This is why I wrote in my original reply
> **Longinus00 said:**
> If this used to work in previous versions of compiz then you really ought to try hunting down the changelog and see what was edited to make your setup not work anymore. A change which reduces the max texture size by 1 would be enough to give you a problem.

Remember that to a computer, 2048 is not < 2048, it's <= ! Ubuntu guys apparently made the same mistake.

---


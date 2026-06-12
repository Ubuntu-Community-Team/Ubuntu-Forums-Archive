---
title: "Is there a place.."
date: 2008-06-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by xaenyx on 2008-06-19
Where I can post a bunch of little problems/fixes for those problems?  After installing ibex, there have been a couple problems (specific to an application like avant-window-navigator and songbird) that I've encountered, and it would be nice to report them.

---

### Post by ronacc on 2008-06-19
this is the place , welcome to the crew.

if they are bugs report them on launchpad .

edit: here is a link     [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

---

### Post by ShirishAg75 on 2008-06-19
you can report bugs here as well as on [http://bugs.launchpad.net](http://bugs.launchpad.net). Of course you'll have to register there if you want to put up a bug. 

Also Intrepid is in heavy development os its better we report here rather than in the issue tracker/bugzilla whatever we call it.

---

### Post by xaenyx on 2008-06-20
oops, whars the delete button

---

### Post by xaenyx on 2008-06-20
k, so here are a couple bugs I can remember off the top of my head (there are more, but I'd have to dig down to remember what they were:

**avant-window-navigator**
*PROBLEM*: Can't change icon
*SOLUTION*: cd to / before starting, try making a shellscript in /usr/bin/awn:
```

#!/bin/bash
cd /
avant-window-navigator

```

**Xorg**
*PROBLEM*: Ubuntu still doesn't come shipped with libc and such (must install build-essential), and it doesn't have patch.  Needs both to apply [this patch to get NVidia video cards to work]("http://ubuntuforums.org/showthread.php?t=833633")
*SOLUTION*: sudo apt-get install build-essential patch

*PROBLEM*: After applying all patches for video cards, ubuntu still won't detect the correct screen resolution.
*SOLUTION*: Find the monitor handbook/guide, and get the correct horizontal/vertical refresh rates and supported resolutions.  Next, do the following:
[LIST=1]
[*]~$ sudo su
[*]~# cvt 1024 768 (where 1024 768 = 1024x768 = desired resolution)
1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
**Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync**
[*]~# gedit /etc/X11/xorg.conf &
[/LIST]

Now, in the Monitor section, add the following, replacing the HorizSync and VertRefresh with the values for your monitor, and the ModeLine with the value you got from the cvt command:
```

HorizSync       30.0 - 72.0
VertRefresh     50.0 - 130.0
ModeLine        **_"1024x768_60.00"_   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync**

```

After that, make sure there is a subsection Display in the Screen section.  It should look something like this:

```

    SubSection     "Display"
#		Viewport	0	0
    Modes      _"1024x768_60.00"_
    EndSubSection

```

Again, replace the "1024x768_60.00" with the appropriate value obtained  at the start of the Modeline, underlined.

---

### Post by Raptor45 on 2008-06-20
This forum is not designed to be a bug tracker. Please report these problems and your solutions to launchpad, if they are not already there. It is designed to track bugs, and people will go there to look for solutions if they have a problem with a given program.

There are simply far too many things that will go wrong throughout the development process to keep track of all kinds of minor issues in the thousands of packages in Ubuntu, which is what Launchpad is designed to manage.

---

### Post by ronacc on 2008-06-20
the xorg thing is not a bug , you are not expected to build things in ubuntu hence build-essentials and patch are not installed by default . the nvidia driver is normaly handled by the restriced modules , intrepid is not even alpha yet so it is very incomplete .

---

### Post by ronacc on 2008-06-20
added info you can set your display mode with nvidia-settings (available in synaptic) nvidia setings would have been installed automaticly if the restricted modules were complete and you had enabled the nvidia driver the normal way . note: when ever you get dumped into low graphics mode it trashes your xorg.conf so once you get it the way you want it back it up and keep your b/u handy .

---

### Post by xaenyx on 2008-06-20
> **ronacc said:**
> added info you can set your display mode with nvidia-settings (available in synaptic) nvidia setings would have been installed automaticly if the restricted modules were complete and you had enabled the nvidia driver the normal way . note: when ever you get dumped into low graphics mode it trashes your xorg.conf so once you get it the way you want it back it up and keep your b/u handy .

Problem was that the nvidia drivers would not install the normal way (the driver manager didn't detect any hardware that is supported, even though it did in hardy)..  If you see that thread I linked to, you know that there is a patch for the nvidia drivers that is needed, but that it will not even patch by default until you install build-essentials and patch, and even then your xorg.conf is still trashed..

> you are not expected to build things in ubuntu hence build-essentials and patch are not installed by default
I still don't understand why it's not included by default.  Ubuntu is the only distro I can think of that does not include it, and leaving it out has zero advantage.

---

### Post by Raptor45 on 2008-06-20
> **xaenyx said:**
> Problem was that the nvidia drivers would not install the normal way (the driver manager didn't detect any hardware that is supported, even though it did in hardy)..  If you see that thread I linked to, you know that there is a patch for the nvidia drivers that is needed, but that it will not even patch by default until you install build-essentials and patch, and even then your xorg.conf is still trashed..


I still don't understand why it's not included by default.  Ubuntu is the only distro I can think of that does not include it, and leaving it out has zero advantage.

None of this is at all unusual; it is not expected that things will "just work" like in Hardy. The nvidia drivers for the new kernel simply have not found their way into the repositories yet and will be fixed in due time.

Whether build-essential should be installed by default is another discussion entirely, although I support that there is no need for it in a default installation for the average user. For advanced users who require the ability to build software, its just a mouse click away.

---

### Post by Eclipse. on 2008-06-20
> **xaenyx said:**
> I still don't understand why it's not included by default.  Ubuntu is the only distro I can think of that does not include it, and leaving it out has zero advantage.

Remember a CD will only hold 700 mb of data.;)

---

### Post by RAOF on 2008-06-20
> **xaenyx said:**
> ...
**Xorg**
...
*PROBLEM*: After applying all patches for video cards, ubuntu still won't detect the correct screen resolution.
*SOLUTION*: Find the monitor handbook/guide, and get the correct horizontal/vertical refresh rates and supported resolutions.  Next, do the following:
[LIST=1]
[*]~$ sudo su
[*]~# cvt 1024 768 (where 1024 768 = 1024x768 = desired resolution)
1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
**Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync**
[*]~# gedit /etc/X11/xorg.conf &
[/LIST]

Now, in the Monitor section, add the following, replacing the HorizSync and VertRefresh with the values for your monitor, and the ModeLine with the value you got from the cvt command:
```

HorizSync       30.0 - 72.0
VertRefresh     50.0 - 130.0
ModeLine        **_"1024x768_60.00"_   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync**

```

After that, make sure there is a subsection Display in the Screen section.  It should look something like this:

```

    SubSection     "Display"
#		Viewport	0	0
    Modes      _"1024x768_60.00"_
    EndSubSection

```

Again, replace the "1024x768_60.00" with the appropriate value obtained  at the start of the Modeline, underlined.

Bear in mind that this isn't a panacea.  Doing this will actually break some drivers.  Some drivers that use XrandR 1.2 (I have experience with nouveau) will fail to work *at all* with a modeline present.  It disrupts their monitor detection, or some such.

> **xaenyx said:**
> ...
I still don't understand why it's not included by default.  Ubuntu is the only distro I can think of that does not include it, and leaving it out has zero advantage.

There are several advantages.  Not shipping a compiler + minimal dev environment saves megabytes from the CDs; this is non-trivial.  Also, not having a build-system installed is marginally more secure than having one installed.

---

### Post by curtis on 2008-06-20
Not shipping a compiler by default is a more sane option that bundling it and having x tools available if someone does get access to your computer system.

You need to save space on a CD to fit it on a CD as well to support it easier (less packages).

Ubuntu 8.10 is under heavy development at the moment and a lot of ABI changes will occur due to GCC being changed from 4.2 to 4.3 (a good thing for core 2 duo and other new technologies)

plus X org is picking up some good development since it is modular now it is easier to work on.

Gnome seems to be coming along good as well.

Ubuntu should of been LTS as it is more polished - but Canonical needs to stick to releases to keep companies that are using the system more reassured.

Edit: Forgot to add something:

Why would we want to have to edit things like that? X org and other projects are working on devices/code just working as expected and being bug free compared to other solutions available.

---

### Post by Gina on 2008-06-20
I agree that the decision not to include a compiler is the right one.  The average user doesn't need it and hence including it only increases bloat - something we are trying our best to get away from!  To include virtually everything the general user wants in one 700MB distro shows great programming IMO unlike .... We want to keep it that way.

---

### Post by 23meg on 2008-06-20
[QUOTE=RAOF]Not shipping a compiler + minimal dev environment saves megabytes from the CDs; this is non-trivial.[/QUOTE]

We do ship build-essential though (at least that was the case with all releases including Gutsy; I didn't check Hardy); it's just not installed by default.

---

### Post by ronacc on 2008-06-20
while the occasional omission chafes me , I understand the reason behind it and agree with the wisdom . Ubuntu is not aimed at me it is aimed at my neighbor who couldn't/wouldn't use a cmdline if his life depended on it , and the need to keep within the 700mb limit of a cd . My internet connection is lower end US cable , I can manage at best 200mb/hr d/l speed ,  a cd = 3hr+ a dvd = 20hr+ and to top it off my ISP (comcast) just loves to mess with peer to peer.

---

### Post by RAOF on 2008-06-21
> **23meg said:**
> We do ship build-essential though (at least that was the case with all releases including Gutsy; I didn't check Hardy); it's just not installed by default.

Of course we do, and if I'd remembered the last thread on ubuntu-devel-discuss, I'd've spotted that.  Uuurgh!

---


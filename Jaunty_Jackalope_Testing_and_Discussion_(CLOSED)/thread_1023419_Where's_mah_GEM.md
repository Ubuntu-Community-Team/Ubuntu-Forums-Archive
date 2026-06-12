---
title: "Where's mah GEM?"
date: 2008-12-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by klange on 2008-12-27
This has been angering me for the past few months:

Why do we continue to build Intel DRM kernel modules without GEM support? Why are Intel graphics drivers so horribly destroyed, and have been for weeks?

I've looked everywhere on Launchpad and try my best to pay attention to updates elsewhere, but I can't find the answer.

I'd love to actually test Jaunty, but it's not that easy when I can even use my laptop because even the simplest of window managers runs so slowly.

Gah!

---

### Post by vishalrao on 2008-12-27
Have you tried vesa mode like suggested in this thread? [http://ubuntuforums.org/showthread.php?t=1022206](http://ubuntuforums.org/showthread.php?t=1022206)

---

### Post by klange on 2008-12-27
> **vishalrao said:**
> Have you tried vesa mode like suggested in this thread? [http://ubuntuforums.org/showthread.php?t=1022206](http://ubuntuforums.org/showthread.php?t=1022206)

Using vesa may be fine from a technical standpoint for most people, but not me. I need hardware-accelerated OpenGL at a number of levels that vesa does not provide.

The 1024x768 maximum resolution also gives me severe headaches on my 1280x800 LCD, so that's a no-go.

It also doesn't change the fact that we should have had GEM three kernels ago.

---

### Post by DougieFresh4U on 2008-12-27
> **WindowsSucks said:**
> This has been angering me for the past few months:

Why do we continue to build Intel DRM kernel modules without GEM support? Why are Intel graphics drivers so horribly destroyed, and have been for weeks?

I've looked everywhere on Launchpad and try my best to pay attention to updates elsewhere, but I can't find the answer.

I'd love to actually test Jaunty, but it's not that easy when I can even use my laptop because even the simplest of window managers runs so slowly.

Gah!

I absolutely agree with you on the Intel 'mess'. I tried the Intel graphics on Jaunty this week, and what a mess. I was having lock ups/freeze after booting to desktop. Only hard shut down would get me out of it. I managed to use a live cd to get the vesa back so I could at least have a usable desktop.
Intel is a complete mess!!

---

### Post by Gina on 2008-12-28
Several people who complained a while back that Jaunty was to stable and no fun should be happy now!!  :lolflag:

---

### Post by luca_linux on 2008-12-28
You could give Fedora 10 a try...

---

### Post by Starks on 2008-12-28
I have GEM

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM GEM 20080716 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.3-devel

---

### Post by amano on 2008-12-28
GEM is a completely new infrastructure. And the Intel drivers added just preliminary support. Just have a look at the tests results from phoronix: There were graphical glitches and massive performance drops: [http://www.phoronix.com/scan.php?page=article&item=intel_graphics_q408&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_graphics_q408&num=1)

I do not believe that a (good) working Intel driver will appear in time for Jaunty. Thus don't set your expectations too high. Drivers will benefit from GEM, DRI2 and DRM Mode-Setting in the mid- to long term. In the short term they will just work somehow with glitches and performance drops.

---

### Post by Starks on 2008-12-28
If you want GEM and DRI2...

[https://launchpad.net/~xorg-edgers/+archive](https://launchpad.net/~xorg-edgers/+archive)

---

### Post by klange on 2008-12-28
> **amano said:**
> GEM is a completely new infrastructure. And the Intel drivers added just preliminary support. Just have a look at the tests results from phoronix: There were graphical glitches and massive performance drops: [http://www.phoronix.com/scan.php?page=article&item=intel_graphics_q408&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_graphics_q408&num=1)

I do not believe that a (good) working Intel driver will appear in time for Jaunty. Thus don't set your expectations too high. Drivers will benefit from GEM, DRI2 and DRM Mode-Setting in the mid- to long term. In the short term they will just work somehow with glitches and performance drops.

I assure you you're wrong: I've used the Xorg-edgers drivers and, unlike what is currently shipping with Jaunty, they performed quite nicely (outside of one bug I believe has been fixed since then...). The Intel drivers have been completely rewritten around DRI2/GEM (which is probably why they perform so horribly in Jaunty in their current state...).

@Starks: Yes, I've used them, I'm wondering when the same functionality will actually make it into Jaunty.

I've also used Fedora 10, and from my experience there was no DRI2 support (and performance was almost as bad as Jaunty...)

**e**: Also, yes, the OpenGl renderer string will show GEM, because the Mesa setup is GEM-ready (which is actually a bad thing in our case because the drivers aren't as non-GEM-ready as the old ones).
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM **GEM** 20080716 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.3-devel

---

### Post by shivathreya on 2009-01-10
I installed UXA/GEM by adding xorg-edgers ppa and intel graphics ppa.

I compiled kernel 2.6.28.

deb [http://ppa.launchpad.net/xorg-edgers/ubuntu](http://ppa.launchpad.net/xorg-edgers/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/xorg-edgers/ubuntu](http://ppa.launchpad.net/xorg-edgers/ubuntu) intrepid main

deb [http://ppa.launchpad.net/intel-gfx-testing/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/intel-gfx-testing/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ubuntu) intrepid main

After upgrading I added the line 'Option "AccelMethod" "UXA" to xorg.conf

There was remarkable difference in the 3d performance.

Atlease glxgears which was showing 200 fps was showing 800 fps.

I have a GM965/960.

Shiva

---

### Post by klange on 2009-01-10
Yet another example of why the mainline drivers need to be updated. There was also a recent RC release which we could follow, but that is unlikely. My laptop is virtually unusable right now due to the poor performance of the graphics drivers (and the xorg-edgers repos are not properly versioned, as I'm sure you are aware, so they take a lot of manual work to use).

---

### Post by Starks on 2009-02-02
Is there anyway to make the new driver not require changes to xorg.conf for UXA support?

---

### Post by RAOF on 2009-02-02
> **Starks said:**
> Is there anyway to make the new driver not require changes to xorg.conf for UXA support?

Yes, we could enable it by default.  But given that UXA isn't exactly trouble-free, this would probably be a bad idea :).

---

### Post by Starks on 2009-02-02
> **RAOF said:**
> Yes, we could enable it by default.  But given that UXA isn't exactly trouble-free, this would probably be a bad idea :).

I can't use Compiz with EXA anymore and the performance penalty is quite unbearable.

I might just go and complain to the ubuntu-x mailing list.

---

### Post by Boomhauer on 2009-02-02
my intel was behaving like poop until i enabled uxa and now it is nice, the best its been in jaunty.  what problems are people having with uxa?

---

### Post by RAOF on 2009-02-02
> **Starks said:**
> I can't use Compiz with EXA anymore and the performance penalty is quite unbearable.

I might just go and complain to the ubuntu-x mailing list.

Well, complaining on the mailing list is unlikely to be very helpful.

I guess you're talking about [this bug](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094), which, like many such bugs, now has a low signal-to-noise ratio.

It *might* be worth asking about UXA by default, but you'd need to be able to say 'no' to (at least) these questions: "Does it still break suspend/resume?", and "Are there any rendering artefacts?".  I don't know about the first question, but UXA made GTK menus render strangely for at least one of the X team.

---

### Post by Starks on 2009-02-02
Suspend, blank screen, and resume is already broken without UXA enabled.

<____<

---

### Post by felix.rommel on 2009-02-04
> **Boomhauer said:**
> my intel was behaving like poop until i enabled uxa and now it is nice, the best its been in jaunty.  what problems are people having with uxa?

With my Intel GMA965 I had no problems with UXA so far but it didn't speed up anything related with KDE. Scrolling in KMail or Konqueror is terrible slow :(

Maybe there is a problem with KDE atm. because scrolling in Firefox is OK. Hope that Qt 4.5 will be used till Jaunty comes out which should speed up whole KDE desktop.

---

### Post by mattduckman on 2009-02-04
> **RAOF said:**
> "Does it still break suspend/resume?"

This is the first thing i noticed when i enabled UXA. suspend/resume technically works, but on resume the xserver crashes. 

> **RAOF said:**
> "Are there any rendering artefacts?"

i notice no artifacts.

the only other issue i found is that partial transparency rendering sucks.

---

### Post by pravit on 2009-02-15
I'm trying to get UXA/GEM working but it doesn't seem to be enabled.

I installed kernel 2.6.28.5-ultimate using kernelcheck. 

I then added these repositorites:
deb [http://ppa.launchpad.net/xorg-edgers/ubuntu](http://ppa.launchpad.net/xorg-edgers/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/xorg-edgers/ubuntu](http://ppa.launchpad.net/xorg-edgers/ubuntu) intrepid main

deb [http://ppa.launchpad.net/intel-gfx-testing/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/intel-gfx-testing/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ubuntu) intrepid main

After refreshing, the update manager found new versions libdrm and all those other packages, which I updated.

I then added Option "AccelMethod" "UXA" to xorg.conf and saved it, then restarted.

But when I run glxinfo I still have:
OpenGL renderer string: Mesa DRI Intel(R) 965GM 20061102 x86/MMX/SSE2
as before.

Can anyone help me out?

Also, how can I tell what version of xf86-video-intel is being used? Do those PPA include the latest 2.6 version?

---

### Post by Starks on 2009-02-16
1. You avoid using a custom kernel. That creates all sorts of problems.

2. Do not use a self-compiled graphics driver. It is very difficult to get all the hooks right unless you know what you're doing.

3. GEM is enabled by default on the current repo kernels and graphics drivers. The edgers drivers also support it.

---

### Post by klange on 2009-02-16
To answer my original question: It's exactly where it should be: Installed and working.

---

### Post by andrewabc on 2009-02-16
> **WindowsSucks said:**
> To answer my original question: It's exactly where it should be: Installed and working.

I have intel g965 chipset. So when jaunty final is out, GEM will be installed and running by default? If so, this should increase performance of my machine? I know with compiz enabled, and I do anything simple such as web page scrolling, xorg can use 20% CPU (to be fair it used to be 50% CPU making compiz useless in hardy).

---

### Post by klange on 2009-02-16
> **andrewabc said:**
> I have intel g965 chipset. So when jaunty final is out, GEM will be installed and running by default? If so, this should increase performance of my machine? I know with compiz enabled, and I do anything simple such as web page scrolling, xorg can use 20% CPU (to be fair it used to be 50% CPU making compiz useless in hardy).
The testing that is going on right now is to determine if UXA is stable enough to have the stack enabled by default, but at the very least it will be installed - you just need to enable DRI2 and UXA in your xorg.conf.

---

### Post by Starks on 2009-02-16
> **WindowsSucks said:**
> The testing that is going on right now is to determine if UXA is stable enough to have the stack enabled by default, but at the very least it will be installed - you just need to enable DRI2 and UXA in your xorg.conf.

Option "AccelMethod" "UXA" doesn't enable DRI2?

---

### Post by klange on 2009-02-17
> **Starks said:**
> Option "AccelMethod" "UXA" doesn't enable DRI2?

It shouldn't. If it does, wow. UXA can be used with DRI (or it used to be able to be...), and last I checked they left DRI2 as a separate option.

---

### Post by Starks on 2009-02-17
As far as I understand it, the driver by default will try to enable DRI2. Because DRI2 relies on UXA, DRI2 will only be enabled when UXA is enabled.

In short, enabling UXA will enable DRI2.

Check your /var/log/Xorg.0.log if you don't believe me.

---


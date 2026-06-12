---
title: "AMD Catalyst center, driver issues"
date: 2012-11-15
forum: Installation &amp; Upgrades
---

### Post by Rob Sayer on 2012-11-15
I recently upgraded xubuntu 12.04 to 12.10 on 2 laptops.  Video on the one with Intel integrated graphics works fine.

On the one with ATI/AMD graphics Vlc works properly but smplayer does not work unless I select the x11 module, which it did not do before.  With other modules either mplayer crashes or I get audio but no video depending upon the selected o/p module.

If I go into Settings Manager and click AMD Catalyst Control Center (non-admin) I get:

> Initialization  error

There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No AMD graphics driver is installed, or the AMD driver is not functioning properly.
Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.
I got the same error message when I ran:
> gksudo amdcccleTried this thread:
> [http://ubuntuforums.org/showthread.php?t=1930450&highlight=xubuntu+AMD+Catalyst](http://ubuntuforums.org/showthread.php?t=1930450&highlight=xubuntu+AMD+Catalyst)but it doesn't seem to have 12.10 specific information.

Here's a little more information:

> $ lspci | grep VGA
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
> $ cat /etc/X11/xorg.conf

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSectionUnder Ubuntu 12.04 (which I replaced with xubuntu 12.04 by just reinstalling) on this machine I got a proprietary video driver listed but I never installed it.  Under xubuntu 12.10 this driver doesn't appear at all in the update manager section.

Perhaps I should be glad I never installed it before ... are there compatibility issues in 12.10?

I downloaded the linux 64 bit installer: AMD Catalyst™ 12.6 Proprietary Linux x86 Display Driver from the amd site but needless to say I haven't installed it yet.

---

### Post by Mark Phelps on 2012-11-15
IF the AMD chipset is really a 4200 -- then it will NOT work with Ubuntu 12.10 -- because that upgraded the X-server to 1.13, and this summer, AMD dropped support for its Linux drivers for the HD 2x/3x/4x chipsets.  The older driver (legacy 12.6) will NOT work with the X-server v1.13.

So basically, there are no restricted AMD drivers that will work with Ubuntu 12.10 and AMD HD 2x/3x/4x chipsets.

---

### Post by Rob Sayer on 2012-11-16
Thanks for the reply.  I suspected something like that when the driver didn't come up on the list..

It's not a big issue on that machine ... it's a single core and I don't use it for playing video much anyway.  I never even noticed any issues with smplayer for a while.

---

### Post by Linuxisfast on 2012-11-16
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

Add this ppa and you will have Catalyst for your older AMD cards.

---

### Post by Rob Sayer on 2012-11-17
Thanks, I'll look at that.

---

### Post by QIII on 2012-11-17
Before you look at that, and for all others who might see this:

The process given ***downgrades ***X Server to 1.12, where Ubuntu 12.10 uses 1.13.  It also uses an ***older***, patched proprietary driver rather than the most recent one.  You need to read the PPA description before launching into it.

This does not "solve" the problem.  It takes you a step back.  That may be fine and it's up to you, but you should be aware what you are doing.

Those who propose this solution to users should make this clear.

---

### Post by Rob Sayer on 2012-11-18
> **QIII said:**
> Before you look at that, and for all others who might see this:

The process given ***downgrades ***X Server to 1.12, where Ubuntu 12.10 uses 1.13.  It also uses an ***older***, patched proprietary driver rather than the most recent one.  You need to read the PPA description before launching into it.

This does not "solve" the problem.  It takes you a step back.  That may be fine and it's up to you, but you should be aware what you are doing.

Those who propose this solution to users should make this clear.

You beat me to it ... I'm not interested in this ppa.  The solution looks potentially worse than the problem.

It's not that bad of a issue anyway.  I don't use that machine for playing video anyway, so having to use the slow x11 driver in smplayer isn't a problem.  Everything else works fine.

But thanks anyway.

---


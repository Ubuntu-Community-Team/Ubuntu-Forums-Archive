---
title: "Disaster turns to good fortune (mostly)"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bobnutfield on 2008-10-02
Hello Everyone,

I had a disaster yesterday where I indadvertently damaged the partitions on my hard drive which proved to be irrecoverable.  Fortunately, I had good backups of main files.  But, I triple booted and I lost a years worth of configuration, which I will now start all over again.  Just goes to prove that even supposedly experienced users can really cock-up sometimes.

I took the opportunity to go ahead and install Intrepid Alpha 6.  So far, it's really great, far better performance than I ever got with Hardy.  I now have native support for my wireless (RTL8187B).  No morre ndiswrapper!!  The scrolling freezes seem to have been fixed (related to ACPI, I'm sure.)

The only real problem (and reasonably signficant for me) is the lack of video drivers.  It seems to be a catch 22:  I cannot run media players (VLC, Mplayer, Totem, etc.) as they all close immediately with the error:

> X Error of failed request:  BadAlloc (insufficient resources for operation)

All my investigation suggests that this is because of the lack of a graphics driver for my ATI X1250, although flash in Firefox play fine.

The catch 22 is that apparently, there is no fglrx available for Intrepid yet.  EnvyNG crashes with the complaint:

> SystemError: E:Unable to correct problems, you have held broken packages.


I have no broken packages.

Has anyone else had this problem and been able to resolve it?

Thanks for any thoughts or replies.

---

### Post by ronacc on 2008-10-02
that error probably reads "you have held BACK packages" that may mean you need to dist-upgrade ( be careful) or it may mean they just are't finished for your arch yet and will be installed at a later upgrade .

---

### Post by bobnutfield on 2008-10-02
> **ronacc said:**
> that error probably reads "you have held BACK packages" that may mean you need to dist-upgrade ( be careful) or it may mean they just are't finished for your arch yet and will be installed at a later upgrade .


Thanks, that makes sense.  It is still in Alpha, so it would not be surprising if there is third party software not ready yet.  Still just a little frustrating not to be able to view any media.

---

### Post by psyke83 on 2008-10-02
Your "BadAlloc" errors suggests that you're trying to play content while using XAA acceleration. In your xorg.conf, Section "Device", add:

Option "AccelMethod" "EXA"

---

### Post by t.alex on 2008-10-02
> **bobnutfield said:**
> 

All my investigation suggests that this is because of the lack of a graphics driver for my ATI X1250, although flash in Firefox play fine.


on the contrary! you do have drivers for your card, in fact free 3d drivers out of the box :) You'll just have to change to EXA acceleration for now. Make sure that your Device section in xorg.conf looks like this:

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
	Option		"AccelMethod"	"EXA"
	Option		"EnablePageFlip" "1"
EndSection

```

//edit: not quick enough :rolleyes:

---

### Post by bobnutfield on 2008-10-02
Thanks to both of you.  That fixed it.  If you don't mind(either poster), would you breifly explaining the difference in what you have posted and the default config in xorg?  The previous installs have automatically picked up the radeon driver, so I assumed it wasn't ready for Intrepid yet. 

t. alex, I simply copied and pasted your config and it worked immediately.

---

### Post by t.alex on 2008-10-02
the default config in xorg.conf uses XAA acceleration (actually radeon defaults to XAA). From the radeon manual page:
[QUOTE='man radeon']Option "AccelMethod" "string"
              Chooses between available cceleration architectures.  Valid options are XAA  and EXA.  XAA is the traditional acceleration architecture and support for it is very stable.  EXA is a  newer  acceleration  architecture with better performance for the Render and Composite extensions, but the rendering code for it is newer and possibly unstable.The  default  is XAA.[/QUOTE]

General EXA has been much faster, but it looks there are some problems with the latest X.Server 
->[http://www.phoronix.com/forums/showthread.php?t=12813](http://www.phoronix.com/forums/showthread.php?t=12813)

---

### Post by psyke83 on 2008-10-02
> **bobnutfield said:**
> Thanks to both of you.  That fixed it.  If you don't mind(either poster), would you breifly explaining the difference in what you have posted and the default config in xorg?  The previous installs have automatically picked up the radeon driver, so I assumed it wasn't ready for Intrepid yet. 

t. alex, I simply copied and pasted your config and it worked immediately.

EXA is a replacement for the old XAA acceleration method in Xorg, which was intended to improve performance especially with compositing managers. You can read about it from "man radeon", for example.

To be honest, I'm surprised that radeon still uses XAA by default. EXA had some performance regressions some time ago, but as far as I know, most of those regressions are gone and EXA is generally superior.

*I only have Intel integrated graphics, which uses EXA by default.

---

### Post by bobnutfield on 2008-10-02
> **psyke83 said:**
> EXA is a replacement for the old XAA acceleration method in Xorg, which was intended to improve performance especially with compositing managers. You can read about it from "man radeon", for example.

To be honest, I'm surprised that radeon still uses XAA by default. EXA had some performance regressions some time ago, but as far as I know, most of those regressions are gone and EXA is generally superior.

*I only have Intel integrated graphics, which uses EXA by default.

Thank you.   I have read this:

> [http://www.phoronix.com/scan.php?page=article&item=981&num=1](http://www.phoronix.com/scan.php?page=article&item=981&num=1)

But this is new to me.  I have only ever known fglrx as the propriatary driver for ATI cards.  In fact, as soon as I changed the driver to "radeon", Ubuntu informed me of the availablity of the ATI Driver (but will not install).  Is this a replacement for the fglrx drivers?

EDIT:  Since I have changed my xorg.conf to the suggested EXA acceleration, my CPU runs at full speed (CPUSpeed does not seem to be be working), and the temps are way up.  I didn't experience this with the fglrx driver.

---

### Post by Miguel on 2008-10-02
No. As you said, fglrx is the proprietary **ATi Driver**. The funny thing is that intrepid ships with Xorg 7.4 and Mesa 7.1 (or 7.2? I'm still on hardy). These are the first stable versions that support 3D acceleration on R500 (x1?00 series) and newer cards (probably some x2000 too). However, the latest fglrx, version 8.9 released three weeks ago, still doesn't support Xorg 7.4.

---

### Post by bobnutfield on 2008-10-02
> **Miguel said:**
> No. As you said, fglrx is the proprietary **ATi Driver**. The funny thing is that intrepid ships with Xorg 7.4 and Mesa 7.1 (or 7.2? I'm still on hardy). These are the first stable versions that support 3D acceleration on R500 (x1?00 series) and newer cards (probably some x2000 too). However, the latest fglrx, version 8.9 released three weeks ago, still doesn't support Xorg 7.4.

Thanks for clearing that up.  That is fascinating...guess it will be a while before I see more than 200fps in glxgrears.  But, it truth, I rarely have ever used compiz (usually only as a tool to show off Ubuntu), and I am not a gamer, so I guess I am good to go...In all other respects, I am getting considerably better performance from Intrepid that I ever did in Hardy.

The temps and cpu overload mentioned in my previous post seems to have corrected itself on a reboot.

---

### Post by Miguel on 2008-10-02
With a bit of luck, you will be able to enjoy more than 200fps in glxgears soon. ATi releases drivers around the 20th of every month, and it isn't too far fetched to hope they will support Xorg 7.4 and kernel 2.6.27 in the next version.

BTW: I would have thought that, with your card, you would get 1k~2k fps in glxgears, as long as fglrx is not installed in your system. I mean, my Mobility Radeon 9600 manages 2100 fps with the free driver.

---

### Post by bobnutfield on 2008-10-02
> BTW: I would have thought that, with your card, you would get 1k~2k fps in glxgears, as long as fglrx is not installed in your system. I mean, my Mobility Radeon 9600 manages 2100 fps with the free driver.

Yes, but the X1250 in this Toshiba laptop has never performed very well.  It supposedly has 256mb of vid memory, but I am sure there is shared memory for the graphics.  I get much better performance out of my desktop's six year old Nvidia Fx5500.

---


---
title: "How many users won't upgrade to 9.04 because of poor intel xorg driver performance?"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rbg on 2009-04-19
I'm in this boat.  I'm curious how many others are in it with me.  It strikes me as a major problem with this release -- that there are lots of users with intel driver performance regressions -- but perhaps my perspective is not in line with reality.

---

### Post by philinux on 2009-04-19
Working fine here on lappy with this integrated card.

Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

Compiz cube etc all ok.

---

### Post by olskar on 2009-04-19
> **philinux said:**
> Working fine here on lappy with this integrated card.

Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

Compiz cube etc all ok.

What FPS do you get from glxgears?
I have a 915 GM card and get 150 FPS in Jaunty where I in intrepid got ~1000

---

### Post by amac777 on 2009-04-19
I have the i845 video card:

VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

I have been using Jaunty since the beta. There was a brief period where X totally failed to load (fail to terminal on startup), but then they got that solved so at least 2d runs ok with this card. Desktop effects cannot be enabled, but I don't use them anyway so that is not a problem for me personally.

Edit: glxgears gives 256 frames / sec. (But glxgears is not an accurate benchmark so just for reference only.)

---

### Post by rbg on 2009-04-19
> **philinux said:**
> Working fine here on lappy with this integrated card.

Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

Compiz cube etc all ok.

I have: 

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

and was still having problems with release candidate.  I won't bother reporting glxgears FPS.  My benchmark is simply switching workspaces with compiz.  In the RC it was still choppy, especially with an application like firefox open.

Are you using UXA?

---

### Post by edm1 on 2009-04-19
What the....? I just went to check glxgears on my GM965 and realised that it's been blacklisted for compiz since yesterday. Compiz has been working fine throughout all of jaunty testing, until now.

After getting it to work i'm getting about 800 FPS.

---

### Post by philinux on 2009-04-19
> **olskar said:**
> What FPS do you get from glxgears?
I have a 915 GM card and get 150 FPS in Jaunty where I in intrepid got ~1000

700 fps with compiz on.

---

### Post by Sylslay on 2009-04-19
I have the i845 video card:

VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

I have been using Jaunty since the beta.

1988 frames in 5.0 seconds = 397.508 FPS
1780 frames in 5.0 seconds = 355.405 FPS
2117 frames in 5.0 seconds = 423.370 FPS
2204 frames in 5.0 seconds = 440.646 FPS
2191 frames in 5.0 seconds = 438.005 FPS
2193 frames in 5.0 seconds = 438.510 FPS
2211 frames in 5.0 seconds = 442.190 FPS
1982 frames in 5.0 seconds = 393.312 FPS
2727 frames in 5.0 seconds = 545.223 FPS
2892 frames in 5.0 seconds = 578.285 FPS
2307 frames in 5.0 seconds = 461.256 FPS
1827 frames in 5.0 seconds = 365.379 FPS
2651 frames in 5.0 seconds = 530.157 FPS
2357 frames in 5.0 seconds = 471.204 FPS
2257 frames in 5.0 seconds = 451.267 FPS

So , better than average 150 on 8.04
But, Skype some times works for 30min, sometimes for 4min, somtime 1min
Pulse Audio????
Settings are correct.
And sitll on linux

---

### Post by jerrylamos on 2009-04-19
Two of my test systems, IBM ThinkCentre A30 i845 graphics, IBM Thinkpad R31 i830 graphics, are dual booted between jaunty RC and Intrepid.  They are noticeably better on Intrepid especially news video.  I run Intrepid on them except for checking bugs.

The other two test systems are O.K. on jaunty, an IBM Thinkpad T40 and a Compaq Presario Celeron 3.3 gHz.  I prefer running jaunty on them.

I see some hints on the RC notes about coping with jaunty on Intel graphics.  Will try them out.  Chances that an "ordinary user" would do that?  Zero.

So for me jaunty bats 50%.

Lots and lots of bugs were fixed, thanks developers.

Jerry

---

### Post by TrueTom on 2009-04-19
**[SIZE="4"]glxgears is *NOT* a benchmark![/SIZE]**

---

### Post by paradigm2 on 2009-04-19
> **rbg said:**
> I'm in this boat.  I'm curious how many others are in it with me.  It strikes me as a major problem with this release -- that there are lots of users with intel driver performance regressions -- but perhaps my perspective is not in line with reality.

Unfortunately it is also the Radeon Xpress 200M as well:

glxgears low fps on Xpress 200M
[https://bugs.launchpad.net/bugs/347569](https://bugs.launchpad.net/bugs/347569)

I'm confident that it will eventually get fixed though.

---

### Post by paradigm2 on 2009-04-19
> **edm1 said:**
> What the....? I just went to check glxgears on my GM965 and realised that it's been blacklisted for compiz since yesterday. Compiz has been working fine throughout all of jaunty testing, until now.

After getting it to work i'm getting about 800 FPS.

They temporarily blacklisted in an update last night due to a n issue which was causing freezes on some configurations.  There are a few launchpad bugs on it.  My understanding is that this will be fixed soon.

---

### Post by hexion on 2009-04-19
I'm using the rcs for 2.6.30 from the kernel ppa with Jaunty and it brought intel performance back to normal levels.

[http://www.phoronix.com/scan.php?page=news_item&px=NzIwOA](http://www.phoronix.com/scan.php?page=news_item&px=NzIwOA)

---

### Post by edm1 on 2009-04-19
> **TrueTom said:**
> **[SIZE="4"]glxgears is *NOT* a benchmark![/SIZE]**

It'll do though.

---

### Post by paradigm2 on 2009-04-19
> **hexion said:**
> I'm using the rcs for 2.6.30 from the kernel ppa with Jaunty and it brought intel performance back to normal levels.

[http://www.phoronix.com/scan.php?page=news_item&px=NzIwOA](http://www.phoronix.com/scan.php?page=news_item&px=NzIwOA)

I just upgraded to 2.6.30rc2.  Unfortunately for me I can see no change on my Xpress 200m card.

glxgears reports the same (Well +10-20 fps difference)

[https://bugs.launchpad.net/bugs/347569](https://bugs.launchpad.net/bugs/347569)

---

### Post by unoodles on 2009-04-19
Hmm. Can ppa's fix the problem?? I upgraded to the .29 kernel and things are not really that bad. Except for bug 359392, things seem ok.
What PPA's will improve things?

Thanks.

---

### Post by hikaricore on 2009-04-19
> **TrueTom said:**
> **[SIZE="4"]glxgears is *NOT* a benchmark![/SIZE]**

Nope it's not, but this is: [http://ubuntuforums.org/showthread.php?t=1110237](http://ubuntuforums.org/showthread.php?t=1110237)
The authors original download link is dead so here: [http://www.mediafire.com/download.php?mmgwuzjzymo](http://www.mediafire.com/download.php?mmgwuzjzymo)

---

### Post by TrueTom on 2009-04-19
That's still not a good benchmark since it is missing textures for example. Though, it is better than glxgears. You can get the code with:

```
bzr branch lp:glxdragon
```

---

### Post by psyke83 on 2009-04-19
> **edm1 said:**
> It'll do though.

Damn it, it won't do! The new GEM/DRI2/UXA code is active in the Intel drivers - this new architecture has different performance characteristics, which makes glxgears even less useful than before.

In Intrepid I could get >1000fps in glxgears, but only 22-25fps in PlanetPenguin Racer.

In Jaunty I can only get ~330fps in glxgears, but PlanetPenguin now gets between 26-30fps*.

Why can't we all agree to stop propagating the myth that glxgears *is *a benchmark, or "good enough"?

*It's necessary to enable UXA and use kernel 2.6.29-1 to overcome performance problems with my 855GM chipset, though.

---

### Post by exploder on 2009-04-19
I unfortunately had to vote "Yes", should the new kernel and driver make it to the main repo or better yet into the final release I would run the 9.04 release. 

The Intel situation is not an "upstream issue", there is a known fix and should be included in the final release. This kind of regression should not be just forgotten until the next release. I should not have to add a PPA repo or anything else to have a functional system.

The quality of 9.04 is outstanding other than the issue with Intel graphics.This kind of regression should not exist in a top ten distribution. A very large number of users have systems with Intel graphics, this needs to be properly addressed for the final release.

Competing distributions that release after Ubuntu are going to have this issue resolved. Why spoil what could be one of the best releases to date with a problem that will impact a large numer of users?

Edit: I do not care about glxgears, it is not conclusive. Proper multimedia playback is my concern. A system with poor multimedia capabilities is worthless.

---

### Post by olskar on 2009-04-19
Can someone please help me? What PPA? I have installed the 2.6.29 kernel and got exactly the same terrible performance!

PlanetPenguin FPS:

Intrepid: 17,2
Jaunty 2.6.28: 4,4
Jaunty 2.6.29: 6,5

---

### Post by Kareeser on 2009-04-19
I voted no... although I have the beta on my laptop. The devs are dragging their heels on this, although they are working on it.

After upgrading to Jaunty, I can't use my VGA output properly either. Too bad, 'cause other than that, it's an excellent release.

---

### Post by novafluxx on 2009-04-19
Yeah...my laptop where my primary OS is Ubuntu has an Intel graphics chip, now I'm sorta feeling left behind.

---

### Post by psyke83 on 2009-04-19
> **exploder said:**
> Edit: I do not care about glxgears, it is not conclusive. Proper multimedia playback is my concern. A system with poor multimedia capabilities is worthless.

The intel driver doesn't seem to set up the write-combining ranges properly, see [bug #314928]("https://bugs.launchpad.net/bugs/314928"). It's trivial to fix manually if you're too impatient to wait for an update. Confirming the bug or adding extra information will only help it get fixed faster.

Enabling write-combining for my ancient 855GM chipset allows flawless 720p playback.

---

### Post by paradigm2 on 2009-04-19
> **olskar said:**
> Can someone please help me? What PPA? I have installed the 2.6.29 kernel and got exactly the same terrible performance!

PlanetPenguin FPS:

Intrepid: 17,2
Jaunty 2.6.28: 4,4
Jaunty 2.6.29: 6,5

Well the word is that 2.6.30rc2 contains many intel fixes for performance.  It did not help my card's performance (ATI radeon 200M) but it might yours:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/)

You will need to install these manually without using a PPA.  

see [https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds)

Warning: There is a risk.  These aren't official and way out of synch with the normal jaunty kernel.  But it worked fine for me.  YMMV.

The link above explains how to UNinstall it if you have problems.

---

### Post by psyke83 on 2009-04-19
> **olskar said:**
> Can someone please help me? What PPA? I have installed the 2.6.29 kernel and got exactly the same terrible performance!

PlanetPenguin FPS:

Intrepid: 17,2
Jaunty 2.6.28: 4,4
Jaunty 2.6.29: 6,5

You installed the kernel from the packages [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.1/"), correct?

Don't forget to enable UXA acceleration, otherwise DRI2 won't get activated. Also turn off compiz for testing purposes.

Note: DRI2 won't work on my chipset (855GM) unless I disable tiling, so this is my xorg.conf:

```
Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod" "uxa"
        Option          "Tiling" "false"
EndSection
```

If you experience corruption with the 2.6.29.1 kernel and UXA/DRI2, try to disable tiling as well.

**Edit:** you must also upgrade to a newer Intel driver by adding the [Xorg Edgers PPA]("https://launchpad.net/~xorg-edgers/+archive") to your sources.list.

---

### Post by olskar on 2009-04-19
> **paradigm2 said:**
> Well the word is that 2.6.30rc2 contains many intel fixes for performance.  It did not help my card's performance (ATI radeon 200M) but it might yours:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/)

You will need to install these manually without using a PPA.  

see [https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds)

Warning: There is a risk.  These aren't official and way out of synch with the normal jaunty kernel.  But it worked fine for me.  YMMV.

The link above explains how to install it if you have problems.

Thanks for your answer, but I get about the same performance as I got with 2.6.29 :(

---

### Post by psyke83 on 2009-04-19
> **paradigm2 said:**
> Well the word is that 2.6.30rc2 contains many intel fixes for performance.  It did not help my card's performance (ATI radeon 200M) but it might yours:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/)

You will need to install these manually without using a PPA.  

see [https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds)

Warning: There is a risk.  These aren't official and way out of synch with the normal jaunty kernel.  But it worked fine for me.  YMMV.

The link above explains how to install it if you have problems.

Alternatively, packages are available [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/"). Works fine for me, with exception to usplash not initializing properly. Performance is better than 2.6.28 (with UXA), but no better than 2.6.29.1 (for my old 855GM chipset).

---

### Post by mabovo on 2009-04-19
> **TrueTom said:**
> **[SIZE="4"]glxgears is *NOT* a benchmark![/SIZE]**

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_intel_greedy&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_intel_greedy&num=1)

---

### Post by jerrylamos on 2009-04-19
> **paradigm2 said:**
> Well the word is that 2.6.30rc2 contains many intel fixes for performance.  It did not help my card's performance (ATI radeon 200M) but it might yours:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/)

You will need to install these manually without using a PPA.  

see [https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds)

Warning: There is a risk.  These aren't official and way out of synch with the normal jaunty kernel.  But it worked fine for me.  YMMV.

The link above explains how to UNinstall it if you have problems.

On this IBM ThinkCentre A30 2.0 gHz Celeron with i845 integrated Intel graphics I get:

"greedy"_______________________2.6.28-11 RC____2.6.30-rc2
glxdragon_________________________2.4 fps________3.8 fps
YouTube Leona Lewis Full Screen___jerky,______not quite so      
_________________________________annoying_________jerky

glxdragon is a complex 3D figure with highlights and shadows.  I looked at Phronix benchmarks, there are so many, I haven't a clue if any relate to reality.

Jerry

---

### Post by psyke83 on 2009-04-19
> **jerrylamos said:**
> On this IBM ThinkCentre A30 2.0 gHz Celeron with i845 integrated Intel graphics I get:

"greedy"_______________________2.6.28-11 RC____2.6.30-rc2
glxdragon_________________________2.4 fps________3.8 fps
YouTube Leona Lewis Full Screen___jerky,______not quite so      
_________________________________annoying_________jerky

glxdragon is a complex 3D figure with highlights and shadows.  I looked at Phronix benchmarks, there are so many, I haven't a clue if any relate to reality.

Jerry

Jerry,

If you don't fix your MTRR ranges, video playback will suffer. Make sure that's not an issue on your system.

---

### Post by jerrylamos on 2009-04-19
> **psyke83 said:**
> Jerry,

If you don't fix your MTRR ranges, video playback will suffer. Make sure that's not an issue on your system.

What's MTRR ranges?

Thanks, Jerry

---

### Post by psyke83 on 2009-04-19
> **jerrylamos said:**
> What's MTRR ranges?

Thanks, Jerry

Take a look at the bug report linked in [this]("http://ubuntuforums.org/showpost.php?p=7102830&postcount=24") comment.

---

### Post by TBerk on 2009-04-19
Well, I have an NVidia 5200 video card, a Creative SB Audigy2 sound card, and an Airlink/RealTek wifi card- so I don't really seem to be affected by Intel driver problems. 

(Actually I *did* have trouble with the laer two at 1st but 9.04 natively recognised the RT2860 wireless chipset and the sound card I was able to update/configure to it working with everything I've thrown at it so far.

(I like AMD anyway.....) ;)


TBerk

---

### Post by psyke83 on 2009-04-19
> **TBerk said:**
> Well, I have an NVidia 5200 video card, a Creative SB Audigy2 sound card, and an Airlink/RealTek wifi card- so I don't really seem to be affected by Intel driver problems. 

(Actually I *did* have trouble with the laer two at 1st but 9.04 natively recognised the RT2860 wireless chipset and the sound card I was able to update/configure to it working with everything I've thrown at it so far.

(I like AMD anyway.....) ;)


TBerk

We're talking about issues with the Intel *graphics* driver - of course you're not going to see any issues if you're using a Nvidia card... ;).

---

### Post by VMC on 2009-04-19
> **psyke83 said:**
> The intel driver doesn't seem to set up the write-combining ranges properly, see [bug #314928]("https://bugs.launchpad.net/bugs/314928"). It's trivial to fix manually if you're too impatient to wait for an update. Confirming the bug or adding extra information will only help it get fixed faster.

Enabling write-combining for my ancient 855GM chipset allows flawless 720p playback.

I used the fix you supplied and I have the same slow frames when playing video. What does you xorg.conf file look like. I have an intregrated 865G chip.

I couldn't even play movies until I ran across another xorg.conf that someone else supplied. It works but I guess its choppy

```
Section "ServerLayout"

 Identifier "X.org Configured"

 InputDevice "Mouse0" "CorePointer"

 InputDevice "Keyboard0" "CoreKeyboard"

EndSection



Section "Files"

 ModulePath "/usr/lib/xorg/modules"

 FontPath "/usr/share/fonts/X11/misc"

 FontPath "/usr/share/fonts/X11/cyrillic"

 FontPath "/usr/share/fonts/X11/100dpi/:unscaled"

 FontPath "/usr/share/fonts/X11/75dpi/:unscaled"

 FontPath "/usr/share/fonts/X11/Type1"

 FontPath "/usr/share/fonts/X11/100dpi"

 FontPath "/usr/share/fonts/X11/75dpi"

 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

EndSection



Section "Module"

 Load "dri2"

 Load "record"

 Load "dri"

 Load "dbe"

 Load "glx"

 Load "extmod"

EndSection



Section "InputDevice"

 Identifier "Keyboard0"

 Driver "kbd"

EndSection



Section "InputDevice"

 Identifier "Mouse0"

 Driver "mouse"

 Option	"Protocol" "auto"

 Option "Device" "/dev/input/mice"

 Option "ZAxisMapping" "4 5 6 7"

EndSection



Section "Monitor"

 Identifier "Monitor0"

 VendorName "Generic LCD Display"

 ModelName "LCD Panel 1024x768"

 Option	 "DPMS" "true"

        HorizSync 31.5-48.0

        VertRefresh 56.0 - 65.0

EndSection



Section "Device"

 VendorName "Intel Corporation"

 Identifier "82865G Integrated Graphics Controller"

 Driver	 "Intel"

 BusID "PCI:0:2:0"

 Option "DRI" "False"

 Option "NoAccel" "True"

 Option "AccelMethod" "UXA"

EndSection



Section "Screen"

 Identifier "Default Screen"

        Device	 "Intel Corporation 82865G Integrated Graphics Controller"

 Monitor "Configured Monitor"

 SubSection "Display"

  Viewport 0 0

  Depth 1

  Modes	"1024x768"

 EndSubSection

 SubSection "Display"

  Viewport 0 0

  Depth 4

  Modes	"1024x768"

 EndSubSection

 SubSection "Display"

  Viewport 0 0

  Depth 8

  Modes	 "1024x768"

 EndSubSection

 SubSection "Display"

  Viewport 0 0

  Depth 15

  Modes	 "1024x768"

 EndSubSection

 SubSection "Display"

  Viewport 0 0

  Depth 16

  Modes	 "1024x768"

 EndSubSection

 SubSection "Display"

  Viewport 0 0

  Depth 24

  Modes	 "1024x768"

 EndSubSection

EndSection



Section "ServerFlags"

        Option "DontZap" "False"

EndSection

```

---

### Post by psyke83 on 2009-04-19
> **VMC said:**
> I used the fix you supplied and I have the same slow frames when playing video. What does you xorg.conf file look like. I have an intregrated 865G chip.

It's quite possible that you didn't set up the MTRR ranges properly.

Please attach the output of:

```
$ cat /proc/mtrr
```

And the output of:
```
$ lspci -vvnn
```

Edit: it's better to reply here: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by haiku88 on 2009-04-19
actually I have to use Jaunty as I couldn't get hardy or intrepid to work on my newish Sony Vaio all-in-one with Intel GMA graphics....Jaunty works with some tweaks to the xorg.conf file

---

### Post by psyke83 on 2009-04-19
Guys & gals,

Since there are several threads open that deal with different aspects of the Intel graphics cards, I've created a new thread detailing all the changes necessary to test the latest DRI2/UXA code. Please see [here]("http://ubuntuforums.org/showthread.php?t=1130582") if you're interested in some unofficial bleeding-edge testing, or just to see an overview of the various issues for Intel graphics users.

---


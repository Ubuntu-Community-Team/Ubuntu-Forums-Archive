---
title: "Bad monitor refresh rate after upgrading to 10.04?"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by h4x0rmx on 2010-05-03
I just upgraded to 10.04 and I've noticed some flickering on my monitor... if I'm correct, the problem is the refresh rate. It is set to 60 Hz and it doesn't give me any options to change it.
I would guess that the display drivers are installed correctly because  I'm running a lot of CompizConfig effects without a problem
Is there anything else that could be causing this problem?
How can I fix it?

---

### Post by h4x0rmx on 2010-05-03
This might be helpful

```
:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
:~$ sudo lshw -C video
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:32 memory:d0000000-d03fffff memory:c0000000-cfffffff(prefetchable) ioport:7110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d5400000-d54fffff
```

---

### Post by h4x0rmx on 2010-05-07
anyone?

---

### Post by smartygeek on 2010-05-09
i have this problem, too

---

### Post by JoWi on 2010-05-09
I'm having the same problem: With my HP laptop, my external (very old, but huge and good) monitor supports 1280x1024 at 100Hz (even more, but this is all I need), which I had been able to use with Ubuntu <=9.10 (by inserting a configuration section, see below). 

Now, after upgrading to 10.04 Lucid, it got stuck at 60Hz. I can select only values up to 60Hz. 

I've tried to paste my "Monitor" section from 9.04

```

Section "Monitor"
	Identifier	"NECMultiSyncFE1250plus"
	DisplaySize	402 300
	HorizSync 30.0-105.0
	VertRefresh 68.0-165.0
	Modeline "1280x1024@100Hz" 247.50  1280 1408 1712 2272  1024 1024 1028 1089
EndSection
```

into the new /etc/X11/xorg.conf and activate it (by replacing "0-CRT1" by "NECMultiSyncFE1250plus" further down in the file) but then x11 wouldn't start any more (splash screen freezes after boot).

I've also tried to insert the lines "DisplaySize" .. "Modline" into the existing "Monitor" "0-CRT1" section of xorg.conf &#8211; but this didn't solve the original problem neither.

Any suggestions?

---

### Post by rapchee on 2010-08-01
it seems they have changed the way the configuration data is stored, so old manuals won't help, and yet there is no new version :/

---

### Post by dfacto on 2010-08-10
Also having this problem.  Its very hard to search for bug reports because I am not sure how exactly to describe the "flickering."  There seems to be no pattern to it, other than when it finally does start, it seems to continue more frequently (not increasingly so, just more, if you take my meaning).  For me, it always happens on the bottom 1/6 to 1/3 of the screen--although the whole screen may blank (I just can't tell!).

Anyway I'm pretty good with xorg at this point in my life and have tried all the tricks I know of.  I'm open for any/all suggestions/advice.

Cheers!

---

### Post by ZED RINO on 2010-09-29
On my laptop with 9.04 I was using 2 monitors and this was great to do designs with inkscape. After SMART failed I installed 10.04 on a new hard drive... Bad idea ! Even if it's faster, many things are not functioning, and especially dual monitor. Fresh rates is not configurable. Nothing really on the internet except this post and nothing new.
I wish next ubuntu will be better than the 10.04...

---


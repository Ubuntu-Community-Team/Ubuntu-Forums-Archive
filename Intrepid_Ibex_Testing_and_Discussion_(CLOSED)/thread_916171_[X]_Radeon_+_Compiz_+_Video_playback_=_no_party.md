---
title: "[X] Radeon + Compiz + Video playback = no party?"
date: 2008-09-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MALEADt on 2008-09-10
How come the new Radeon driver refuses to playback video when compiz is enabled? Getting stuff like
```
X11 error: BadAlloc (insufficient resources for operation)
```
as mplayer output

Thanks

---

### Post by MALEADt on 2008-09-11
Solved. The by default selected XAA acceleration method [does not provide](http://www.phoronix.com/forums/showpost.php?p=25717&postcount=15) a mechanism to migrate pixmaps from system ram to vram.
Shouldn't EXA, the up-to-date replacement of XAA, be enabled by default?

This setting manually forces EXA:
```
Option		"AccelMethod"	"EXA"
```
More details [on the DRI wiki](http://dri.freedesktop.org/wiki/ATIRadeon#head-b7838bf182d6dfa8ab3988ed1352180e28790e2d).

---

### Post by Robertjm on 2008-09-12
I ended up leaving my compiz settings alone. Anytime I want to watch a DVD I just load Gnome in "failsafe"mode, which bypasses the extra stuff. DVDs play just fine.

Then restart Gnome when I need all those wobby windows again. :-)

Robert

---

### Post by MALEADt on 2008-09-12
> **Robertjm said:**
> I ended up leaving my compiz settings alone. Anytime I want to watch a DVD I just load Gnome in "failsafe"mode, which bypasses the extra stuff. DVDs play just fine.

Then restart Gnome when I need all those wobby windows again. :-)

Robert

That works too, but you can't tell a new user to "start gnome in failsafe mode" when he wants to view a video, can you ...

EDIT: [lauchpad entry](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/269357)

---

### Post by Robertjm on 2008-09-12
No disrespect, but I'd think its a heck of a lot easier for a new user to click Sessions in the lower lefthand corner of the GDM gui and then choose "failsafe Gnome" than trying to get a new user to edit the files to force EXA.

And by new user, I'm taking that to mean a person whose somewhat of a novice when it comes to linux and what's going on under the hood.

I'm for getting the thing fixed permanently. I was just pointing out a quick, down and dirty, workaround for people when they're ready to pop a DVD in the machine for the next couple of hours, or so.

Later,

Robert

---

### Post by MALEADt on 2008-09-15
> **Robertjm said:**
> No disrespect, but I'd think its a heck of a lot easier for a new user to click Sessions in the lower lefthand corner of the GDM gui and then choose "failsafe Gnome" than trying to get a new user to edit the files to force EXA.

And by new user, I'm taking that to mean a person whose somewhat of a novice when it comes to linux and what's going on under the hood.


That's true, I don't want a new user to have to edit the xorg.conf either, and that's why I've [filed a bug to enable EXA as default accelerator](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/269357). This has to happen sooner or later anyhow, as EXA is going to replace XAA...

---

### Post by bpl07 on 2008-09-15
My system is extremely unstable with EXA enabled, so I stick with the default XAA.  I switch to metacity whenever I want to watch video with the compiz fusion icon (fusion-icon in synaptic).

---

### Post by MALEADt on 2008-09-15
> **bpl07 said:**
> My system is extremely unstable with EXA enabled, so I stick with the default XAA.  I switch to metacity whenever I want to watch video with the compiz fusion icon (fusion-icon in synaptic).

Which driver are you running?
Using xserver-xorg-video-radeon, my system is too painfully slow, due to [a recently introduced regression](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/269388). I really hope this one gets fixed...
Anybody some suggestions how to debug X? attaching GDB to the process doesn't help I guess, as no crash occurs, and running startx under strace or valgrind results in a quite immense logfile i'm afraid.

---

### Post by danf_1979 on 2008-09-15
Confirmed. Using EXA fixes the issue. Thanks MALEADt.

---

### Post by MALEADt on 2008-09-27
To all concerned: EXA lag due to pixmapp migration has been fixed, thus EXA acceleration is working again.

---

### Post by Robertjm on 2008-09-27
I just upgraded my system with all available patches, but my xine is still shutting down. (separate issue is the GDM is ignoring my choosing Failsafe mode now!!).

---


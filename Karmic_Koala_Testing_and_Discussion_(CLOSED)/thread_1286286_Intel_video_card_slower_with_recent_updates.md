---
title: "Intel video card slower with recent updates"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andresmh on 2009-10-08
Do you also get the feeling that Compiz and other video related things are slower since like 2 or 3 days ago?

lspci:
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

### Post by Ahrim on 2009-10-08
Indeed. I am experiencing the same problem.

---

### Post by hewbert on 2009-10-08
YES! It's driving me nuts.  Sometimes it's blatantly obvious, other times it's subtle enough to just be annoying.

I've found a few bug reports that seem related to it:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/421232]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/421232")
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/416073]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/416073")
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/440986]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/440986")

Hope this gets worked out soon!


```

Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```

---

### Post by andresmh on 2009-10-08
I'm glad it's not just me

---

### Post by andrewabc on 2009-10-08
Does this have anything to do with 100% xorg CPU on login bug?

Check your system monitor to see if it is. (temporary fix is to logout and in and it will stop).

They better not screw up intel graphics for this release :(

I got intel i810 (karmic works great!).
Newer computer has Intel g965 and 100% cpu bug on beta livecd, unuseable on livecd, but not bad performance on liveusb (even though both had 100% cpu bug).

---

### Post by VMC on 2009-10-08
I noticed that mine was weirdly slow and awkward **until** I installed both kernel-12 **and** Intel-2.9.0. Now its fast again.

I have an Intel **i865** integrated video chip.

---

### Post by hewbert on 2009-10-08
> **VMC said:**
> I noticed that mine was weirdly slow and awkward **until** I installed both kernel-12 **and** Intel-2.9.0. Now its fast again.

I have an Intel **i865** integrated video chip.

Unfortunately, I'm current on updates as well, but it hasn't improved the issue at all :\

---

### Post by hewbert on 2009-10-09
If someone figures this out one way or another, please post ;)

This is really the only "big" problem I'm having with Karmic.

---

### Post by rockin_goliath on 2009-10-09
Everything is fine on my end, using kernel-12 and intel-2.9.0
Dell Mini 9 32gb SSD and 2gb RAM

Is there any application in particular that I should try to get a sense whether or not it is slower?

---

### Post by hewbert on 2009-10-09
> 
Everything is fine on my end, using kernel-12 and intel-2.9.0
Dell Mini 9 32gb SSD and 2gb RAM

Is there any application in particular that I should try to get a sense whether or not it is slower?


My performance issues are noticeable in pretty trivial usage - drawing windows, opening new ones, etc.  Even, say, opening a menu in an application can have some lag.

It's not extremely severe, but crappy enough to be pretty annoying.

I'm currently using compiz, but have tried it under a new 'test' account without any effects, and that still lacked expected performance.

I wish I could at least pinpoint it :\

---

### Post by VMC on 2009-10-09
> **hewbert said:**
> My performance issues are noticeable in pretty trivial usage - drawing windows, opening new ones, etc.  Even, say, opening a menu in an application can have some lag.

It's not extremely severe, but crappy enough to be pretty annoying.

I'm currently using compiz, but have tried it under a new 'test' account without any effects, and that still lacked expected performance.

I wish I could at least pinpoint it :\

I know this might sound silly, but you have re-booted since applying your updates?

Also does [FONT="Courier New"]top[/FONT] show any relevance. Any thing pop out that eats too much cpu%?

---

### Post by hewbert on 2009-10-09
> **VMC said:**
> I know this might sound silly, but you have re-booted since applying your updates?

Also does [FONT="Courier New"]top[/FONT] show any relevance. Any thing pop out that eats too much cpu%?

Nah, not silly at all, but yes, I've rebooted.  top doesn't show anything unusual.

I did install xserver-xorg-video-intel 2.4 for the heck of it and had much better performance.  There's side effects to that, of course, so it was simply a test :)

---

### Post by VMC on 2009-10-09
It appears that now the 9 series is affected and the 8 series is stable now. It use to be reversed. The recent kernel patches may be the culprit.

Just for grins whats the output of:
```
uname -r&&aptitude show xserver-xorg-video-intel|grep Ver

```

By the way, todays output has another point issue kernel upgrade. Now .42.

---

### Post by hewbert on 2009-10-09
> **VMC said:**
> It appears that now the 9 series is affected and the 8 series is stable now. It use to be reversed. The recent kernel patches may be the culprit.

Just for grins whats the output of:
```
uname -r&&aptitude show xserver-xorg-video-intel|grep Ver

```

By the way, todays output has another point issue kernel upgrade. Now .42.

% uname -r&&aptitude show xserver-xorg-video-intel|grep Ver
2.6.31-13-generic
Version: 2:2.9.0-1ubuntu1

I just updated, too, but it hasn't affected the performance.

---

### Post by Miguel on 2009-10-09
We got mesa 7.6 in a recent update. It's possible that is the reason some of you are seeing performance regressions. Fill bugs, and if confirmed, Bryce Harrington will most likely rever to a previous mesa version (details on the ubuntu-x mailing list).

---

### Post by cylverbak on 2009-10-09
My video display has bogged way down too as of an xserver-xorg-video-intel update done 2(?) days ago.

uname -r&&aptitude show xserver-xorg-video-intel|grep
Ver2.6.31-11-generic
Version: 2:2.9.0-1ubuntu1

This is on an EeePC 1000 which was working very nicely prior to that update. It's not nearly as much fun now. Gotta love betas :)

---

### Post by Seq on 2009-10-09
I'm running compiz on an i965 (x3100) and haven't noticed any issues. And my backlight still doesn't work (2.9 was supposed to fix this I thought).

```
$ uname -r&&aptitude show xserver-xorg-video-intel|grep Ver
2.6.31-13-generic
Version: 2:2.9.0-1ubuntu1

$ lshw -C video
WARNING: you should run this program as super-user.
  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:28 memory:d0000000-d00fffff memory:c0000000-cfffffff(prefetchable) ioport:3110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d0100000-d01fffff
```

---

### Post by Shibblet on 2009-10-09
Do you have Compiz set for indirect-rendering?

---

### Post by zoomy942 on 2009-10-10
> **Shibblet said:**
> Do you have Compiz set for indirect-rendering?

whats that?

---

### Post by cylverbak on 2009-10-11
After this mornings updates, my video is flying again! I normally update daily, first thing in the morning.
> [UPGRADE] libieee1284-3 0.2.11-5ubuntu1 -> 0.2.11-5ubuntu2
[UPGRADE] libusplash0 0.5.41 -> 0.5.42
[UPGRADE] linux-headers-2.6.31-13 2.6.31-13.43 -> 2.6.31-13.44
[UPGRADE] linux-headers-2.6.31-13-generic 2.6.31-13.43 -> 2.6.31-13.44
[UPGRADE] linux-libc-dev 2.6.31-13.43 -> 2.6.31-13.44
[UPGRADE] telepathy-idle 0.1.4-1 -> 0.1.4-1ubuntu1
[UPGRADE] usplash 0.5.41 -> 0.5.42

---

### Post by andresmh on 2009-10-11
> **cylverbak said:**
> After this mornings updates, my video is flying again! I normally update daily, first thing in the morning.


I think you might be right! I think it's back to the way it used to be, which is good.

---

### Post by cylverbak on 2009-10-13
This afternoons updates have killed the speed once again . . . sigh!

> [UPGRADE] byobu 2.38-0ubuntu1 -> 2.38-0ubuntu2
[UPGRADE] devicekit-disks 007-2 -> 007-2ubuntu1
[UPGRADE] libpython2.6 2.6.4~rc1-0ubuntu2 -> 2.6.4~rc1-1ubuntu1
[UPGRADE] libzephyr4 3.0~beta.2483-2 -> 3.0~rc.2544-1
[UPGRADE] python2.6 2.6.4~rc1-0ubuntu2 -> 2.6.4~rc1-1ubuntu1
[UPGRADE] python2.6-minimal 2.6.4~rc1-0ubuntu2 -> 2.6.4~rc1-1ubuntu1
[UPGRADE] xserver-common 2:1.6.4-2ubuntu1 -> 2:1.6.4-2ubuntu2
[UPGRADE] xserver-xorg-core 2:1.6.4-2ubuntu1 -> 2:1.6.4-2ubuntu2
[UPGRADE] xserver-xorg-video-intel 2:2.9.0-1ubuntu1 -> 2:2.9.0-1ubuntu2


---

### Post by tekstr1der on 2009-10-13
> **cylverbak said:**
> This afternoons updates have killed the speed once again . . . sigh!

Not sure how that's possible. Last update was for one very specific patch regarding KDE with KMS.

My onboard Intel graphics have been flying (relative to Jaunty & early Karmic) since the 2.9 series hit. Consistently getting 23.x seconds in GtkPerf vs over 30 sec with 2.7 drivers.

---

### Post by avb on 2009-10-13
:) im getting 8.55 sec with mist theme

---

### Post by oztrailrider on 2009-10-13
I'm getting 5.6 - 5.7 seconds for 100 rounds under gtkperf on a G31 board. This is the first time I have run it so I have no previous figures to compare to.

---

### Post by cylverbak on 2009-10-13
We may be talking apples vs oranges here, I'm not sure. I just know that doing the upgrade this afternoon, the menu response became glacial on the netbook karmic koala version. Trying to choose anything was painfully slow. Once loaded there is no speed problem with the running program. The slowdown only seemed to effect the menuing response.

I downgraded (ie. restored the older versions)
xserver-common 2:1.6.4-2ubuntu2 -> 2:1.6.4-2ubuntu1
xserver-xorg-core 2:1.6.4-2ubuntu2 -> 2:1.6.4-2ubuntu1
xserver-xorg-video-intel 2:2.9.0-1ubuntu2 -> 2:2.9.0-1ubuntu1 

Screen response on the netbook menu is now running fine again.

---

### Post by ormandj on 2009-10-13
> **VMC said:**
> I noticed that mine was weirdly slow and awkward **until** I installed both kernel-12 **and** Intel-2.9.0. Now its fast again.

I have an Intel **i865** integrated video chip.

Same issue here on X4500MHD and X4500HD. Had to do the 'partial update' in order to get things to work properly.

---


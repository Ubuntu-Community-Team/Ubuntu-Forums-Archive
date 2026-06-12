---
title: "Hey, I think I have DRI2!!?"
date: 2008-12-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zombiepig on 2008-12-07
I just installed the latest set of jaunty updates, which included kernel 2.6.28. And amazingly, I think I've now got DRI2 on my intel 965 graphics!

I may be wrong, but now I can run glxgears and have it work properly in a wobbly window, and follow cube rotation properly too :D

Here's a screenshot as proof.

---

### Post by reacocard on 2008-12-08
Awesome! I've been waiting for DRI2 for forever now. Is graphics performance in general better than 8.10 that you've noticed?

---

### Post by Jay_Bee on 2008-12-08
Finally, it's happening :)

---

### Post by Starks on 2008-12-08
You guys are most likely mistaken.

I don't think the DRI2 hooks are enabled yet.

I also can't replicate your results on a fully updated livecd or installed environment with my i945.

---

### Post by Starks on 2008-12-08
*deleted*

---

### Post by portis on 2008-12-08
Does anyone test the new xserver and intel driver in xorg-edgers repo?

The DRI2 support has been merged into the intel master and server-1.6-branch on 5 december. ([http://anholt.livejournal.com/40208.html]("http://anholt.livejournal.com/40208.html"))

The intel driver and xserver in the xorg-edgers repo are checked out on 7 december, so I think they are quite new and the DRI2 support should be included.

But after installing, the DRI2 doesnot work for my intel 965 chip.
I have these lines in the Xorg.0.log:

(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.5.99.2, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
...
(II) AIGLX: Screen 0 is not DRI2 capable

---

### Post by tormod on 2008-12-08
The screenshot looks like indirect rendering. But I am pretty sure xserver 1.6 will be needed for DRI2. And a newer -intel driver... Maybe zombiepig is using non-accelerated rendering?

Before installing anything from the xorg-edgers PPA, always check the PPA web page for latest issues/instructions. See also this thread: [http://www.phoronix.com/forums/showthread.php?t=14235](http://www.phoronix.com/forums/showthread.php?t=14235)

xserver 1.6 should arrive in Jaunty later this week, and I think DRI2 will be enabled in the build.

The -intel 2.5.1 does not have support for DRI2. As the Anholt blog says, DRI2 has been merged to intel master, which is the trunk and not the 2.5.1 branch. It is merged into the 2.6 branch though.

---

### Post by zombiepig on 2008-12-08
> **tormod said:**
> The screenshot looks like indirect rendering. But I am pretty sure xserver 1.6 will be needed for DRI2. And a newer -intel driver... Maybe zombiepig is using non-accelerated rendering?


Maybe... but running glxinfo says "direct rendering: yes", and performance is close to intrepid (maybe a little slower). How can I tell if it's non-accelerated?

This is all just on a stock jaunty installation, no ppa's enabled.

---

### Post by tormod on 2008-12-08
> **zombiepig said:**
> How can I tell if it's non-accelerated?
What does "glxinfo | grep renderer" report? Also look through Xorg.0.log to see any relevant messages, possibly from AIGLX.

---

### Post by portis on 2008-12-08
I finally got DRI2 working by recompiling the intel driver from git repo and with the untouched 1.5.99.2 xserver from xorg-edgers repo.
But glxgears fell from 1100 FPS to ~350 FPS.
And sometimes window titles are broken.

(**) Option "DRI2" "true"
(II) Loading extension DRI2
(II) intel(0): [DRI2] Setup complete
(II) intel(0): direct rendering: DRI2 Enabled
(II) GLX: Initialized DRI2 GL provider for screen 0

---

### Post by Starks on 2008-12-08
> **portis said:**
> I finally got DRI2 working by recompiling the intel driver from git repo and with the untouched 1.5.99.2 xserver from xorg-edgers repo.
But glxgears fell from 1100 FPS to ~350 FPS.
And sometimes window titles are broken.

(**) Option "DRI2" "true"
(II) Loading extension DRI2
(II) intel(0): [DRI2] Setup complete
(II) intel(0): direct rendering: DRI2 Enabled
(II) GLX: Initialized DRI2 GL provider for screen 0

Are you using the DRM packages from that repo?

---

### Post by portis on 2008-12-08
Yes, version is 2.4.1+git20081203+modesetting-gem.4c9361b8-0ubuntu0tormod1

The DRI2 is not stable. It freezed several times. Now I return back and wait for the official solution.

---

### Post by Starks on 2008-12-08
How did you compile from master with a non-2.4.2 libdrm?

(edit: i used the cflags and libs to bypass, but i'm not sure how wise of a trick that is.)

---

### Post by portis on 2008-12-08
[http://ph.ubuntuforums.com/showthread.php?t=890843]("http://ph.ubuntuforums.com/showthread.php?t=890843")

I used this guide to compile some necessary libs.

---

### Post by portis on 2008-12-08
[http://ph.ubuntuforums.com/showthread.php?t=890843]("http://ph.ubuntuforums.com/showthread.php?t=890843")

I used this guide to compile some necessary libs.

---

### Post by Starks on 2008-12-08
That guide is honestly less than helpful since that most of the code in question has already been incorporated into masters.

I just want to know how to build drm so that I can generate 2.4.2 package or have the compilation recognized as 2.4.2.

---

### Post by blazercist on 2008-12-08
Perhaps I'm missing something and this only applies to the intel driver but I can make glxgears wobble and follow the cube properly in Hardy 8.04 with the NVIDIA proprietary driver 180.02 beta.

---

### Post by Kazade on 2008-12-08
The nVidia drivers don't use any of the open source stack. They implemented this a long time ago with their drivers.

---

### Post by blazercist on 2008-12-08
> **Kazade said:**
> The nVidia drivers don't use any of the open source stack. They implemented this a long time ago with their drivers.

Thanks, thats why I was confused,  I can see that now using my MSI Wind which has Intel graphics that you are indeed correct, DRI2 would be nice but I'll wait for a stable release.  

Thanks for the good news.

---

### Post by zombiepig on 2008-12-08
> **tormod said:**
> What does "glxinfo | grep renderer" report? Also look through Xorg.0.log to see any relevant messages, possibly from AIGLX.

```

~$glxinfo | grep renderer
OpenGL renderer string: Software Rasterizer

```

So I guess it is non-accelerated rendering. Nothing in the xorg logs to indicate why this is though.

---

### Post by andrewabc on 2008-12-08
I'm a bit confused about this thread.
I read the wiki on dri2 and what it is.
I see a couple people posting pictures of compiz cube.
I have intel 965 and compiz cube has been possible for more than a year (even when it was blacklisted).

Does dri2 make compiz effects work better?
Currently with compiz enabled, xorg uses about 20-40% CPU to do basic compiz stuff, and massively slows down working on spreadsheets in openoffice, and watching flash in firefox (among other things). Hopefully it does solve those problems.

---

### Post by zombiepig on 2008-12-09
> **andrewabc said:**
> I'm a bit confused about this thread.
I read the wiki on dri2 and what it is.
I see a couple people posting pictures of compiz cube.
I have intel 965 and compiz cube has been possible for more than a year (even when it was blacklisted).

Does dri2 make compiz effects work better?
Currently with compiz enabled, xorg uses about 20-40% CPU to do basic compiz stuff, and massively slows down working on spreadsheets in openoffice, and watching flash in firefox (among other things). Hopefully it does solve those problems.

Try this - run glxgears, then start rotating your cube. Things will look messed up. DRI2 means that compiz will play nicely when 3d programs are running, among other things.

---

### Post by andrewabc on 2008-12-09
> **zombiepig said:**
> Try this - run glxgears, then start rotating your cube. Things will look messed up. DRI2 means that compiz will play nicely when 3d programs are running, among other things.

I see what you mean.
glxgears acts weird using cube. simply moving the window makes it look bad, even not using cube.

---


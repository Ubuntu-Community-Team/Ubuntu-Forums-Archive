---
title: "Alpha 2 performance???"
date: 2009-07-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mariner09 on 2009-07-22
I'm trying Alpha 2 on a Lenovo T61 and I'm using the PAE kernel.

When all my apps are running, I notice some real sluggishness with the desktop environment.  At times, the mouse and everything will freeze for a few seconds and then come back.

I have 4gb of RAM and I'm never using more than half of it.

With the Intel video, I also see some hinting of neon green reminiscent of the old OSD display for the function keys.  I have UXA enabled and maybe that's the result.  It's not constant but there on the edge of the screen or in a panel on a website.

Is anyone else seeing these things?

---

### Post by Craigy90 on 2009-07-22
Alpha 2 is kind of old... (alpha 3 comes out tomorrow). Do you still see these problems running the current daily-live cd image?

---

### Post by psyke83 on 2009-07-22
Your issue is quite possibly [this bug]("http://bugs.freedesktop.org/show_bug.cgi?id=20766").

I am uncertain if this will be fixed in the current packages (and therefore alpha 3), or a kernel update will be required, as the problem seems partially within the DRM kernel code.

---

### Post by mariner09 on 2009-07-22
This was an alpha 2 install with updates as current as today.  I was going to try a fresh alpha 3 this weekend...

---

### Post by jocko on 2009-07-23
> **mariner09 said:**
> [COLOR=Red]This was an alpha 2 install with updates as current as today.[/COLOR]  I was going to try a fresh alpha 3 this weekend...
That means you are already running alpha 3. It will be released as a cd image today, and the cd image will of course be built from the packages that are already in the repo.

---

### Post by mariner09 on 2009-07-23
I just rebuilt from the daily-build on the 22nd.  I may have had some xorg.conf settings that were relevant from before the 2.6.31-3 kernel.  They may have been contributing to my video performance issues since UXA is now the default.  We shall see....

---

### Post by mariner09 on 2009-07-23
After about an hour of using last night's daily build with all updates, the same thing set in.  Random pauses of X.  Slight neon green hinting.  I have an Intel GM965.

---


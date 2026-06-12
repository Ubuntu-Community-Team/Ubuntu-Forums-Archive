---
title: "New Kernel + i915 modeset + close lid = kernel panic?"
date: 2009-06-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by NightMKoder on 2009-06-14
I was just wondering if anyone saw the above behavior with 2.6.30-9-generic?

I don't know if modeset is part of it - haven't tested.

---

### Post by psyke83 on 2009-06-14
> **NightMKoder said:**
> I was just wondering if anyone saw the above behavior with 2.6.30-9-generic?

I don't know if modeset is part of it - haven't tested.

The intel driver has been using modesetting for over a year (IIRC), so it seems unlikely. It's more likely that the UXA/DRI2 changeover is causing problems for your chipset.

---

### Post by RAOF on 2009-06-14
> **psyke83 said:**
> The intel driver has been using modesetting for over a year (IIRC), so it seems unlikely. It's more likely that the UXA/DRI2 changeover is causing problems for your chipset.

That's not the modesetting[1] you're thinking of :).  Kernel modesetting still isn't enabled by default.

Not quite the same, but I've been having problems with resume-from-suspend while testing KMS - the X server often (nearly always) will fail to display anything but a black screen on resume, and I need to SAK it.  I'm testing now whether those go away without KMS.

[1] I'd guess you're thinking of modesetting a-la the "xserver-xorg-video-intel-modesetting" driver we carried in Universe for a while.

---

### Post by yelo3 on 2009-06-15
I also have this problem, mine is not about modesetting, nor about suspend & resume:
[https://bugs.launchpad.net/bugs/383973](https://bugs.launchpad.net/bugs/383973)

---

### Post by psyke83 on 2009-06-15
> **RAOF said:**
> That's not the modesetting[1] you're thinking of :).  Kernel modesetting still isn't enabled by default.

Not quite the same, but I've been having problems with resume-from-suspend while testing KMS - the X server often (nearly always) will fail to display anything but a black screen on resume, and I need to SAK it.  I'm testing now whether those go away without KMS.

[1] I'd guess you're thinking of modesetting a-la the "xserver-xorg-video-intel-modesetting" driver we carried in Universe for a while.

Ah, I misunderstood the original poster (because I assumed that KMS wasn't enabled in Karmic yet). Thanks for the explanation! Yes, I was thinking of modesetting that was enabled in the driver (which caused a lot of problems on my poor 855GM chipset for quite some time, but eventually got fixed with the ForceEnablePipeA hack).

---


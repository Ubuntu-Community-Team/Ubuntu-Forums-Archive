---
title: "hardware time confusion"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Roger E Critchlow Jr on 2009-10-02
I installed the beta yesterday.  

When I started the install, my hardware clock was running my local time zone, 6 hours west of UTC.  When I finished the install, my hardware clock was still running my local timezone, which is to say that the system thought it was running local time.

But the install had actually shifted the hardware clock another 6 hours west.

When I went to System>Administration>Time and Date, the first attempt to launch yielded a cannot load configuration error.  Subsequent launches loaded a configuration that had no timezone, and wouldn't let me fix the time.

I finally had to fix the time manually with 'sudo date --set="..."; sudo hwclock -s'

Anyone else seeing this?

-- rec --

---

### Post by tom56 on 2009-10-02
> **Roger E Critchlow Jr said:**
> I installed the beta yesterday.  

When I started the install, my hardware clock was running my local time zone, 6 hours west of UTC.  When I finished the install, my hardware clock was still running my local timezone, which is to say that the system thought it was running local time.

But the install had actually shifted the hardware clock another 6 hours west.

When I went to System>Administration>Time and Date, the first attempt to launch yielded a cannot load configuration error.  Subsequent launches loaded a configuration that had no timezone, and wouldn't let me fix the time.

I finally had to fix the time manually with 'sudo date --set="..."; sudo hwclock -s'

Anyone else seeing this?

-- rec --

Yeah, I'm having similar problems. Any changes I make in Sys->Admin->Time seem to be instantly forgotten.

---


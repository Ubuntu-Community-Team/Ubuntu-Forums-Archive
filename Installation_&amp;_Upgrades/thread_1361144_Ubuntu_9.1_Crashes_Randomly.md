---
title: "Ubuntu 9.1 Crashes Randomly"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by SNYP40A1 on 2009-12-21
I installed Ubuntu 9.1 this morning on my home system.  From the Live CD or from the installation, it will randomly crash.  Often during bootup, sometimes after the system has loaded -- just by moving the mouse or clicking on the Firefox launch icon.  What should I do to fix the crashing?  I am using an Intel E6700 system on an MSI motherboard with Intel 945 Chipset with integrated GMA 3100 graphics.  I tried using the recovery console - package corruption fixes, but that did not seem to help.

---

### Post by hugmenot on 2009-12-21
First of all run memcheck from the CD boot menu.

---

### Post by SNYP40A1 on 2009-12-22
> **hugmenot said:**
> First of all run memcheck from the CD boot menu.

It's not a memory problem.  I also dual boot WinXP and that never crashes.

---

### Post by hugmenot on 2009-12-22
How does it crash?

I would do memcheck anyway.

---

### Post by SNYP40A1 on 2009-12-22
Ok, I'll do a memcheck.  Everything just completely freezes.  The mouse no longer moves, keyboard does not respond.  This usually happens either during boot or within 10 seconds after loading.  Simply moving the mouse around can cause it to freeze.  The recovery console works fine though.  Let me know what I can do...

---

### Post by hugmenot on 2009-12-22
Sounds like a hardware problem to me. This random freezing business indicates that strongly.

---

### Post by friedrich_engelsbogne on 2009-12-22
"I also dual boot WinXP and that never crashes."

So stick to WinXP -what app do you want to run that needs linux?

It could be a memory problem, but given this is linux you are trying to run, it could be anything. Frankly, even just typing this my keyboard is behaving randomly. Its bobbins, and anyone who tells you otherwise is lying.

---

### Post by SNYP40A1 on 2009-12-22
If it was a hardware problem, then how come I have no issues with WinXP?  Could be a driver issue... 

The system is for my parents.  They don't need anything more than word processing and internet.  Just don't want the virus / spyware exposure that M$ provides.

---

### Post by SNYP40A1 on 2009-12-22
So is there a safemode or minimal mode besides recovery console?

---

### Post by edonuf on 2010-02-24
I was glad to find this thread, as I have Ubuntu 9.1 on my IBM T41 (dual boot with XP), but the exact same issue.  Ubuntu crashes randomly, normally just after boot (sometimes during).  No regular repeatable steps to recreate, but everything freezes with no console access etc...

Any idea on the cause since December?

---

### Post by lavinog on 2010-02-24
The problem could be caused by ureadahead.  It has its share of bugs.
It can safely be removed.
Every 30 days or after an update (which happens more frequently) ureadahead does a trace during the boot.
After the trace it seems to consume a lot of memory, and programs tend to crash.
One way to tell if a trace occured is to type **df** if you see a line that says:
```

/var/lib/ureadahead/debugfs

```
this is another bug with ureadahead.

---

### Post by ndefontenay on 2010-02-24
To solve this problem generally, we will need to access logs located in /var/logs anyway. There must be some kind of signs in there of what's going on.

---


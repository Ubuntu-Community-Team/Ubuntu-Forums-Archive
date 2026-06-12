---
title: "Lots of USB Drives in the Places menu"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by PuleX on 2008-10-10
i just installed Intrepid beta (i386) on my pc and after some cutomization it seems to be running like a charm. Well, except for one small issue: 

I have 4 entries for USb Drives in the Places menu (see attachment). This can't be correct, since there is only 1 usb drive connected to my pc which is even turned off. The only other usb devices are a mouse and a keyboard. 
```
$ lsusb
Bus 008 Device 002: ID 163f:1611  
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c043 Logitech, Inc. MX320 Laser Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 046d:c30e Logitech, Inc. UltraX Keys (X)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I haven't been able to find a launchpad bug about this issue. Am I overlooking something? or is tehre a setting I need to tweak to make these USB Drive entries disappear from the Places menu? 
Thanks in advance!

---

### Post by UbuWu on 2008-10-10
> **PuleX said:**
> 
I haven't been able to find a launchpad bug about this issue.

Well, then file one...

---

### Post by PuleX on 2008-10-10
> **UbuWu said:**
> Well, then file one...

Well, that would have been my next step... 

Excuse me for trying to find out if I had maybe missed a bug report, or an easy fix for this 'issue'. I didn't know it was now Ubuntu community policy to drown the Bug Handler Team in possibly useless bug reports.

---

### Post by UbuWu on 2008-10-10
No problem, I didn't mean you shouldn't as well ask for advice here. But even if you find an easy fix here, it is useful to file a bugreport as other people are likely to run into the same problem as well. Don't worry about missing a bug report, if that is the case, it will be marked as a duplicate of the existing bug.

---


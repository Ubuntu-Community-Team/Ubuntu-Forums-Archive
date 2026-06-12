---
title: "Kernel Panic on install attempt"
date: 2005-08-04
forum: Installation &amp; Upgrades
---

### Post by Silvanus on 2005-08-04
When I start the installation after the "boot:" prompt I get a message saying:
```
kernel panic - not syncing: Fatal exception in interrupt.
```
in short order. I've tried expert mode, acpi=off, noapic nolapic, etc.- all to no avail. I know my ISO image was okay: I checked the md5 sum. Although the computer is old and has somewhat non-standard hardware, I installed Fedora Core 3 on it so the hardware shouldn't pose a problem.

Does anyone know of a solution?

Thanks!

---

### Post by petehall on 2005-08-04
What program did you use for burning the ISO to disc? If you used Nero, try using Alex Feinman's [ISO recorder](http://isorecorder.alexfeinman.com/isorecorder.htm)  instead.

---

### Post by Silvanus on 2005-08-04
I actually used Roxio, with which I've burned from ISO before. I'll try it again with that ISO Recorder, though.

Thanks!

---

### Post by Rapaport on 2005-08-04
A similar problem happened to me when I installed ubuntu: i received the following error after finishing the initial installation and attemption to finish by opening ubuntu in GRUB.
```

Pivot_root: no such file or directory
/sbin/init: 428 : cannot open dev/consoles no such file
Kernel panic - not syncing: attempted to kill init
```

That's where I'm at. GRUB installed fine and I can still access windows XP but no Ubuntu. All help is greatly appreciated!

---

### Post by Silvanus on 2005-08-04
The CD isn't the problem; it worked fine on another computer. Is there anything I can do to get it to work on the first box?

Thanks.

---


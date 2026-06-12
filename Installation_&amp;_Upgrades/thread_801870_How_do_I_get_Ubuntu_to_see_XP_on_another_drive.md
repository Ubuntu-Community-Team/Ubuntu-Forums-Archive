---
title: "How do I get Ubuntu to see XP on another drive?"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by gmilne on 2008-05-21
I have Ubuntu boot manager on E:\ and XP is on F:\

XP boots fine. Ubuntu hangs on initranfs

Is there a next step?
Thanks. 
Reinstall Ubuntu? Do something in the BIOS?

---

### Post by yogo on 2008-05-21
> **gmilne said:**
> I have Ubuntu boot manager on E:\ and XP is on F:\

XP boots fine. Ubuntu hangs on initranfs

Is there a next step?
Thanks. 
Reinstall Ubuntu? Do something in the BIOS?
Sorry but your title does not seem to jive with your other questions.

Bios will not have anything to do with Ubuntu not loading, however once it does load, go to places, computer, the the drive where XP is at to mount XP from Ubuntu as in your title ?.

---

### Post by housam on 2008-05-21
Boot from ubuntu live CD and type in the terminal 
```
sudo fdisk -l
``` 
where -l is a small L and post the results

---


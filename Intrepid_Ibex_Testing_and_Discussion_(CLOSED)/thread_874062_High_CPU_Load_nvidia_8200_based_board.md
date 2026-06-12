---
title: "High CPU Load nvidia 8200 based board"
date: 2008-07-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Lem on 2008-07-29
Just built up a new box with the new 8200 nvidia chipset. Getting one core nearly maxing out continuously - swapping from one to the other. Screen refresh is slow and the system isn't very responsive. Turning compiz on/off doesn't seem to be changing much. Using the 177 nvidia driver.

Any ideas what's causing this?

---

### Post by psyke83 on 2008-07-29
> **Lem said:**
> Just built up a new box with the new 8200 nvidia chipset. Getting one core nearly maxing out continuously - swapping from one to the other. Screen refresh is slow and the system isn't very responsive. Turning compiz on/off doesn't seem to be changing much. Using the 177 nvidia driver.

Any ideas what's causing this?

Is this even an Intrepid issue? How do you know what is the normal behaviour for this hardware if you just built it? Do you really need to use the 177 (beta) driver for an 8200 card? I don't think so...

Anyway, look at the NVIDIA [documentation]("http://us.download.nvidia.com/XFree86/Linux-x86/177.13/README/appendix-b.html") for "OnDemandVBlankInterrupts", and do some research on the NvNews forums and you'll find threads like [this]("http://www.nvnews.net/vbulletin/showthread.php?t=115916").

---

### Post by Lem on 2008-07-30
The 8200 is a new nvidia integrated chipset rather than a discrete graphics card. It requires the 173 or 177 drivers. I've had better results with the 173 set but something still isn't right. Disabling the nvidia driver seems to make the problem go away, but then i'm back to 800x600.

Might try a hardy install with a manual install of the current nvidia drivers and compare.

---

### Post by Lem on 2008-07-30
Hardy + 177 drivers works fine. CPU load much less and more balanced. Must be something in the new kernel that's causing problems.

---

### Post by ronacc on 2008-07-30
just for info on my amd64 system with an nvidia 7600gs and the 177 driver with gnome desktop + compiz
with just some screenlets active I am showing about 5% on both cores fluctuating 1>2% on each . intrepid a3 uptodate

---


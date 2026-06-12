---
title: "Black screen on install"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by erans on 2008-07-17
Trying to install Ubuntu on an old Pentium 3. I'm loading from the live CD, and after the loading bar fills up, the screen goes black. I tried finding an answer to this online and couldn't. Any ideas?

---

### Post by lukjad on 2008-07-17
I'm running a Celeron 633. That's around a PIII. My problem was that I was putting the CD into the wrong disk drives. If you have 2 CD drive, try switching the CD from one to the other. If that doesn't work, you may have them set up incorrectly or you may have a damaged disk.

---

### Post by wpshooter on 2008-07-17
> **erans said:**
> Trying to install Ubuntu on an old Pentium 3. I'm loading from the live CD, and after the loading bar fills up, the screen goes black. I tried finding an answer to this online and couldn't. Any ideas?

How much memory does this machine have ?

What version of Ubuntu are you attempting to install ?

---

### Post by erans on 2008-07-17
The machine has 128 MB of RAM and I'm attempting the latest version of Ubuntu (but I plan to switch to XFCE desktop as soon as it's installed). 

I booted in safemode with nosplash and some other modifiers (can't remember atm) and I got to what looked like a terminal line ("ubuntu@ubuntu$"). I had absolutely no idea what to do at that point.

---

### Post by lukjad on 2008-07-17
Try something like 
```
startx
```
That might work.

---

### Post by avtolle on 2008-07-17
At 128 mb RAM, I'm guessing that you might want to take a look at Xubuntu. See also this link: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) for some other ideas (yes, it's a bit dated, but has good information).

---

### Post by lukjad on 2008-07-17
True. I guess that might be a good thing to try.

---


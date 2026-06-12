---
title: "Crash on enter at first login"
date: 2010-02-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by alex88 on 2010-02-09
Hi, i've installed the daily build of yesterday, i've installed all updates and installed nvidia-185 drivers via synaptic.
I've restarted and i've noticed some black dots on the top of the screen, during writing the dots becomes lines growing size when i write, i've included 2 screenshots, one when the system is just booted and one with the lines after some keystrokes.
The problem is that if i press "enter" the gdm hangs up, but the lines still grow when i press keys. I can't do anything, also the power button doesn't do nothing.

But if i login, i can use the system without pressing "enter" normally. I have to logout->login again to make the dots disappear and then i can finally use the "enter" key... Any help?

I'm running on Asus G2s laptop

---

### Post by phenest on 2010-02-09
Not another thread on this. Try searching the forum first. This has been reported, like a gazillion times.

Boot into recovery mode, and...
```
sudo apt-get remove plymouth
```

---


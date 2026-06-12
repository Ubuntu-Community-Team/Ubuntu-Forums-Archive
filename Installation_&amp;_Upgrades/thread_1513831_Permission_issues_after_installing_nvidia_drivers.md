---
title: "Permission issues after installing nvidia drivers"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by captainpotato on 2010-06-20
I've just done a clean install of 10.04 and am getting it up to full working condition, but have hit a couple of odd issues:

1. The machine does not shut down or restart unless I do so using the shell (shutdown -h 0, for instance). If I try to shut down using the GUI, it just logs me out, taking me back to the login screen. From that screen the same thing happens.

2. after installing the latest nvidia drivers (through the 'hardware drivers' option), automatic mounting of the 2nd hard drive in my machine, plus USB drives/SD cards no longer happens. The error I am getting is "not authorized", so hardly helpful either.

3. I have also just noticed that I don't have any sound either now.

I am sure that it is due to the nvidia driver installation because it has happened twice (I reinstalled the OS after the first time, hoping to avoid it by doing so). I do need to use the proprietary driver because the default one does not support the two monitors running off of my graphics card correctly.

Any ideas where I could start to fix this problem?

---

### Post by captainpotato on 2010-06-20
Okay, an update: if I change the nvidia driver to version 173, the problems go away.

Good enough for me for now... now to solve the other problems that I've since detected.

---


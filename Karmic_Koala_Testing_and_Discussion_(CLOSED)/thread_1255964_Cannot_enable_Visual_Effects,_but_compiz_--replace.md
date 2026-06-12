---
title: "Cannot enable Visual Effects, but compiz --replace is working"
date: 2009-09-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tawmas on 2009-09-02
Hello,

a few days ago a partial update removed the xorg driver for my nvidia card, so I had to reinstall nvidia-glx-185 by hand. Since then, Desktop Effects do not start automatically at login, and I cannot enable them from System > Preferences > Appearence (after some flickering during which compiz starts and is then replaced again by metacity, I get a popup saying "Could not enable Desktop Effects).

I opened a terminal and typed compiz --replace to see what was the problem, only to find that compiz would work flawlessly. In fact, I can launch compiz --replace& and enjoy Desktop Effects until I log out...

How do I go about this problem? Is there some log file that I can use to see what's going on with Desktop Effects?

---

### Post by stumbleUpon on 2009-09-02
You might have enabled metacity compositing by default. When you do compiz --replace, this removes metacity compositing and so might be working.

Try the following

Alt + F2 > gconf-editor > apps > metacity > general > uncheck compositing manager.

Does this help??

---

### Post by gradinaruvasile on 2009-09-02
I had that problem many times... just install fusion-icon and u are set.

---

### Post by tawmas on 2009-09-02
Yes, I had briefly enabled metacity compositing while addressing the missing driver issue, but I disabled it before enabling Desktop Effects as I already got burned with that. :-)

I just triple-checked, and it's off, yet Desktop Effects will not start.

---

### Post by steeleyuk on 2009-09-02
This happened for me as well, but wasn't sure if it was just my problem.

Installed Ubuntu, then the Nvidia driver. Once you restart X and the driver becomes enabled, Compiz is also enabled and working. Turn Compiz off, then try turning it back on again (via the Appearances dialog) and it will say that the Desktop Effects couldn't be enabled.

Like you, compiz --replace works fine as does Metacity compositing.

---

### Post by tawmas on 2009-09-02
I wonder if this affords for a bug report... although right now it would appear to be quite a useless one wrt to available information.

---

### Post by TrueTom on 2009-09-02
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/420308]("https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/420308")

---

### Post by tawmas on 2009-09-02
Thanks for the LP reference! I subscribed to the bug.

---

### Post by Loevborg on 2009-09-02
I have the same issue; thanks for bringing the LP bug to our attention. Good to know it's being worked on.

---


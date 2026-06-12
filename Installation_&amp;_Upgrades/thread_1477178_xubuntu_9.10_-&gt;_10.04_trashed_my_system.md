---
title: "xubuntu 9.10 -&gt; 10.04 trashed my system"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by fatdragon on 2010-05-08
The upgrade process went smoothly but the system fails to boot up after.  When it starts, it gives 'failed to connect to socket' error, followed by a low-res xubuntu splash screen, then blank screen.  The system become unresponsive after that.

I thought X may be running so I tried ctrl-alt-backspace but nothing happened.  I tried ctrl-alt-F1/2/3/etc and nothing happened.  I'm officially stuck.

What do I do now?

---

### Post by Catharsis on 2010-05-08
You can try booting into Recovery Mode. Hold down Shift while you boot, and then select the kernel that has "(recovery mode)" after it (usually the second one).

Also, what graphics card do you have?
```
lspci | grep VGA
```
(You can get to a terminal by selecting "root shell" in recovery mode.)

If you have any other kernels in GRUB, try those and see if they work.

---


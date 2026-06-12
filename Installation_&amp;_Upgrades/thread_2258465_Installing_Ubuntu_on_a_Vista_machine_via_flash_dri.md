---
title: "Installing Ubuntu on a Vista machine via flash drive, freezing on partition screen"
date: 2014-12-27
forum: Installation &amp; Upgrades
---

### Post by ryandschulte on 2014-12-27
Procedure generating error:

I boot up the computer, press Esc for boot menu, select my flash drive, and start installing Ubuntu the same way as I've done on my XP computer. But once I get to the screen where it asks me to allocate disk space for an Ubuntu partition, it freezes, the mouse and keyboard become unresponsive, the hard drive access light stops blinking, and every computer connected to my ethernet switch gets internet access cut off. My wifi still works, and when I unplug the malfunctioning Vista's ethernet cable from the switch, all the other computers regain internet access. 

Possible cause:

When I try to boot Vista, after the blue loading screen at the very beginning of the boot process, it goes to a black command-prompt style screen that says: 

Disk Read Error
Press Ctrl-Alt-Del to restart

which is why I was trying to install Ubuntu in the first place.

Question:

Why is this error occurring, has anyone else experienced this, and how can I fix it?

---

### Post by geoffmcc on 2014-12-28
If it is failing while trying to partion disk and it also gives a disk error while trying to boot Vista, I'm inclined to think your drive is failing. 

Check out ultimate boot disk. May be able to fix drive or give some more info

Edit: you may also get it done by booting from Ubuntu  live disk and running GParted to see how partitions look and fix as needed.

---

### Post by Mark Phelps on 2014-12-28
> Disk Read Error

Not a good sign -- and together with the other symptoms, I would agree with the assessment that you have a failing, or already failed, hard drive.

---


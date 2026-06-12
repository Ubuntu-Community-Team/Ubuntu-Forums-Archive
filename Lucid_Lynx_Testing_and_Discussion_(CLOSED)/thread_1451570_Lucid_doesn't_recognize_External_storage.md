---
title: "Lucid doesn't recognize External storage"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bluestar14 on 2010-04-10
on the live cd, it shows my windows partition, and my other HD(internal).....it also responds when i plug in my usb drive, but when i installed it, it wouldn't recognize my windows partition, my other HD(internal), and even my usb drive

---

### Post by BrokeMahPC on 2010-04-10
We will need the answers to a few questions to help you.
-Did you have Ubuntu installed before?
-What method did you use for installing it?
-1 Install windows and Ubuntu side by side.
-2. Use entire disk. (I hope not!)
-3. Specify partitions manually.
-What hardware do you have.

This could be a grub problem - open a terminal from Applications - accessories and type:
sudo update-grub
enter you password when it asks and reboot - take note of what the grub bootscreen says and report back.
Also - try the live CD again and check your windows partition etc are still there.

One thing to be aware of is that Lucid is still in the Beta testing stage - it has not been released as a final working version and has one or two problems that need solving.
Where and when did you get your live CD and what type is it. Desktop i386, 64bit, an alpha or a beta release?

---

### Post by linuxman94 on 2010-04-10
This should have been posted in the Lucid Lynx dev forum.  

Ill have a mod move it for you.

---

### Post by bluestar14 on 2010-04-10
for some reason, i restarted a couple of times, installing a few stuff required me too, then all of a sudden, it works!

---


---
title: "Gutsy update: swap space not initialized"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by ccprog on 2007-10-20
Since I installed the upgrade from feisty to gutsy tonight, the system somehow forgot about the allocated swap partition, resulting in really, really bad screen behavior - it practically froze.

A manual swapon solves the problem and fstab has a correct entry, so my impression is, the command got somehow lost from the startup scripts. Where is it supposed to be? /etc/rc seems not to exist for this distro.

---

### Post by ccprog on 2007-10-20
OK, I just found it myself. I had a false UUID for the swap partition in fstab.

I f you are wondering how to solve this, [here]("http://ubuntuforums.org/showthread.php?t=580572") is how it is done.

Anyway, I learned something else from this:

1. If you resize or move a swap partition, what really happens is that a new one is formatted. Thus the UUID changes.

2. Using the GParted Live CD, or any other tool started outside the installation, it does not update fstab. If you think about it, it is obvious - another system runing has no knoledge which one would be your usual boot partition.

---


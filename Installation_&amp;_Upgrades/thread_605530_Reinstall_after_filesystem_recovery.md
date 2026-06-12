---
title: "Reinstall after filesystem recovery"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by kresho on 2007-11-07
I've had some filesystem corruption, which I fixed with xfs_repair. After reinstalling some obviously damaged packages, I am able to use the system again.

I'm fairly sure more binaries are damaged, but I don't know which. Do you have any ideas how to reinstall all packages, but in a way that only binaries are recovered, and configurations are left as they are now? I've invested considerable time during the past few years and I don't feel like reinstalling the system from scratch and going through all that configuration again.

---

### Post by bulldog on 2007-11-07
I should use synaptic and see if there are broken packages on your system.

---

### Post by kresho on 2007-11-07
A "broken package" in apt (synaptic) means a package with unmet dependencies. What I need is a way to reinstall only binaries in packages that were prevoiusly correctly installed.

---

### Post by Lumenary on 2008-05-03
Hello,


I worte a tutorial on how to do this while avoiding package dependency loops:


[INDENT][[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=735693&highlight=advanced+reinstall+packages+reinstalling+ubuntu[/COLOR]]("http://ubuntuforums.org/showthread.php?t=735693&highlight=advanced+reinstall+packages+reinstalling+ubuntu")[/INDENT]


Caveat emptor; be sure you want to do this, as it could reset the configuration of certain packages.


> **kresho said:**
> I've had some filesystem corruption, which I fixed with xfs_repair. After reinstalling some obviously damaged packages, I am able to use the system again.

I'm fairly sure more binaries are damaged, but I don't know which. Do you have any ideas how to reinstall all packages, but in a way that only binaries are recovered, and configurations are left as they are now? I've invested considerable time during the past few years and I don't feel like reinstalling the system from scratch and going through all that configuration again.

---


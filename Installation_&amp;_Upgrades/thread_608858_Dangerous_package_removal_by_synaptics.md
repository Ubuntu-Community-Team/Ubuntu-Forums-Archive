---
title: "Dangerous package removal by synaptics"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by sistoviejo on 2007-11-10
When trying to install the package linux32 (for running 32 bit apps in my x86-64 bit installation), synaptics wants to do the following changes for dependencies:

util-linux (essential) will be removed
ubuntu-minimal will be removed
util-linux-locales will be removed
linux32 (version 1-3build1) will be installed

Is it ok to remove all those 3 packages??? 
It doesn't sound quite right to me.
I'm a little scared because I screwed up my installation by removing the gnome-desktop package in feisty.
Right now I'm using gutsy in an HP tx1215nr laptop. The processor is an AMD turion 64 dual core.I'll appreciate any advice. thanks! :)

---

### Post by sistoviejo on 2007-11-10
BTW.. What I'm trying to do is install the package linux32 which is a wrapper to run 32 bit apps in x86-64 making the app think it is running on a x686 architecture.

I'm trying to do this in order to use 32 bit apps. 
I am especially interested in running Oracle express edition 10 because I need it for college.

thx!

EDIT:

I tried a forced install (using "dpkg -i --force-architecture") but oracle thinks I don't have enaugh swap space...
```

This system does not meet the minimum requirements for swap space.  Based on 
the amount of physical memory available on the system, Oracle Database 10g 
Express Edition requires 1024 MB of swap space. This system has 782 MB 
of swap space.  Configure more swap space on the system and retry the installation.

```
what should I try?
here's my free ram:
```

root@silvio-laptop:/media/storage/progs/linux/oracle# free
             total       used       free     shared    buffers     cached
Mem:        899188     855884      43304          0      54884     183104
-/+ buffers/cache:     617896     281292
Swap:      1020116     218464     801652

```
...maybe I should start a new thread about this?

---


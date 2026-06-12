---
title: "VMWARE install on 6.06.  Need to config .h files"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by jamrlm on 2007-11-16
This should be a simple question for someone.

I am starting with a brand new computer, a Gateway AMD 64 dual processor machine.  I formatted over the installed XP system and first installed 7.10 which worked and then installed wmware 6.0 desktop which also installed.  However when I got to the power on step for my first vitural machine it would not power on and gave an error message which shed no light on the real problem.  The response from vmware was that 7.10 was not supported.

So I tried 7.04 which found a problem with the BIOS on the machine that had to do with a timer not being connected.  7.04 quit in a keneral panic immediatly.

Becomming tird of down loading and trying to install different versions of UBUNTU, I dug out the origional install disc I used on my laptop several years ago.  I turned out to be 6.06, and it installed just great.  The upates made it 2.6.15-29-amd-64 generic.

Next I tried vmware again.  This time it stopped in the config process and asked for the path to the include files.  It assumed that it should be located at /usr/src/linux/include.  After some muddling I found a package "linux-headers-2.6.15-29-amd-64-generic' and using the Synaptic installer loaded it at  /usr/src/linux/include/linux-headers-2.6.15-29-amd-64-generic. 
This got me further in the config process but not beyond this step.  It told me that the library was not configured. 

Now to the question!
 
I do not know how or what to do to configure and what configuring would do.  I have been unable to muddle through this lack of knowledge.

I worked for 12 years as an application programmer (not system) under HPUX and never ran across this.  The paths to the individual .h files were always inserted at the beginning of the module if I remember correctly.

---


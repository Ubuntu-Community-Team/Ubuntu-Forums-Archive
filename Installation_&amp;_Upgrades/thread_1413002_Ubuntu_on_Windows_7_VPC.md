---
title: "Ubuntu on Windows 7 VPC"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by Tutunkommon on 2010-02-21
All,

I found a similar question on the forums, but the answer was not directly related to my problem, so I will try again...

I have a laptop running Windows 7 Professional.  I installed the virtual PC and XPMode in order to have the multiple virtual machines I need to do my work.  I would like to install ubuntu in another image, as I have some things that would be better done in Linux than on windows.  I cannot make ubuntu my base installation.  It HAS to be in a virtual machine.

The problem is that after the install completes, I try to start the virtual machine, and it crashes and powers down.  It doesn't get past the ubuntu logo in the middle of the screen.

I am far from a linux expert.  I have a machine that runs my company website from an ubuntu install, and it works very well.  I just need a bit of direction in getting the virtual machine working.

Any thoughts?

Thanks!

---

### Post by pirateghost on 2010-02-21
basically VPC is gimped into only truly supporting MS.  try VirtualBox instead.  if you have a key for xp, just install an xp vm (for the mentioned requirement of running xp in vm) in VirtualBox and call it quits.  i gave up on getting any linux distros to work in VPC a long time ago.

---

### Post by Mark Phelps on 2010-02-22
> **Tutunkommon said:**
>  ...I just need a bit of direction in getting the virtual machine working.
A quick check of the VPC FAQ would have shown you that only MS operating systems are supported as guests -- which is not surprising as this is an MS product.

To install other guest OSs, you would need to use a non-MS product -- as already mentioned.

---


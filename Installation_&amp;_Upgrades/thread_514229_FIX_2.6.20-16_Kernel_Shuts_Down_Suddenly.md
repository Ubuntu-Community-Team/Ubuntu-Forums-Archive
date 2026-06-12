---
title: "FIX: 2.6.20-16 Kernel Shuts Down Suddenly"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by dbreese on 2007-07-31
I've recently encountered a weird issue and thought I would share just in case someone else has the same problem.

Laptops: Two Compaq NW 8240, one Compaq NC 8230
Ubuntu: 7.04
Recently installed 2.6.20-16 kernel

Symptoms: When heavy cpu load occurs, laptop would suddenly shut down and power off without warning.  I could peg the cpu with a simple perl loop and within minutes, laptop would shut down.  What was throwing me off is that when I tried to power on, the laptop would shut down before passing the BIOS boot screen (not even make it to GRUB loader).  Even just sitting at the BIOS menu would shutdown the laptop.  Therefore, I figured it was definitely a laptop hardware issue.

I swapped my hard drive with 2 other compaqs in the office and THOSE would then crash with same symptoms.

I booted off two live cds (Ubuntu and Knoppix) and ran the "peg cpu" script and NO laptop would crash.

So, I concluded that the hard drive was somehow causing all this.  

Got a brand new identical hard drive and copied my partitions over using partimage -- SAME THING STILL OCCURRED.

SOLUTION:
Reverted back to 2.6.20-15 AND ALL ISSUES DISAPPEARED.  I can't cause the crashing no matter what load I now throw at the CPU.

MY CONFUSION:
What is still confusing me is how the BIOS still acts up.  It must be that the 2.6.20-16 kernel is heating the cpu without throttling enough, so when the BIOS starts to boot back up, it hits a temp threshold and shuts back down?

Hope it helps someone.  Not sure if this is a bug in 2.6.20-16 or where I should post it?

-Dustin

---


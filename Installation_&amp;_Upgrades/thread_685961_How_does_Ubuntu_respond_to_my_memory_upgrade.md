---
title: "How does Ubuntu respond to my memory upgrade?"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by raydar on 2008-02-02
I just upgraded an AthlonXP 2200+ machine running Ubuntu from 512MB to 1GB of RAM.  I definitely noticed an improvement, and my swap file went from upwards of 200MB to usually downwards of 40MB.  What I'm curious about is whether there's any configuration I ought to do in Ubuntu as a result of having put in more RAM.  

For instance, I remember reading somewhere that when manually setting up a Linux drive, one should make the swap partition be such-and-such a percentage of the total system RAM.  I'm thinking it's likely that when I installed Ubuntu, it set up my system based on 512MB of RAM, so do I suddenly have too small a swap partition now that I doubled my RAM?  (Seems strange that I should need a bigger swap partition as a result of having more RAM and thus less need for a swap file.)

I imagine there could be other swap settings, having to do with the file as opposed to the partition, or some completely different settings, that I'm not thinking of 'cause I'm relatively new to Linux.  Any advice would be much appreciated! :)

---

### Post by Pumalite on 2008-02-02
With 1 GB of RAM, you are fine. Don't worry. The rule is /swap to be 2x RAM, up to 1 GB.. Most people do fine with 1 GB of /swap. Ubuntu will fill as much memory as you give it.. Memory is to be used.

---


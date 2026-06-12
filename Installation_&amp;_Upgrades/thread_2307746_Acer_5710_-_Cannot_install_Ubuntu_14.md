---
title: "Acer 5710 - Cannot install Ubuntu 14"
date: 2015-12-28
forum: Installation &amp; Upgrades
---

### Post by jbb0906 on 2015-12-28
I have an Acer 5710 with an intel t2450 processor that has been running Ubuntu 9 for ages. I´ve tried several times to upgrade it, with no success. I can boot to the 14.04 Live USB, but when I try to install, I get a screen full of errors and it never starts.
I have a 120 gb drive, that I have tried repartitioning from 1 through 4 partitions, and the disk has been wiped clean, but I am still unable to get anything above V 9.01 to install and run.
Please Help

---

### Post by sudodus on 2015-12-28
Welcome to the Ubuntu Forums :-)

Please start an own thread (instead of 'hi-jacking' another thread). This time I helped you by moving your post to an own thread, and I tried to make a good title by adding the computer brand name and model.

We need more data about your computer in order to help. Otherwise we can only guess, for example that you have problems with the graphics. So please specify your computer

- (we know already brand name and model)
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

And tell us what happens when you 'Try Ubuntu' booted from a DVD disk or USB pendrive.

-o-

I looked at the following link to get a crude knowledge about the specifications

[acer-aspire-5710...](http://www.cnet.com/products/acer-aspire-5710-15-4-core-2-duo-t5500-vista-home-premium-1-gb-ram-80-gb-hdd/specs/)

but your specifications might differ.

A computer with a core2duo processor and Intel graphics should work with the current Ubuntu family operating systems. If you have only 1 GB RAM, it is not enough for standard Ubuntu and Kubuntu, but Lubuntu, Xubuntu and Ubuntu MATE should work well. These flavours have lighter desktop environments, but the same engine under the hood as standard Ubuntu. The version ***14.04.1 LTS*** has long time support and should be the first version to try.

There might also be problems with the wifi chip. The free drivers might not work, but if you tell us about your wifi hardware, we might be able to suggest a solution.

If there are still problems, you might try a 'community re-spin' based on Ubuntu 12.04 LTS, for example ***Bento, Bodhi, LXLE, ToriOS***. This older version might have better drivers for your old hardware.

---


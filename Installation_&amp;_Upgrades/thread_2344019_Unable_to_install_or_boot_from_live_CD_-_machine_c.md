---
title: "Unable to install or boot from live CD - machine check exception"
date: 2016-11-21
forum: Installation &amp; Upgrades
---

### Post by Caveat_Emptor on 2016-11-21
I have an old machine that had been running various Ubuntu and Lubuntu generations for a long time. I messed up the LVM partitions a few months ago, and am trying a fresh install.

I can boot into an installation disk with Lubuntu 16.04 (or 14.04), but when I attempt to boot into the Live distro or install, I get a machine check exception:

cpu 0 machine check exception 4 bank 1: etc.

Searching through the forums, folks suggest running a Memtest, which I am doing right now. All the memory is detected.
I will try taking out a memory module at a time.

Is this a hardware error, or should I be trying different boot parameters - unsure how to do that with a CD installation? Given I don't have a valid install on disk any more.

(ASUS A8R-MVP Motherboard, AMD Athlon 144 single core processor, 3 GB of DDR-330 RAM)

---

### Post by mörgæs on 2016-11-22
Yes, it's likely to be a hardware error.

Could the problem be overheating? Have you checked heat sink and fan(s) for dust bunnies?

---


---
title: "Kernel panic message (which disappeared) after upgrading Lubuntu 22.04.2, and broken"
date: 2023-04-30
forum: Installation &amp; Upgrades
---

### Post by mag-linares on 2023-04-30
On a computer that had only Windows 10 I installed, in dualboot, Lubuntu 22.04.2 LTS x86_64.

3 kernels were installed:

(dpkg --list | grep linux-image)

· linux-image-5.15.0-43-generic

· linux-image-5.15.0-71-generic

· linux-image-generic

At first everything was fine, during my first day with Lubuntu, installing the applications that I will need. 

Until, the next day, I received notice of a system update, and I accepted it.

The update seemed to be successful but, after rebooting the boot stuck giving me a kernel panic.

I rebooted again, and I never get that "kernel panic" message again, but it just always gets stuck at this screen:

[https://gyazo.com/04efb25db08b98c509d1a2dbd177b2c1](https://gyazo.com/04efb25db08b98c509d1a2dbd177b2c1)

I didn't know what to do, until I tried to boot by selecting the linux-image-5.15.0-43-generic kernel, and then the system booted right.

Since then, I have been working with the linux-image-5.15.0-43-generic for a few days, but I would like to know if I have any way to repair the linux-image-5.15.0-71-generic, since having it there "broken " is of no use to me, and I guess I'd better have two kernels just in case, plus use the most recent one.

How could I repair it?

---


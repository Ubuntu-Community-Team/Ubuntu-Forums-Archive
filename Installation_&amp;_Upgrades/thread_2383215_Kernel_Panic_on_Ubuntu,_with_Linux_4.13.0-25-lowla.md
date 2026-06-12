---
title: "Kernel Panic on Ubuntu, with Linux 4.13.0-25-lowlatency"
date: 2018-01-22
forum: Installation &amp; Upgrades
---

### Post by dshinks on 2018-01-22
Hi All,

I updated to Ubuntu 17.10 the other day from 17.04 and since then I'm running into problems starting up.

From the grub menu, the default "Ubuntu" option just stops on a purple screen. I found after doing a bit of digging around (managed to switch to TTY1 during startup) that a kernel panic error was being produced; along the lines of "No init found".

Pressing "e" to edit the boot settings for the Ubuntu entry shows that it's using /boot/initrd.img-4.13.0-25-lowlatency.

If I go into to Advanced options for Ubuntu, I find the low latency option there, along with a generic option, and a generic option for an older version, and recovery options for all of them.

The generic version seems to boot just fine, as does the older version.

I could do with some help/advice on one (or both!) of the following:

* What steps should I take to investigate the problem with the -lowlatency boot option?
* If fixing that isn't an option, what could I do to make the "Ubuntu" option point at the -generic init instead?

So far, I've managed to set the default boot entry in /etc/default/grub, by setting it to "Advanced options for Ubuntu>Ubuntu, with Linux 4.13.0-25-generic", although that doesn't feel like the neatest way of doing it.

Any advice would be appreciated; I'm still relatively new to this!

Many thanks!

---


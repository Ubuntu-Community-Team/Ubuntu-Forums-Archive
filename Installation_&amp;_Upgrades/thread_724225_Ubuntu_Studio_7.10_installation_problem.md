---
title: "Ubuntu Studio 7.10 installation problem"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by ian davidson on 2008-03-14
Hi,

I installed Ubunto Studio onto a laptop. The inistallation seemed to go OK.
I did not have the machine networked at the time, and it dis not ask for a screen resolution.

When I boot the OS from the hard disk, GRUB runs OK, the boot screen shows, and the progress bar gets about 1/8 of the way along and then just stops.

Dead!

Any ideas?

Many thanks in advance,

Ian davidson.

P.S. judging from the number of similar messages in this forum it looks like the installation of UBUNTU
is not yet mature.

---

### Post by zvacet on 2008-03-14
Did you checked [md5sum](https://help.ubuntu.com/community/HowToMD5SUM) before you burned iso,burb it slow and check CD integrity?

---

### Post by ian davidson on 2008-03-17
Yes, I did a "check Cd integrety" before installing.

Did this on two different machines and is was OK on both.

Does it need the Network configuring to boot OK?

Another clue. If I boot the CD "as is" I get IRQ 15 nobody cared - error message and it does not boot.
So I F6 to more options and append "irqpoll" to start line - then it boots OK.

Could this be the problem.

As it looks like I will have to do another re-install, where can I find out the 
recommended partition layout for a 20G disk?

Many thanks for your response,

ian

---


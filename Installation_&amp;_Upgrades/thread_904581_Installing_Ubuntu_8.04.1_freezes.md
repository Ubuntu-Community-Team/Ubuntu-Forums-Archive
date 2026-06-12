---
title: "Installing Ubuntu 8.04.1 freezes"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by houzer on 2008-08-29
Hello all.
Complete Linux noob here. I've been curious about using Ubuntu for quite a while and finally tried to get started but am having some install issues.

I've been trying to install Ubuntu as the only OS on an old Gateway tower and it keeps freezing during the install. 

Quick specs:
Pentium III 750MHz
384mb RAM
64mb Video Card
100MHz FSB
80gb IDE Hard Drive (Western Digital)

I first tried installing from the alternate CD, made it all the way to "Preparing foomatic-filters" and then it locked up.

I tried the live CD next and could not get past partitioning even after setting them up with GParted before hand. 

So I went back to the alternate CD. I ran check CD for errors, the memory test, burned a new CD @ 4x speed. Now it's freezing at "Preparing iso-codes".

Partitions are set up as:
#1 / 10GB ext3
#2 /home 65GB ext3
#3 swap 1 GB

I have looked through the forums for any other ideas but don't know where to go from here.

Thank you in advance for any help offered.

-houzer

---

### Post by koym on 2008-08-29
houzor, not source of help but looks like we have a similar ?(s) as my Dell OptiPlex GX1 with 512MB ram, Pentium 3/450 MHz 16 gig HD having network card is amidst a memory test after verifying I have a good 8.04.1 and install attempt. L1 Cashe: 32k 4382 MBs; L2 Cache:512k 574Mbs Memory 64M 260 MB, Chipset Intel i440BX.

amidst the U8.04.1 install, monitor went gray; Watched it step by step; had coffee + breakfast + phone call; First had a blinking hyphen on CD port showing the HD was engaged; then the monitor grayed. Rebooted w/o CD and PC attempted to come up in old unrenewable Ubuntu. 

Then I rebooted with install disc U 8.04.1-desktop-i386.iso and I did the tests which appear to check out fully, WallTime is 45 & shows Pass 4 on Std Test, Zero errors

---

### Post by gjoellee on 2008-08-29
you don't have so much RAM. It passes the minimum requirements of the Live CD, but it is recommended to have atleast 512mb to run Ubuntu smoothly, you might wonna try Xubuntu instead:)

---

### Post by houzer on 2008-08-29
Okay, downloading Xubuntu now. We'll give it a go.

thanks!

---


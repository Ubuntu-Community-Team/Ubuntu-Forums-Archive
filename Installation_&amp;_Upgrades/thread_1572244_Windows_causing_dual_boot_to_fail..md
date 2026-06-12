---
title: "Windows causing dual boot to fail."
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by Ascent_NZ on 2010-09-10
Hi there,

This isn't so much a problem as one I have solved.

I've had Windows XP Pro installed on my Laptop for years. Recently I installed a dual boot of Ubuntu Lucid 10.04 as a project. The install went perfect and Ubuntu booted up fine no matter how many restarts I performed. 

The first time I tried to boot into Windows it performed a dskchk, which isn't inherently bad as it performed one with my now working setup too. Once Windows had loaded up and I restarted I find that the boot loader no long works and instead I get this error:

```
no module name found. Aborted.
Press any key to exit.
```After pressing enter:

```
Non-system disk or disk error.
Replace and strike any key when ready.
```Now this proved to be one big headache.

Booting from a live CD was fine, booting from a SystemRescueCD was also fine.

I could get it working follow solution 2 in [this guide.]("http://www.sysresccd.org/Sysresccd-Partitioning-EN-Repairing-a-damaged-Grub")

However that left me back where I started having a prefect boot into Ubuntu everytime and have it killed when I boot into Windows.

No solution I found and tried helped at all.

So last resort I made a bootable disk from my i386 folder and slipstreamed SP2 and 3 into it along with some SATA HDD drivers as the install wouldn't recognise the HDD without them. 

So with a fresh install of Windows and a fresh install of Ubuntu I now have it working and the Grub menu works perfect all the time everytime even after booting into windows.

Safe to say I have no idea why an old (dirty) install of Windows XP Pro would cause this but starting from scratch has fixed it for me.

Hope noone else has it as bad as this but hopefully this will save you looking too far for answers.

Mike

---


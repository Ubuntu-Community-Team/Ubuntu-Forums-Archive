---
title: "Booting and APT upgrade of Grub"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by junius123@hotmail.co.uk on 2010-01-17
OK, usual apologies if this is a serial repeat. Can't see it anywhere at first sight.  

I am loading 9.10 (K or U, makes no difference).  This installs 2-6-31.14.  Eventually I am unable to dissuade APT from upgrading to Grub 1.97 beta4.  One of two things can happen.  

1)  I am upgraded to a later kernel at the same time (currently 2-6-31.18).  This singularly fails to work, in that I end up with no working kernel at all and I can only run memtest (or Windows 7, which is about as much use): good for the soul no doubt, but frustrating.  "Solution": tar up the whole of /boot beforehand and then reinstate it afterwards.  I am back to square 1, but at least a working square 1.  

2)  I persuade APT not to upgrade the kernel.  I then get 14 (and 14 recovery) in my grub.cfg, but boot fails dramatically, and it becomes apparent that it has forgotten about /dev/sda, my hard disk.  Further investigation shows that I have a new initrd.img in /boot, which doesn't work properly; reinstate the backup version, and all is well.  

What is going on?  Is it just me?  How come there aren't crowds of protesting peasants with pitchforks outside Canonical Towers?  

If anyone can cast any light on this, please do so.

---

### Post by Leppie on 2010-01-17
> **junius123@hotmail.co.uk said:**
> 1)  I am upgraded to a later kernel at the same time (currently 2-6-31.18 ).  This singularly fails to work, in that I end up with no working kernel at all and I can only run memtest (or Windows 7, which is about as much use): good for the soul no doubt, but frustrating.  "Solution": tar up the whole of /boot beforehand and then reinstate it afterwards.  I am back to square 1, but at least a working square 1.
AFAIK the latest stable kernel is the 17, are you using the "proposed" repo? 

> **junius123@hotmail.co.uk said:**
> 2)  I persuade APT not to upgrade the kernel.  I then get 14 (and 14 recovery) in my grub.cfg, but boot fails dramatically, and it becomes apparent that it has forgotten about /dev/sda, my hard disk.  Further investigation shows that I have a new initrd.img in /boot, which doesn't work properly; reinstate the backup version, and all is well.
but all is working now?

---

### Post by kansasnoob on 2010-01-17
I've installed and set up *buntu for about 40 seniors and I always go to Software Sources when I'm done and under the Updates tab I make sure that only the Important Security Updates is ticked and that Release Upgrades is set to never.

It helps to prevent a lot of breakage :D

On my own machine I install everything including the Proposed Updates because I'm a lunatic.

---

### Post by junius123@hotmail.co.uk on 2010-01-17
Dear Leppie, Kansasnoob,

Thanks.  I do indeed have everything in sight ticked, because (being as I am an incurable optimist) I kind of assume that nothing quite this drastic will occur if I do; or at least, it will have occurred to some other poor unfortunate first.  More fool me.  And yes, this is my own machine: even I am not so cavalier as to trash a company asset with such regularity!  

Leppie - just the same happened when I got 17.  But of course, it is most unlikely to be the kernel itself that is causing this peculiar behaviour; rather some other dross I pick up from "Proposed".  

I guess that (exploring the wilder shores of Kubuntu not being my main mission in life at the moment) I will be well advised to remove one or two ticks, as suggested.

---

### Post by Leppie on 2010-01-17
maybe it's better to do a clean install?
if you want to test some stuff, better make full system backups on a regular base.
the proposed repo is for prereleases, so installing from there should not give too much trouble. i believe that the backports are alphas, so if you do not know how to undo the updates this repo pushes through, it may be better to not use it.

---

### Post by junius123@hotmail.co.uk on 2010-01-18
Backports are alpha - really?  OK, here goes with the rubber (that means pencil eraser in my neck of the woods, so stop sniggering at the back there...).  

As for system backups, you are of course quite right.  But to quote St Augustine of Hippo (of dubiously blessed memory), "Lord make me virtuous, but not just yet".  Somehow it is never ***quite*** the right time to burn holes in all those DVDs (there's always another package or 600 or so to install: "Just one more little one can't hurt, can it?"), and by the time you really, really want to have hold of your backup it's too late!  Meanwhile, God bless [FONT=Verdana]systemrescueCD.com[/FONT]...

My star performance so far is contriving to give **sudoers** 0460 permissions.  God only knows how I managed it, but trust me, it is ***so*** not a good idea. You can't have half as much fun with Windows; not on purpose, anyway...

---


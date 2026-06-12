---
title: "ubuntu installed from livecd but refuses to boot despite every workaround in the book"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by Spaff on 2008-11-17
OK so I've gone for a dual boot (XP and ubuntu 8.10) on my master hard disk, partitioning 50% of the 250gb into 3 (for root, docs and swap) and install via the liveCD all went smoothly until it came to rebooting and loading up the new OS.

The OS boot menu pops up inviting me to load XP (which works just fine) or give ubuntu a go. When I go for ubuntu it tries and tries and tries but to no avail. The loading screen is displayed for some time then I am eventually booted out to BusyBox with the initframfs prompt.

The only thread I could find that seems to come anywhere close to my trouble is this one: [http://ubuntuforums.org/showthread.php?t=765195](http://ubuntuforums.org/showthread.php?t=765195)

However the problem there seems to be that users can't even get the cd to boot whereas I have no problem with that, it's just after the install that I get to the same point (busybox) without a clue.

So loading up the liveCD to jiggle about I discover that my SATA drives (I have 4, all different sizes) keep swapping their positions each time I boot and a helpful chap in IRC suggests I try editing my menu.lst which I've done but changing the root  (hdX,X) line makes no difference as obviously my drives keep switching.

Another chap suggests i forget about my sdd5/sdc5 (as they keep changing) and instead concentrate on my UUID's, however the correct UUID is definitely being used in the grub menu.lst so no editing seems to be necessary.

Then, from the thread listed above I added all_generic_ide floppy=off irqpoll to my menu.lst as a workaround and I am STILL getting no closer

I am totally at a loss now.

This is already the second attempt at an install and with a different iso (32bit as opposed to 64bit) burned to a fresh disc, that has been checked, but I cannot get past this point.

Both installs seemed to go fine. Neither will boot.

Anyone care to lend a helping hand?

The great irony is that I am writing a feature on the simplicity of a fresh linux install on a home PC, and yet 14 hours after first attempting the setup I am still stuck at my computer tearing my hair out.

Perhaps I can change the angle of my piece to the helpfulness of friendly ubuntuforums users?

---

### Post by Spaff on 2008-11-18
Anyone?

I've been through so many guides and threads in search of  solution and it's driving me crazy.

If nobody can answer this conundrum then may I ask instead, would a fresh install on a newly formatted slave HDD have any better results? This would then not need to have a Windows partition and could be purely for ubuntu.

Somebody suggested to me that would work but I am dubious as I can't see how it gets around my original problem, unless that is in some way related to my partitions?

Mucho gracias

---


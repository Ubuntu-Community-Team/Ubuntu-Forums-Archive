---
title: "At installing, fd0 error then hangs..."
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by apetrusa on 2007-05-16
Hi,
I have an older laptop (Dell CPi, 266XT) with 256 MB ram.
At this particular moment, it runs Suse Linux (which installed itself qithout a hitch).
I downloaded teh Ubuntu 7.04 which I am trying to install (and wipe out the Linux install).
However (regardless what I try from the menu - Live, memory tests or the install), it gets to this error:
Buffer I/O error on drive fd0, logical block 0.
As far as I know, this is the floppy (which I don't have).
I checked my BIOS, and my floppy is disabled, while in the Boot device order there is the CD as first choice then the HD as second... no floppy in sight.
So, how do I go around this and instal Ubuntu?

---

### Post by flying_icarus on 2007-05-20
Hi, I just ran into the same thing... there is a discussion about this on
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306") and the last post suggests the mistake was burning a CD ISO onto a DVD, and that burning it on a CD solved the hang.

In my case I too burned a CD ISO onto a DVD, so will now try to do it the right way. ;)

Other options are trying with an alternate install CD...

---


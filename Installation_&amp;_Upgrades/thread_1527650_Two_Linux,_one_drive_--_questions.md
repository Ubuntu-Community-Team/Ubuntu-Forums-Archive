---
title: "Two Linux, one drive -- questions"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by Calidore on 2010-07-09
Hi, all.  Briefly, I'd like to set up a two-Linux drive, but need some  help with the details.  More depth follows.

Back in the day I fooled around a bit with FreeBSD a bit (ver. 2.x), so I  do have a tiny bit of familiarity with Unix commands.  At the time, I  dual-booted with Windows, which I remember being pretty easy to set up.

Now I've decided I'd like to get to know Linux and get a better grasp of  Unix in general.  I've just learned of the existence of Linux from  Scratch, which sounds great, but you need a working Linux installation  to create a fresh one.

I have a spare 160GB external Seagate that isn't doing anything, so what  I'd like to do is split that in half, installing Ubuntu on one and  using the other for building LFS.

However, partitions seem to be a bit more complicated in Unix than  Windows.   In the latter, each piece is effectively an independent  drive.  In Unix, however, you have partitions for home, root, swap,  etc.  It seems partitions in Unix are like top-level directories in  Windows, which messes up my visualizing.  Dual-booting Windows and  FreeBSD was easy because Windows took its piece and ignored the other,  but I'm not sure how to create separate Linux installations on one  drive; it seems like they'd intertwine.

I should mention that I've done a test Ubuntu installation on the  external drive just to make sure it will boot, and no problems there.   (Annoyingly, my BIOS only allows one hard drive to be designated as  boot, so I have to go into the setup and manually switch it between my  main and the external drives when I go back and forth, but I can live  with that.)  So now I want to know:

A) If I can simply shrink the existing installation partition and use  the empty space for another for LFS, or 

B) If I have to erase the drive and redo it from scratch.

And in either case, how.  A general explanation to help me picture Linux  partitions and layout would be great and appreciated also.

My system, by way of reference:

Intel i7 860 (4 cores plus Hyperthreading) on an Asus P7P55D motherboard
4 gigs RAM
Nvidia 8600 GT graphics card
WD 640GB main drive
Seagate 160GB USB external drive
Plextor PX-880SA DVD drive
USB keyboard & mouse
Dell E228WFP flatscreen monitor
Realtek PCIe integrated NIC

While I'm asking things, I do have one general question that's been  bugging me for years:  Why is it always recommended (both for Windows  and Unix) that a swap file be either 1x, 1.5x, or 2x RAM.  Seems to me  that having more RAM means needing less swap space.  With my 4 gigs, of  which XP uses 3, I have swap turned off entirely with no problems.  Does  Unix handle swap differently?

Thanks much!

Best,

Calidore

---


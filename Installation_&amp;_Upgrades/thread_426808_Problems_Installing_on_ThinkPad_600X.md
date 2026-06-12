---
title: "Problems Installing on ThinkPad 600X"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by Jaybop on 2007-04-28
I've tried installing both X/Ubuntu 7.04 on my ThinkPad 600X to no avail.  There seems to be a problem with the installer detecting DMA on my internal CD-ROM drive, when it should be disabled.. thus causing lots of I/O errors.

I had similar success with Knoppix UNTIL I used one of the cheat codes, "nodma" which as it implies, disables DMA.  Now, when I started Knoppix, I simply used that command line option during startup.  I want to try a similar command at start/installation of X/Ubuntu, but I can't seem to find it.  I've searched for this option, but I only find:

- disable DMA support: Alt-F2, Enter, hdparm -d0 /dev/hdc
- proceed with install: Alt-F1, Enter

Which looks like it needs to be used somewhere *later* in the installation.

I've also suggestions to place "ide=nodma" or "nodma" in the F6 boot options, but that doesn't seem to work either.

Is there a way to disable DMA all together in the F6 Boot Options (or better yet, just the CD-ROM)?

TIA.

---

### Post by Jaybop on 2007-04-28
On second inspection, it appears that the installation is looking for a non-existent floppy drive (fd0) and that's where my first I/O errors come from.  I *think* I read something about ThinkPad floppy complications during installtion..

---

### Post by Jaybop on 2007-04-28
I've tried adding "floppy=nodma" and "floppy=thinkpad" in the Boot Options, but I still receive the following errors immediately after "uniform cd-rom driver revision: 3.20:"

end_request: I/O error, dev fd0, sector 0
end_request: I/O error, dev fd0, sector 0
Buffer I/O error on device fd0, logical block 0

[ this goes on for a while ]

Any ideas?

---

### Post by rnb0588 on 2007-08-22
Had a similar problem.  had to disable the floppy in the BIOS then boot up.  otherwise it would churn on the fd0 errors.  I have a thinkpad T22

---


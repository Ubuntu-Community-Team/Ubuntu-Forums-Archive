---
title: "grub error 18"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by jem7v on 2006-12-18
Running Edgy on the 2.6.17 kernel, as I have been since late October.  I just installed my routine updates this afternoon, which had been piling up for a month or so (because for some reason, I have to manually Refresh my sources in Synaptic before it actually notices updates even though I have it set to check every day)... Included were kernel image headers, but not actually any new kernel that I noticed.

And when I went to reboot, um, I got:
Error 18: Selected cylinder exceeds maximum supported by BIOS

which is retarded, because I've been booting up JUST FINE since I upgraded to Edgy.  I can still boot with the old 2.6.15 kernel and work from a command line, but it won't load the latest X server and graphics drivers obviously.  I admit that I have an older motherboard and a large hard drive, and it's Certainly conceivable that the latest kernel updates were saved somewhere on the hard drive where my BIOS can't read, whereas the older kernels are still at the start of the drive where it's safe.  (It would seem to be the logical assumption.)


All the solutions I've found so far have suggested "moving your boot partition to the front" or "installing grub in a partition at the front of your hard drive," etc, etc, etc.  My boot files are in a FOLDER labeled boot (on my hda1 partition), but they certainly aren't on their own partition, and I have no idea how to create a tiny partition for them at the start of the drive, nor what I would have to do once I created that partition.

Any idea how I would go about doing this partition work?  It would even be helpful if somebody could point me toward an excellent (rather than sub-par) tutorial about editing/creating new partitions from the command line or a live CD.  I have no desire to reinstall Ubuntu because I have a lot of important information saved in my home directory (which, sigh, is Also not on a separate partition, thanks to the joy of the installer's automatic partitioner).  I could probably back most of it up through devious methods if I have to, but the important thing is that I don't WANT to.

Help would be greatly appreciated, because right now I have to ask for suggestions in WinXP on our other computer, and it's so yucky to work with.

---


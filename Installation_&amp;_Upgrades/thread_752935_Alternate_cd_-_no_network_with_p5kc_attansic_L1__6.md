---
title: "Alternate cd - no network with p5kc attansic L1  64bit amd64 install"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by higginse on 2008-04-12
Problem & workaround.

I am in the process of installing gutsy ubuntu-7.10-alternate-amd64 on an
Asus P5KC motherboard and encountered a problem with the alternate cd
installation.

The alternate install doesn't recognise the Attansic L1 Gb network card by default,
though the live cd does.

To workaround this:

1. I booted the livecd (64bit version - first time used the 32 bit drivers and couldn't figure out why I got an invalid module format error)
2. Created a partition on the disk I was planning to install onto
3. copied the atl1.ko driver onto the partition.
4. rebooted using the alternate cd.
5. When it failed to detect the network, I switched to a console window(alt-F2) . From this -
  a. Mounted the partition created before.
  b. copied the driver into /lib/modules/<kerner-version>/kernel/net/atl/atl1.ko
  c. Installed the driver with modprobe. I tried insmod first, but it actually needs mii.ko also, so 
     modprobe is better.
6. Returned to install window, and this time it detected the net card without a problem.

Some notes:
  The Invalid module format error 32bit vs 64bit  had me scratching my head for a bit.
  The alternate cd should really have the atl driver packaged by default. 
  Not sure where I should recommend adding it for Hardy (if it's not there already).
  I only used the disk to copy the files as I don't have a floppy on  the box and it seemed
  like the easiest as the disk as new and empty!
  Incidentally I wanted the alternate cd because I want to do a raid installation.

---


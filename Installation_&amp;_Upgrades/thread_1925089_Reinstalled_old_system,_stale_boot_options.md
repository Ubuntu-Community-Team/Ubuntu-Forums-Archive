---
title: "Reinstalled old system, stale boot options"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by inphektion on 2012-02-13
I have an old dell workstation i scraped dust off of and booted.  Had an old intrepid install with md raid 1 on 2drives.  I put a 12.04 alpha2 alt x64 boot disk and reinstalled, reconfigured md raid but didnt low level format the disks.
I can successfully boot off the new md raid into 12.04 but in the grub menu there are two entries: 
One for /dev/sda1 intrepid and the other for /dev/sda2 intrepid.
They arent valid but update-grub's os prober always finds them.

Any clues how to purge this?

---


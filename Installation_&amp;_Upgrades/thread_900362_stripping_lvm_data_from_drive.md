---
title: "stripping lvm data from drive"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by isecore on 2008-08-25
I decided to reinstall my system today. I'm going for the AMD64 and setting up my drives in LVM, which means I'm installing from the alternate CD.

My system previously had an LVM setup which I for various convoluted reasons decided to abandon. I had two drives in that group which was failing, and having bad experiences with removing drives from groups I decided to simply reinstall instead. 

I took backups, then yanked the failing drives and fired up the alternate install disc. However, when it comes to setting up the LVM it complains there's already LVM data on the drive, that there's a volume group with the name I want (which it autosets to the hostname of the computer), and that it was missing devices with [really long UUID].

I've been trying for the past 45 minutes to figure out how to remove this data from the drive so I can install a fresh LVM onto it. I'm currently booting from the 8.04 live-cd and working with LVM from there, but I can't seem to get rid of this data. If I use fdisk to remove it from the drive it pops right back after a reboot, and trying to do a vgremove it gives me this error:

```

  Couldn't find device with uuid 'j91k4N-X0SS-TIcf-e6E6-PgCQ-NWJN-Moo54I'.
  Couldn't find all physical volumes for volume group superbeast.
  Couldn't find device with uuid 'j91k4N-X0SS-TIcf-e6E6-PgCQ-NWJN-Moo54I'.
  Couldn't find all physical volumes for volume group superbeast.
  Volume group "superbeast" not found

```

I just want to strip whatever LVM-data is on that drive so I can start fresh. The same goes for the other drive I'll add to the volume group later. Any pointers as to what I'm doing wrong?

---


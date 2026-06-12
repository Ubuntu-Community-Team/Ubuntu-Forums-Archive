---
title: "Lubuntu 20.04 failing to boot"
date: 2020-06-07
forum: Installation &amp; Upgrades
---

### Post by devilriderman on 2020-06-07
Hi, 

Went through my installation, copied a youtube video for the partitioning.  Brings to a blue boot screen giving me options to boot from 4 things, and non of them work.

I want to have Lubuntu installed alone.

I tried to install again but this time getting Lubuntu to install on the largest partition.  Same result.

I'm enclosing pictures of my bios that I change a few things(ufei, legacy boot etc) to no avail.

Also, I'm enclosing a pic of my partition.

Thanks in advance for the help.

---

### Post by guiverc on 2020-06-07
It might have helped if you provided a link to the youtube video; whilst I'd likely not have watched it, I may have known the source/creator, or at least what idea of trust I'd put in it being accurate/helpful.

You provided a KDE Partition Manager screen of four partitions, but no details to make it helpful. You haven't provided anything that tells us what they are allocated for.  On most modern Lubuntu systems a single partition alone is used (a partition for / alone, esp. for BIOS) or two partitions on UEFI (one for /, and one for /boot/efi/ but I don't see an EFI partition in your diagram either). 

(On troublesome devices (small UEFI netbooks) I usually just let the installer use it's defaults, then if I'm not happy I either adjust or re-install.)

---

### Post by GhX6GZMB on 2020-06-07
Let the Lubuntu installer do the partitioning. You can define more than one partition during install and also the mount points.

Boot from a live USB/DVD until you reach the (almost empty) live desktop. Then just start the installer. You'll be asked about language and keyboard layout before coming to partitioning.
I recommend that you select "format" for all partitions.

---

### Post by CelticWarrior on 2020-06-07
The suggestions above are for selecting "Erase and install..." instead of manual partitioning. It's much better to let the installer automatically choose the best partitioning layout when one doesn't know what to do. Very likely the video you watched isn't applicable to new UEFI computers as already commented - an EFI partition is required and not shown in your screenshots.

---

### Post by devilriderman on 2020-06-08
Thanks guys!  

When I first went to install and let Lubuntu do it, it looked like it was going use the whole partition without any UEFI.  Maybe I didn't observe it right.  This time it's Installed and given me a tiny UEFI partition and I'm here on Lubuntu typing this now.  Appreciate it!

---


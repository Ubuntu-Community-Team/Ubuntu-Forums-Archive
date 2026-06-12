---
title: "XP wont boot aftr 6.06 install"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by SneakPeak on 2007-05-25
Hi All

I installed Ubuntu 6.06 after using a liveCD with GParted to compress my XP partition and create a new ext3 partition, a fat32 partition (to use as a common area) and a swap partition.  Installation went well and Ubuntu is working fine.

Probelm is XP won't boot. The system hangs when I select XP from the grub menu.  I can see all the XP files from Ubuntu.  They are all still on the disk in the NTFS partition.  I have even opened 1 or 2 documents in read only mode.  XP just won't boot.  Not in safemode, not in last known good configuration, nothing.

XP booted fine after I had compressed its partition and created the new partitions.  I used it for a few days with no problems before installing Ubuntu.

Any advice?:(:(

---

### Post by geezerone on 2007-05-25
Have you tried 'fixmbr' from a Recovery console on your windows XP boot disk. Once you do this though Grub will be wiped but you can reinstall Grub again. The supergrub disk(free download)  also will fixmbr too as well of a host of other tools.

HTH :)

---

### Post by SneakPeak on 2007-05-25
Problem Solved:

When I installed Ubuntu it would not install when ACPI for APIC was active in the BIOS.  I had to deactivate it.  Ubuntu installed and I forgot that I had deactivated it.  Windows wouldn't boot but as soon as I reactivated ACPI for APIC in the BIOS windows suddenly started booting again.  Strangely enough Ubuntu now boots with ACPI for APIC activated but it did not during the installation.

Anyway all is well that ends well.  Thanks to those who offered advice.:D

---

### Post by SneakPeak on 2007-05-26
Hi All

My ACIP for APIC problem is back.  XP won't boot with it disabled and Ubuntu won't boot with it enabled.  I get kernel panic errors.

Going to search the archives to see if I can solve.

Sneak Peak:o

---

### Post by confused57 on 2007-05-26
> **SneakPeak said:**
> Hi All

My ACIP for APIC problem is back.  XP won't boot with it disabled and Ubuntu won't boot with it enabled.  I get kernel panic errors.

Going to search the archives to see if I can solve.

Sneak Peak:o

What you can do is add "acpi=off", without quotes, to your menu.lst kernel line...you can try it temporarily by highlighting your Ubuntu entry in your grub boot menu, press "e", then add it to your kernel line, then press "b" to boot.  If it works, you can make it permanent.

---

### Post by SneakPeak on 2007-05-28
Thanks Confused57

That seems to have solved the problem.  By the way the problem was intermitent I would say 1 in 5 boots was a problem.  The rest of the time it just went through.

Cheers

Sneak Peak:)

---


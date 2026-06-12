---
title: "&quot;out of memory&quot; error when trying to install 22.04"
date: 2022-08-27
forum: Installation &amp; Upgrades
---

### Post by davidjmhansen on 2022-08-27
I created multiple boot versions of 22.04 and tried this many times.

I get to the menu and select "Try or install Ubuntu ...."

When I make that selection, I get the "out of memory" error.

I tried unloading the squashfs then modifying /etc/initramfs-tools/init*config to change the memory settings many different sizes.  (I have 64GB ram in my very new MSI  ge77HX I7-12800HX laptop with a rtx-3070ti graphics card).

I tried changing changing the resolution of my screen in the bios from 2560x1440 to many lesser values.  (Because I read that higher resolution screens consume more grub memory)

I read that this was caused by a 32 bit version of GRUB not being able to deal with large amounts of memory  (Addressing more than 4GB).

I tried  many versions of ubuntu.  The studio version installation went the farthest one time.  I actually got to a graphical screen and selected time zone, hard disk (NVME SSD) partitioning, but it then failed after the reboot with an "out of memory" error.

---


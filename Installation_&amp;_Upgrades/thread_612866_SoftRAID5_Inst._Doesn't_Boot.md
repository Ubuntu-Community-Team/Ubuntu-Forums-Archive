---
title: "SoftRAID5 Inst. Doesn't Boot"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by hosk on 2007-11-14
Hey,

I recently have tried to install Ubuntu Alternate on a both RAID5'd and unRAIDed set of 4 500GB disks connected to a M2NPV-VM Motherboard (fake)RAID controller and come up with the same set of responses.  I either end up with a non-booting blinking cursor and blank screen, or I get a DISK BOOT FAILURE error.  

I properly partition them every time, a small partition on the front of /dev/sda for the /boot and software RAID the rest up properly, and the machine refuses to boot. It doesn't even see GRUB.

Any help would be much appreciated, I've been messing with this for like a week straight. Random suggestions also appreciated, I'm willing to try anything.

---

### Post by hosk on 2007-11-14
I should also note I tried them unRAIDed and RAIDed according to the motherboard, I've also set it up with 150mb /boot on /dev/sda1 and the rest as LVM and still nothing either way.

---


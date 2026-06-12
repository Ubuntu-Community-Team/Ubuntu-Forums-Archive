---
title: "when GRUB fails - pls suggest me bootloader"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by Average_Joe on 2007-12-07
Hello,

I have installed *buntu on dozens of machines, but not many Vista machines.  On the Vista machines I have done, GRUB did its job.  I ran into a little problem and would appreciate advise.

I have here a Toshiba laptop, I did the following:
* blanked out hard drive 
* installed Vista onto a 20GB partition (primary, /dev/sda1)
* then installed XP Pro onto a 40GB partition created by using the Windows installation CD.  To my surprise, Windows made my 40GB into an extended partition.
* at this point I could boot into XP, but not into Vista, and that was completely expected

* Now I installed Ubuntu 7.10 which had been my plan all along so that I could take advantage of nice GRUB to triple boot

* GRUB found Vista, but not XP  (again, a surprise for me, GRUB has always done such a good job in the past finding all bootable partitions of many OS versions)

Can you recommend me a bootloader that I can install to the disk, which will pick up all three of Vista, XP, and Ubuntu 7.10?

Thanks!!

---

### Post by Pumalite on 2007-12-07
Add Vista to your menu.lst. (hd0,0)

---

### Post by Average_Joe on 2007-12-07
Thank you,  I will give this a shot.
I figured I needed a machine ID (one of those long code things) in order to get the volume recognized.
I hope  adding the simple GRUB device and partition notice will work as you described.

---


---
title: "Adding BackTrack2 to Grub menu.lst"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by w116tjb on 2007-10-30
Okay, so here's the current setup...

sda1 = Windows XP
sda2 = Ubuntu 7.10
sda4 = BackTrack2
sda3 = extended
  -sda5 = swap (swap is a sub partition to sda3 according to gparted)

When I installed BackTrack2, it overwrote my MBR but I got all that fixed. When the grub menu appears, I can select between Ubuntu and XP, but it doesn't give an option for BackTrack. I believe BackTrack is located at (hd0,3), but I could be wrong. What should I add to my grub menu to allow me to boot into BackTrack?

Thanks!

---

### Post by w116tjb on 2007-10-30
Bump?

---

### Post by w116tjb on 2007-10-30
I figured it out. Just in case anyone else is having the same problem, here's the solution:

Location: /boot/grub/menu.lst

> 
title 		BackTrack

root 		(hd0,3)

kernel 		/boot/vmlinuz ro root=/dev/sda4

boot


Title is the name that appears on the grub menu.
Root is the location on the disk. 0 denotes that it's the first hard drive. It'd be 1 if it was the second hard drive. The 3 in my example denotes the location on the first disk. This number is usually 1 less than the partition it's on. So if it's on sda4 on the first disk, it'd be (hd0,3).
Kernel tells GRUB where the kernel is. 'ro' means read-only. I tried using 'rw' instead, but it gave me errors. Root is the partition it's on.
Boot is self-explanatory. 

Hope I explained it correctly.

---


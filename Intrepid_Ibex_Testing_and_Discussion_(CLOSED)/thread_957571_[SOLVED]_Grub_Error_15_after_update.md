---
title: "[SOLVED] Grub Error: 15 after update"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by belfasttim on 2008-10-24
Hi -- I'd been running 8.1 on a spare machine and really liking it. I booted up this morning, saw that a substantial number of updates had been released so I installed them and rebooted as prompted.

After boot, grub gives me an "Error 15: File not found" on all options in the grub menu 

Ubuntu intrepid (development branch), kernel 2.6.27-4-generic
Ubuntu intrepid (development branch), kernel 2.6.27-4-generic (recovery)
Ubuntu intrepid (development branch), kernel Last successful boot
Ubuntu intrepid (development branch), memtest86+

I am wondering if a new kernel was built and installed that didn't update the grub loader menu?

Any help appreciated.

---

### Post by caljohnsmith on 2008-10-24
How about booting your Live CD, open a terminal (applications > accessories > terminal), and do:
```
sudo fdisk -lu
```
Post the results of that, and also figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
sudo blkid
ls -l /mnt/boot
```
Please post the output of all the above commands. :)

---

### Post by belfasttim on 2008-10-24
Thanks Caljohn! 

As suspected, it turned out that the new kernel was -7, not -4, and Grub naturally wasn't finding the -4. I edited the loader list to point to -7 and it booted right up!

Thanks for the help.

---

### Post by caljohnsmith on 2008-10-24
Glad you got it working with too much hassle; cheers and have fun Ubuntu-ing. :)

---

### Post by freakshow26 on 2008-10-24
> **belfasttim said:**
> Thanks Caljohn! 

As suspected, it turned out that the new kernel was -7, not -4, and Grub naturally wasn't finding the -4. I edited the loader list to point to -7 and it booted right up!

Thanks for the help.

im have the same problem and im kind of new to linux show what u did so i can get back in ubuntu lol

---


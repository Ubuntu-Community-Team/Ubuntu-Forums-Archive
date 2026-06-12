---
title: "boot problem"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by gustavoberman on 2006-09-28
Hello there!

I got this problem:
I installed ubuntu dapper64 with the desktop cd, and at the partition selection I did 6 partitions (/, /usr, /var, swap, /tmp, /home), all of them in ext3.
The install process ended without problem.
But when I try to boot the computer it doesn't find grub so it says "insert a boot disk"

If I boot with the cd and select to "boot from the first partition" it boots ok.

It seems that it cannot find grub at the mbr.

It is a sata drive (the only sata drive) and I have just 1 ide (the cdrom)

Any help?

---

### Post by gustavoberman on 2006-09-29
I reached the solution: the / partition was not set to boot!!!! ](*,)

---

### Post by piotrwoj on 2006-09-29
You will correct the file: /boot/grub/menu.lst and write command:
grub-install --recheck --no-floppy /dev/sda or:
sda1, hdax etc. You must chroot on other bootcd - rescuecd
P.S My english is fatal - sorry
-------------------------------------------------
 
[DRZWI]("http://www.drzwi-warszawa.pl/")

---


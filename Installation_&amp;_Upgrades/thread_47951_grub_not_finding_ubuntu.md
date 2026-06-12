---
title: "grub not finding ubuntu"
date: 2005-07-10
forum: Installation &amp; Upgrades
---

### Post by plewisfdx on 2005-07-10
I have successfully installed HH on my laptop, and want to install it on my desktop as well.  I have WinXP set up on hda, a cdrom on hdb and a partitioned 80g disk on hdc that has been through the Ubuntu install, just never booted.

It gets to grub, "Grub loading stage 1.5", then it had an error 12.  I have a linux boot disk, and I changed the settings on menu.1st a couple of times, and have gotten error 17, and 21, so I know my changes are in the right place, just not doing the right ones.

The partitions are :
1. 100 mb old SuSE boot partition,that I don't need anymore, and not big enough for much.
2. 10 gb partition that I installed grub into, and apparently put GRUB here too.
3-9 data

So on my emergency boot disk, I erased the old hdc1 stuff, and copied the contents of the boot folder to it.  This is where I have been making my changes.  hdc2 should show as root (hd2,1)??  this is one of those errors, error 21.

How can I make grub skip over the first partition and run the grub on the second?  My Ubuntu disk hangs on install, so I only have the rescue disk, and a little linux knowledge.

Thanks,

phil

---

### Post by plewisfdx on 2005-07-11
bump

---

### Post by mingus on 2005-07-11
*3-9 data*

Does this mean something?

*hdc2 should show as root (hd2,1)??*

No, /dev/hdc is in grub syntax (hd1) because it is the second hard drive boot device.  The "1" is saying that it is the second partition, but aren't you making the changes now in the first partition where you copied /boot into?  

Additionally, when grub is installed the initialization program (stage1) is modified to include a pointer to where it should find stage2 (the actual loader).  If you have the grub files located on the / partition under /boot *and* you have a separate partition which is also /boot, this pointer may be wrong.  So if the above does not work, and you want the boot loader on the second partition under /, then make the necessary changes in menu.lst on the second partition and then do:
$sudo grub
> device (hd1) /dev/hdc
> device (hd0) /dev/hda
> root (hd1,1)
> setup (hd0)
> quit
This assumes you want to install grub to the MBR on the W$ disk hda and hence dual-boot from grub.  Since there is some confusion already, a very good idea to have XP install media or a W98/ME bootable diskette handy should you need to get back the W$ MBR (which is easy to do).

---


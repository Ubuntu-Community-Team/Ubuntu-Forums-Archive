---
title: "boot windows xp and 7 with grub"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by paintbalforjesus on 2009-11-15
I previously had windows 7 installed and Ubuntu 9.10, I was using grub and it would let me get to either one no problem.

I just finished installing windows XP, of course this overwrote grub, but I got grub back, but now I can't get grub to boot into windows 7.  When grub boots it still says "windows vista (loader)" (the same thing it said before I installed windows XP, but now when I click on that it goes to XP.  There are no other non-linux options.

My current configuration is:
first disk:320 gb
    first partition: sda1 ubuntu 9.10
    second partition: sda2 windows 7 reserved stuff
    third partition: sda3 windows 7 itself
    fourth partition: sda4 files stuff

second disk: 1tb
    first partition: sdb1 files stuff
    second partition: sdb2 windows XP

I realize none of this is optimal, I've been just patching it together how I could for a while, I plan to do a complete wipe of both disks and reinstall around Christmas time when I get a break from college, but for now I would really like to find a temporary solution that would let me get to all my operating systems


my current grub menu.lst looks like this:

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		9227f158-d0a9-40ea-946d-ffb221b479d5
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=9227f158-d0a9-40ea-946d-ffb221b479d5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		9227f158-d0a9-40ea-946d-ffb221b479d5
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=9227f158-d0a9-40ea-946d-ffb221b479d5 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		9227f158-d0a9-40ea-946d-ffb221b479d5
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=9227f158-d0a9-40ea-946d-ffb221b479d5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		9227f158-d0a9-40ea-946d-ffb221b479d5
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=9227f158-d0a9-40ea-946d-ffb221b479d5 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
uuid		9227f158-d0a9-40ea-946d-ffb221b479d5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


any help would be greatly appreciated.

---


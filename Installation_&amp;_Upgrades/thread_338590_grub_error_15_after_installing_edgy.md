---
title: "grub error 15 after installing edgy"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by Polygon on 2007-01-14
I just upgraded from dapper to edgy (by using the live cd and then just installing over my previous installation), and in the process i wiped my / , /boot, and /swap partitions

and then after it was done installing, if i try to select ubuntu from the list, it says "grub error 15: file not found" !

how is this even possible after a fresh reinstall anyway?

anyway, here is some info:

my menu.lst:

> title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hde2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hde2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdf2
title		Microsoft Windows XP Home Edition
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1



and here is my partition table

[[IMG]http://img156.imageshack.us/img156/1272/screenshottf9.th.png[/IMG]](http://img156.imageshack.us/my.php?image=screenshottf9.png)

what am i doing wrong... i really hate grub. Every single time i upgrade or reinstall its always grub that screws up...

---

### Post by Polygon on 2007-01-14
bump

---

### Post by Polygon on 2007-01-15
I solved this:

turns out a couple things were wrong

in the menu.lst

"root (1,0)" was wrong. I changed it to (0,0)

also the path to the kernel and the initrd file were wrong. they were at /boot/blahblah and i changed it to /blahblah

then i just pressed b (for  boot) and it worked. I also had to manually change it in the menu.lst so it didnt happen agaoin =P

---


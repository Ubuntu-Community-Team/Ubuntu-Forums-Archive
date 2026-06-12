---
title: "Clone a USB startup disk"
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by Iusedtowearatie on 2011-04-19
I often run various computers from my Ubuntu 10.04 USB startup disk. Every now and then, people get interested and want a copy of their own. Since I have installed a few extras (VLC, codecs, flash etc) on the disk, not just the out of the box 10.04, I would like to create a clone of the USB startup disk, to give away.
How can it be done?

---

### Post by alterpinguin on 2011-04-19
use dd
(see: man dd)
-
The destiny usb-stick has to be the same size or bigger
as your source.
-
and check, that you dont copy the wrong usb-stick (the empty one)
to your source!
-
If the new destiny usb-stick has a more space, then after the copy
you can use parted to add a new partition or to resize some partitions.
-
asume your sourc usb is /dev/sdc
then you plugg-in the new usb and this will be the next as /dev/sdd
!check! then you can duplicate with dd
dd if=/dev/sdc of=/dev/sdd
you may add a bs=1024 or bs=4K to write in bigger chunks ..

!and you know, you overwrite the new usb, thats you have to secure any data on it, and copy it back later .. .. or it is lost!

---

### Post by Iusedtowearatie on 2011-04-20
Perfect! Worked exactly as I had hoped.
Many thanks for the detailed advice!

(Note to others: Depending on which distro you use to perform this, you may find that you need to add su or sudo to the recommended command line. Also, it's worth putting some effort into checking if the USB:s are sdb or sdc or sdd...) :)

---


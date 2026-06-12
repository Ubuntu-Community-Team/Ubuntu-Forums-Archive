---
title: "My solution for the busybox problem (install of Ubuntu 8.04)"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by publicidadno on 2008-05-03
I have solved my problem with the last kernel in the new Ubuntu 8.04 modifying the file "menu.lst" (/boot/grub/menu.lst) using the UUID (instead of /dev/hd?? format):

**Before:**

title		Debian GNU/Linux, kernel 2.6.24-17-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
boot

**After:**

title		Debian GNU/Linux, kernel 2.6.24-17-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=9f7f358d-6948-44fd-9d36-f166c2566170 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
boot

If i put /dev/sdb1 it works also, maybe a bug in the new kernel??? (my harddrive is not scsi)

To know your uid you must see the fstab file (/etc/fstab). (You can change all the entries: recovery modes, old kernels, etc... )

Perhaps these changes might be useful for anyone with these problems...

Regards

---

### Post by bobnutfield on 2008-05-03
The new linux kernels all name the drives sd(x) instead of hd(x).  It doesn't matter if the drive is sata, scsi or ide.  

Bob

---

### Post by publicidadno on 2008-05-03
bobnutfield,

Ok, i dont know this!!!  :-#

thanks and regards

---


---
title: "Grub and changed partitions"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by gareththered on 2007-09-25
I recently changed the partitions on my PC by removing redundant partitions and having a general tidy up.
My Ubuntu root partition was within an extended partition and was /dev/sda6.  After my reorganisation it has changed to /dev/sda3 (I removed the extended partition for one).
I can get things to boot by reinstalling grub manually.
Every time there is a system update and a kernel is upgraded, the system attempts to place a menu entry for the new kernel in grub&#347; ´/boot/grub/menu.lst´ file, as it should.
Unfortunately, after a reboot I get an error stating that the image cannot be found. If I hit the é´ key to edit, I notice that my root is hd(0,5) i.e. the original /dev/sda6.  I can boot by changing this to hd(0,2) but it doesn´t matter how many times I change the menu.lst file and manually re-install grub, after an upgrade it reverts to hd(0,5) in menu.lst!
Anybody with any ideas where it gets this information from?

---

### Post by rsambuca on 2007-09-25
There is a line in the menu.lst that sets root.  If you post your menu.lst I can tell you what to change.  (I am on my XP box at the moment so I can't tell you the exact line).

---

### Post by gareththered on 2007-09-25
Just to save on screen space, I´ve removed all the comment (#) lines.  It´s the lines```
root            (hd0,5)
```that keep reverting after I change them to hd(0,2) and manually reinstall grub!
```
default		0

timeout		5

hiddenmenu

title		Ubuntu gutsy (development branch), kernel 2.6.22-12-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-12-386 root=UUID=6aee3c9c-f3ee-489c-84f3-20d411215e66 ro quiet splash
initrd		/boot/initrd.img-2.6.22-12-386
quiet

title		Ubuntu gutsy (development branch), kernel 2.6.22-12-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-12-386 root=UUID=6aee3c9c-f3ee-489c-84f3-20d411215e66 ro single
initrd		/boot/initrd.img-2.6.22-12-386

title		Ubuntu gutsy (development branch), kernel 2.6.22-11-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-11-generic root=UUID=6aee3c9c-f3ee-489c-84f3-20d411215e66 ro quiet splash
initrd		/boot/initrd.img-2.6.22-11-generic
quiet

title		Ubuntu gutsy (development branch), kernel 2.6.22-11-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-11-generic root=UUID=6aee3c9c-f3ee-489c-84f3-20d411215e66 ro single
initrd		/boot/initrd.img-2.6.22-11-generic

title		Ubuntu gutsy (development branch), kernel 2.6.22-10-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-10-generic root=UUID=6aee3c9c-f3ee-489c-84f3-20d411215e66 ro quiet splash
initrd		/boot/initrd.img-2.6.22-10-generic
quiet

title		Ubuntu gutsy (development branch), kernel 2.6.22-10-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-10-generic root=UUID=6aee3c9c-f3ee-489c-84f3-20d411215e66 ro single
initrd		/boot/initrd.img-2.6.22-10-generic

```
Thanks for your time.

---

### Post by rsambuca on 2007-09-25
Actually, it is in the top commented stuff.  That is the part we need to see.

EDIT:  I am not positive, but if my memory is correct it is groot something or other.

---

### Post by gareththered on 2007-09-25
Brilliant, I just had a look at the rest of the file, and found```
# groot=(hd0,5)
```I shall change that to hd(0,2) and will wait patiently for the next kernel update.
Many, many thanks for your help.

---


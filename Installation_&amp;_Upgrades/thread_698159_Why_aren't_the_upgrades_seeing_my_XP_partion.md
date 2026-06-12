---
title: "Why aren't the upgrades seeing my XP partion"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by McTek on 2008-02-16
Why do I have to manually edit Menu.lst each time I install an updates? PS: Why do I want to install KDE updates to my Gnome install?

---

### Post by hyperair on 2008-02-16
Miconfiguration of menu.lst. Why don't you post it here?

---

### Post by McTek on 2008-02-16
This is what menu.lst looks like after updates:
> ## default num
tem.
default		0

## timeout sec
timeout		10

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bac84bbd-6f9d-47de-9a77-f8f62ab6fefa ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bac84bbd-6f9d-47de-9a77-f8f62ab6fefa ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


This is what it looks like after I edit Menu.lst:
> ## default num
tem.
default		0

## timeout sec
timeout		10

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bac84bbd-6f9d-47de-9a77-f8f62ab6fefa ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bac84bbd-6f9d-47de-9a77-f8f62ab6fefa ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
 
Now XP will show in grub list.

---

### Post by ayampanggang on 2008-02-16
i dont know how it works, but is your winXP partition appear on the fstab? the updater might look it from there.

---

### Post by hyperair on 2008-02-16
Between the timeout line and your first GRUB entry, add a line containing just this:
```

### BEGIN AUTOMAGIC KERNELS LIST

```

Then run "sudo update-grub". If your Windows entry is still there, then the issue is fixed. Otherwise, post the new menu.lst and we'll see what we can do.

---

### Post by McTek on 2008-02-17
Ckeck fstabs and it is listed there.

---

### Post by McTek on 2008-02-17
Will have to wait for next update to test. thank you both

---


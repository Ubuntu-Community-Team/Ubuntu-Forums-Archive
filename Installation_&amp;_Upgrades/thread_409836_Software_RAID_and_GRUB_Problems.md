---
title: "Software RAID and GRUB Problems"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by Abecedaria on 2007-04-15
Hi,

I just set up a new Ubuntu 6.10 install on 2-20GB PATA drives in a software RAID. The partitions are as follows: 

md0 = /boot  (raid1) 100MB
md1 = /        (raid0) 40GB
md2 = swap   (raid0) 1GB

The install goes fine, but when I reboot, I end up at the grub prompt instead of automatically booting the kernel or offering a menu. 

```
grub>
```
If I manually specify the kernel, initrd, and root, it boots just fine. Here's what I use:
```
root (hd0,0)
initrd.img-2.6.17-10-generic
kernel /vmlinuz-2.6.17-10-generic ro root=/dev/md1
```

I looked at the menu.lst and it uses the same commands. 

Why isn't grub reading the menu.lst and automatically booting? Am I missing something obvious here? :confused: 

abc

---

### Post by Abecedaria on 2007-04-21
bump

---

### Post by nexus9k on 2007-04-23
Have you checked grub-install to make sure that stage1 is installed?  Is it possible that /dev/md1 is not ready yet?

---

### Post by Abecedaria on 2007-04-23
> **nexus9k said:**
> Have you checked grub-install to make sure that stage1 is installed?  Is it possible that /dev/md1 is not ready yet?

I checked /boot/grub and stage1 is installed. Here are the relevant portions of my menu.lst. Do you see anything wrong? Grub just doesn't seem to want to load it. 

```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.17-11-generic root=/dev/md1 ro quiet splash
initrd		/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.17-11-generic root=/dev/md1 ro single
initrd		/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-386 root=/dev/md1 ro quiet splash
initrd		/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-386 root=/dev/md1 ro single
initrd		/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/md1 ro quiet splash
initrd		/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/md1 ro single
initrd		/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST 
```

Any more ideas?

abc

---

### Post by nexus9k on 2007-04-24
> **Abecedaria said:**
> I checked /boot/grub and stage1 is installed. Here are the relevant portions of my menu.lst. Do you see anything wrong? Grub just doesn't seem to want to load it.

Have you tried running grub-install again against the physical disks?  

```

$ sudo grub-install /dev/sda

$ sudo grub
grub> device (hd0) /dev/sdb
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

```

The above is assuming that you are using sda and sdb for your mirror.

---

### Post by Abecedaria on 2007-04-24
> **nexus9k said:**
> Have you tried running grub-install again against the physical disks?  

```

$ sudo grub-install /dev/sda

$ sudo grub
grub> device (hd0) /dev/sdb
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

```

The above is assuming that you are using sda and sdb for your mirror.

You rock! :guitar:  That absolutely fixed it. I just don't know why I didn't think of trying that earlier. :-k

Thanks again for your help!

abc

---


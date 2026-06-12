---
title: "Uninstalling 2nd ubuntu partition?"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by JaggedOne on 2007-12-09
I have three partitons. One windows XP and two ubuntu. i want to uninstall the 2nd ubuntu partition (and its swap space, each ubuntu partition has its own swap space.) How Do I do this and keep grub happy? Something about fixmbr? What is that and how do I use it?

---

### Post by wjp.reg on 2007-12-09
> **JaggedOne said:**
> I have three partitons. One windows XP and two ubuntu. i want to uninstall the 2nd ubuntu partition (and its swap space, each ubuntu partition has its own swap space.) How Do I do this and keep grub happy? Something about fixmbr? What is that and how do I use it?

What is the second ubuntu partition for? was it a bootable partition?  if not, use gparted and first unmount it and then delete it.  Nothing to do with grub if it wasn't a bootable partition.

If it was, edit /boot/grub/menu.lst and remove the references to the second partition you no longer need.

---

### Post by JaggedOne on 2007-12-09
Thanks but I have no idea how to edit menu.lst... Im afraid I might break something. What exactly do i remove?

It was a bootable partition.

---

### Post by wjp.reg on 2007-12-09
> **JaggedOne said:**
> Thanks but I have no idea how to edit menu.lst... Im afraid I might break something. What exactly do i remove?

It was a bootable partition.


You can do that with:

```
gksu gedit /boot/grub/menu.lst
```

and then delete the sections for the second bootable partition.

It will read something like this:

> title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=25db8c66-74a6-4dab-ad2b-b96614fe9e3d ro quiet splash
initrd		/initrd.img-2.6.20-16-generic
quiet


title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=25db8c66-74a6-4dab-ad2b-b96614fe9e3d ro single
initrd		/initrd.img-2.6.20-16-generic



Just be sure you don't delete the partition that has the active ubuntu system running on it.

hd0,0 = first hard drive, first partition
hd0,1 = first hard drive, second partition
hd0,2 = first hard drive, thrid partition

and so on....

---

### Post by JaggedOne on 2007-12-09
Thanks. Also, how do I delete the swap? It is locked on gparted and I can not format it.

---

### Post by wjp.reg on 2007-12-09
> **JaggedOne said:**
> Thanks. Also, how do I delete the swap? It is locked on gparted and I can not format it.

was the swap shared between the two ubuntus, if so you can't remove it.  Otherwise, unmount the swap to be removed by selecting unmount from the gparted | Partition menu and then delete it.

---

### Post by JaggedOne on 2007-12-09
Doh, major screw up here. I formated the ubuntu install before I edited grub. Now whenever I boot It hangs up on grub and gives me an "error 22".

All I can do is boot from the live disk now. And as far as I can tell I can't edit grub files from a live cd. Help!

---

### Post by wjp.reg on 2007-12-09
are we having fun yet?? :lolflag:

[Here are instructions for restoring grub using the live CD]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-09167948173503db5923da717a106f0c3aac1cd2")

See the section titled:>  Using the Desktop/LiveCD while preserving Windows Bootloader

---


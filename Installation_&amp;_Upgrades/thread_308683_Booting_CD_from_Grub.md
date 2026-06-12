---
title: "Booting CD from Grub?"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by mikeapple on 2006-11-28
I have an old laptop that has a locked bios (long story) so i cant change the boot order.

I currently have xubuntu installed and grub installed in the MBR

Is it possible to launch a setup CD(windows 2k) by adding something to my menu.lst? 
or
If i copy the windows boot disk to a partition. Would adding an entry into my menu.lst pointing at that work?

Thanks in advance

---

### Post by sebbe1991 on 2006-11-28
[http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB](http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB)
the fast method should work on ubuntu

---

### Post by mikeapple on 2006-11-29
Thanks I will give that a go :)

---

### Post by sebbe1991 on 2006-11-29
Here is a how to do it in Ubuntu

First find the Terminal

Get the needed files
```

wget ftp://ftp.mcc.ac.uk/beta/local/teaching_cluster/disks/memdisk
wget ftp://ftp.mcc.ac.uk/beta/local/teaching_cluster/disks/sbm.bin

```

Create GRUB Entry
```

sudo cp memdisk sbm.bin /boot
sudo gedit /boot/grub/menu.lst

```

at the end of menu.lst add
```

title=SBM-Boot a CD
kernel /boot/memdisk
initrd /boot/sbm.bin

```

---

### Post by mikeapple on 2006-11-30
worked a treat.

Many thanks for your help

Mike.

---


---
title: "Booting from windows recovery partition"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by jpaulb on 2010-09-21
I installed Ubuntu on a old laptop running windows 2000


After the installation the boot loader GRUB II does not give me the option to use the Windows 2000 recovery option. This would be necessary since I to not have a recovery disk. Is there any info about how to include the Windows recovery operation in the boot menu?

Originally F11 brought up a menu with the option to recover W 2000.

---

### Post by Mark Phelps on 2010-09-22
GRUB2 finds other operating systems by scanning for certain files in their partitions.  That's why, when folks have the OEM-default Win7 setup, in which the boot loader files are in one partition and the Windows OS files are in a second partition, it typically creates two menu entries for Win7.

If there are no actual Windows OS files in your Recovery partition (and there might not be if it's a compressed Windows Image file), then GRUB2 sees nothing there and builds no entry.

Besides, all that GRUB2 does in the case of MS Windows is hand over control to an MS Windows boot loader -- and since there is apparently no such animal in your Recovery partition, even if you DID add an entry, it would not do anything.

---

### Post by psusi on 2010-09-22
Are you sure you still have the recovery partition, and if so, which one is it?  What does sudo fdisk -l show?

---

### Post by jpaulb on 2010-09-23
> **psusi said:**
> Are you sure you still have the recovery partition, and if so, which one is it?  What does sudo fdisk -l show?


[LIST]
[*]Dev                  start           end             blocks  ID      System
[*]/dev/sda1            1               637             5116671 c       W95 FAT32 (LBA)
[*]/dev/sda2     2313      2432      960120         c      W95 FAT32 (LBA)
[*]/dev/sda7     1863      2312      3614593        7      HPFS/NTFS
[/LIST]

/dev/sda2 is the recovery partition
/dev/sda7 is the partition I would like to share data on.

---

### Post by psusi on 2010-09-23
I don't see a Linux partition.  Do you have a wubi install or something?  If you want to boot the recovery partition, hold down shift to make the grub menu come up at boot time ( if it doesn't already ) and hit c to get to the console.  Enter the following:

set root=(hd0,2)
chainloader +1

Beware though; the windows recovery will wipe out your Ubuntu install.

---

### Post by jpaulb on 2010-09-25
> **psusi said:**
> I don't see a Linux partition.  Do you have a wubi install or something?  If you want to boot the recovery partition, hold down shift to make the grub menu come up at boot time ( if it doesn't already ) and hit c to get to the console.  Enter the following:

set root=(hd0,2)
chainloader +1

Beware though; the windows recovery will wipe out your Ubuntu install.
Thanks for your help

I tried your suggestion without success and had a brain storm, something like a seizure:P

Why not copy the code in grub.cfg for the Windows boot and change what is necessary to boot the recovery partition. It worked.
May not be the most elegant solution 

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows 2000 Professional recover(on /dev/sda2)" {
	insmod fat
	set root='(hd0,2)'
	
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```

---


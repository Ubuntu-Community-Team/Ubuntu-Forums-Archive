---
title: "Partition sector doesn't have the endmark 0xAA55"
date: 2013-01-29
forum: Installation &amp; Upgrades
---

### Post by sangeetha821 on 2013-01-29
In gparted disk is showing unallocated.
in testdisk Partition sector doesn't have the endmark 0xAA55 and my partition is correct in drive
and  bootinfoscript result overlaps in partition

---

### Post by oldfred on 2013-01-30
Bootscript is not really showing any MBR at all. MBR is boot code & partition table and it looks like random data which bootscript is trying to report as a partition table.

If test disk can restore a partition table that would be a good choice, but you will still have to reinstall a boot loader.

---

### Post by sangeetha821 on 2013-01-31
how to re-install boot loader.

---

### Post by oldfred on 2013-01-31
You need to restore a valid  partition table first and have Ubuntu installed so it can find the rest of grub. 
If just Windows it only looks at partition table for boot flag, but again you have to have valid partition table first.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

    
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by sangeetha821 on 2013-02-01
i got my linux back.. i restore my linux partition and re-install grub. after reboot everthing k. thanks a lot...

---


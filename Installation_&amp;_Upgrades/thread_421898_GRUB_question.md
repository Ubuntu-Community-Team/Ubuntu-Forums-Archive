---
title: "GRUB question"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by icechen1 on 2007-04-24
Hello,
I have windows XP,Ubuntu,Opensuse installed on the computer.
Is there any way to remove openSUSE (I like Ubuntu) and change the boot loader to the Ubuntu's?Also, the Grub is installed in the openSUSE partition by its installer and each time i boot,it go to the opensuse grub menu.

---

### Post by tyler_roach on 2007-04-24
You can use the gparted live CD to remove the suse partition, and there is a 'super grub disk" (Google it) you can use to restore or install grub on your ubuntu partition.

---

### Post by icechen1 on 2007-04-24
> **tyler_roach said:**
> You can use the gparted live CD to remove the suse partition, and there is a 'super grub disk" (Google it) you can use to restore or install grub on your ubuntu partition.

thanks,i will try that

---

### Post by tarpon_bill on 2007-04-24
It's much easier to just install the new over the old. If you know how make note of the partition scheme and reuse the SUSE partitions when installing. Or just run the Ubuntu installer and when you get to the partition selection, choose manual partitioning and pick the partitions then. Install in the same SUSE partitions, or delete the SUSE partitions and use the freed space to put in new partitions and continue on.

It's all on the install disk.

---

### Post by icechen1 on 2007-04-24
> **tarpon_bill said:**
> It's much easier to just install the new over the old. If you know how make note of the partition scheme and reuse the SUSE partitions when installing. Or just run the Ubuntu installer and when you get to the partition selection, choose manual partitioning and pick the partitions then. Install in the same SUSE partitions, or delete the SUSE partitions and use the freed space to put in new partitions and continue on.

It's all on the install disk.

yes but i already have ubuntu,i don't want to have 2 ubuntu or to reinstall

---


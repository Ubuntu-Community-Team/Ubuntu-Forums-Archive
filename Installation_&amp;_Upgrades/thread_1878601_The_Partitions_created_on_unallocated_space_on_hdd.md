---
title: "The Partitions created on unallocated space on hdd"
date: 2011-11-10
forum: Installation &amp; Upgrades
---

### Post by lse123 on 2011-11-10
In hdd
The Partitions created on unallocated space on hdd? this means I must create unallocated space to install ubuntu 10.04 LTS?

In a usb stick
may exist two partitions? may each with ubuntu 11.10 one and ubuntu 10.04 LTS the other? what to do to can choose between what to boot from?

---

### Post by darkod on 2011-11-10
HDD
Yes, you need unallocated space on the HDD and that is where the partitions will be created (either by using one of the auto options, or you can do it manually).

USB stick/hdd
Yes, you can have two or even more installs of ubuntu. There is nothing special to do, except make sure you install the bootloader grub2 to the MBR of the usb stick, not to your internal hdd. The grub2 on the usb stick will be from the second install of ubuntu, it will overwrite the grub2 from the first installation but that doesn't matter because any grub2 will be able to boot both 10.04 and 11.10.

---

### Post by Gatemaze on 2011-11-10
> **lse123 said:**
> In hdd
The Partitions created on unallocated space on hdd? this means I must create unallocated space to install ubuntu 10.04 LTS?

Not necessarily, you can always format and ovewrite another partition LOSING what is already in this partition. I repeat LOSING what is already in this partition.

> **lse123 said:**
> 
In a usb stick
may exist two partitions? may each with ubuntu 11.10 one and ubuntu 10.04 LTS the other? what to do to can choose between what to boot from?
yes you could with different partitions. grub on usb pen i would imagine...

---


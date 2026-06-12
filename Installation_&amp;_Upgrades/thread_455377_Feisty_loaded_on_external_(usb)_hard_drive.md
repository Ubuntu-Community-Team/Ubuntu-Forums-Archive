---
title: "Feisty loaded on external (usb) hard drive"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by noobie123 on 2007-05-26
I just installed feisty on usb hdd by following[ leobaby's directions listed here]("http://ubuntuforums.org/showpost.php?p=2132418&postcount=481") 

1. Created some free space on the hdd by deleting one of the partitions
2. Booted from "*alternate install*" ubuntu disc 
3. Choose manual partitioning during install and let Ubuntu create default partitions on the free space. It created 1 ext3 and 1 swap partition
4. Installed all the packages
5. Choose to **install Grub on external usb hdd** rather than master boot drive. (**VERY IMPORTANT**)
6. Then I edited the menu.lst in /boot/grub folder to read following> 
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=37b02941-7729-4812-8417-d335fc9aa0ea ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=37b02941-7729-4812-8417-d335fc9aa0ea ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

7.  Booted from USB drive into ubuntu :) 

Hope it helps.

---

### Post by macogw on 2007-05-26
> **noobie123 said:**
> I just installed feisty on usb hdd by following[ leobaby's directions listed here]("http://ubuntuforums.org/showpost.php?p=2132418&postcount=481") 

1. Created some free space on the hdd by deleting one of the partitions
2. Booted from "*alternate install*" ubuntu disc 
3. Choose manual partitioning during install and let Ubuntu create default partitions on the free space. It created 1 ext3 and 1 swap partition
4. Installed all the packages
5. Choose to **install Grub on external usb hdd** rather than master boot drive. (**VERY IMPORTANT**)
6. Then I edited the menu.lst in /boot/grub folder to read following
7.  Booted from USB drive into ubuntu :) 

Hope it helps.

Or just take out the internal drive first.

---

### Post by Cows on 2007-05-26
Why would you want to take out the internal drive.. the external drive is made to be d/c and reconnected..

---


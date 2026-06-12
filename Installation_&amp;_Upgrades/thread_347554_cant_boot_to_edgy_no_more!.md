---
title: "cant boot to edgy no more!"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by roar on 2007-01-27
can I recover my Edgy installation ? heres what happened:
I had xp and Edgy dual-booting and it was all good. Because I had 20 GB free space on my laptop I decided to install Dapper too. I got the dvd, burned it, and started installing. Since it didnt seem possible to edit partition table manually, I choose to let installer install on free space. The install went fine, but when I restart I dont see Edgy at all. I now can boot to xp and Dapper. 

This is from Dapper, here is sudo fdisk -l:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1274    10233373+   7  HPFS/NTFS
/dev/sda2            1275        1402     1028160   83  Linux
/dev/sda3            1403        6516    41078205    f  W95 Ext'd (LBA)
/dev/sda4            6517        9729    25808422+  83  Linux
/dev/sda5            3698        6247    20482843+   b  W95 FAT32
/dev/sda6            1403        2422     8193087   83  Linux
/dev/sda7            2423        3697    10241406   83  Linux
/dev/sda8            6248        6375     1028128+  82  Linux swap / Solaris
/dev/sda9            6376        6516     1132551   82  Linux swap / Solaris

Partition table entries are not in disk order

I think sda1 is xp, sda2 is boot partition, 3 extended, 4 is dapper, 5 is another windows partition (storage type fat), 6 and 7 is / and /home on Edgy, not sure which. 8 and 9 is swap for Edgy and Dapper

this is /boot/grub/menu.lst that I see when in dapper

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda4 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda4 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda4 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda4 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,3)
kernel          /boot/memtest86+.bin
boot


title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


Can I edit this file somehow so that grub will let me choose to also boot to Edgy?

---

### Post by Dr. Nick on 2007-01-27
Yes, it looks like you could edit menu.lst to get back into edgy. I couldnt figure out which is the / on edgy, either 6 or 7 like you mentioned, I would think 6 though. I would have thought dappers install of grub would have added edgy though.

Grub starts counting at 0 while sda starts at 1 thus everything in menu.list is 1 number off. 

an entry like this may work 



```
 title           Ubuntu, kernel 2.6.15-27-386
 root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda6 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot
```

The only thing you will have to figure out is what kernel version you need to put in.

Another thing you could try is mounting the sda6 or sda7 partitions and look at the menu.list from the edgy partition and copy a few parts of it over

---

### Post by roar on 2007-01-27
Yes! I already had tried your first suggestion, but that didn`t work. Then I mounted sda2, because i created a separate partition for boot when I installed edgy, so boot was on sda2 and / on sda6, as you assumed. The menu.lst from the edgy install was rather strange looking though:

title           Ubuntu, kernel 2.6.17-10-386
root            (hd0,1)
kernel          /vmlinuz-2.6.17-10-386 root=UUID=1ced8b3f-1906-465f-8e42-7692a6601a02 ro quiet splash
initrd          /initrd.img-2.6.17-10-386
savedefault
boot

Anyways, after I put this into menu.lst I am able to boot to edgy also, thanks doc.

---


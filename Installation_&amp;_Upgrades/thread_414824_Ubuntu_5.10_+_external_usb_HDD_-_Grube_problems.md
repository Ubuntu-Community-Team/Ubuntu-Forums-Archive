---
title: "Ubuntu 5.10 + external usb HDD - Grube problems?"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by ninocass on 2007-04-20
Hi all

I need to run ubuntu 5.10 and dont want to install it on my lappytop so im using an external HDD.

The HDD is a laptop harddrive in a caddy connected via USB.

I changed the current HDD to the HDD that is in the caddy and proceded with a clean install of ubuntu (1 EXt3 partition, 1 Fat32 partition) which loaded up nicely.

I then swapped my HDDs back around and put the ubuntu 5.10 one back in the caddy.

I know 100% that my laptop allows booting from USB as i use a DSL install on my pen drive.

When i boot i get a brief glimpse of the grub that on the 5.10 HDD and then it changed to the GRUB loaded thats on my main HDD.

im asuming that theres something wrong with my GRUB.

I set up my grub by using the GRUB install method:
```

grub> root (hd
 Possible disks are:  hd0 hd1

grub> root (hd1,
 Possible partitions are:
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type is fat, partition type 0xb

grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

```

---

### Post by slimdog360 on 2007-04-20
have you tried setting your bios to boot from usb before the hdd?

---

### Post by ninocass on 2007-04-20
Yep as i mentioned i boot from USB from my pendrive so i know that the order is okay :)

i think the grub is at fault

---


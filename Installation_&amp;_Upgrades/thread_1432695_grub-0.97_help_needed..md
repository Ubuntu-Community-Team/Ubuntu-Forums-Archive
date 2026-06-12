---
title: "grub-0.97 help needed."
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by ramaswamyps on 2010-03-18
i removed the original grub2 and installed grub-0.97  [0.97-29ubuntu59]
grub-install /dev/sdb8 installed it in root partition.
i get grub prompt at boot time.
how do i make a menu.lst/grub.cfg ?
> tux ~ # dir /mnt/sdb8/boot/grub/        
default        fat_stage1_5	  jfs_stage1_5	     stage1
device.map     grubenv		  minix_stage1_5     stage2
e2fs_stage1_5  installed-version  reiserfs_stage1_5  xfs_stage1_5

what are boot lines to use?
> tux ~ # dir /mnt/sdb8/boot/     
System.map-2.6.31-14-generic  initrd.img-2.6.31-14-generic
System.map-2.6.31-18-generic  initrd.img-2.6.31-18-generic
System.map-2.6.31-19-generic  initrd.img-2.6.31-19-generic
System.map-2.6.31-20-generic  initrd.img-2.6.31-20-generic
abi-2.6.31-14-generic	      memtest86+.bin
abi-2.6.31-18-generic	      vmcoreinfo-2.6.31-14-generic
abi-2.6.31-19-generic	      vmcoreinfo-2.6.31-18-generic
abi-2.6.31-20-generic	      vmcoreinfo-2.6.31-19-generic
config-2.6.31-14-generic      vmcoreinfo-2.6.31-20-generic
config-2.6.31-18-generic      vmlinuz-2.6.31-14-generic
config-2.6.31-19-generic      vmlinuz-2.6.31-18-generic
config-2.6.31-20-generic      vmlinuz-2.6.31-19-generic
grub			      vmlinuz-2.6.31-20-generic
tux ~ # 
i want to boot only ubuntu in the manu.lst
any help welcome :)

---

### Post by lidex on 2010-03-18
Scroll down to this section: "Uninstalling GRUB 2 / Reverting to GRUB Legacy" on this page:
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by ramaswamyps on 2010-03-18
thanks :)
it is resolved now.
run update-grub to make new menu.lst after installing grub-0.97
this may help someone.

---


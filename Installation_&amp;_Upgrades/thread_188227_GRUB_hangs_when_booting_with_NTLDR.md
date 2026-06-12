---
title: "GRUB hangs when booting with NTLDR"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by madmike562 on 2006-06-03
I have been triple booting Windows 98,Windows xp,and Ubuntu 5.10 with W98 and xp on hda and Ubuntu on hdb for about 6 mo.GRUB is installed in /boot on hdb1  and NTLDR/boot.ini loads a copy of the hdb bootsector (bootsect.lnx) on hda.

I have had intermittant problems with GRUB hanging at the GRUB_  prompt but up until now I was able to hit reset and it would boot normally.Now all I get is the prompt.I installed service pack 2 on Windows xp just before grub stopped working, not sure if it's related or not ( but with MS it's possible).

I was able to create a GRUB boot floppy ([https://wiki.ubuntu.com/GrubHowto/BootFloppy]("https://wiki.ubuntu.com/GrubHowto/BootFloppy")  ) using live cd and boot the system.I have  reinstalled GRUB to hdb /boot using grub>root (hd1,0) grub>setup (hd1) and recopied the bootsector to hda with no success.I was thinking that possibly the /boot/grub/stage1,stage2, or menu.lst files had become corrupt but I was able to copy the files to make the working boot disk.Does anyone have suggestions on what else to check?

At this point I'm considering reinstalling Ubuntu but would rather just fix this.
                              Thanx in advance, Mike

---

### Post by linuchsan on 2006-06-03
mbr on a slave drive??? see grub>setup (hd1)

---

### Post by madmike562 on 2006-06-04
I believe grub>setup (hd1,0) should install grub to the second physical drive (hd1) 
and the the first partition (,0).Here are the results of fdisk -l for clarity.I have noted which os is where.

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    c  W95 FAT32 (LBA)    --Windows98
/dev/hda2            1276        7475    49801500    f  W95 Ext'd (LBA)   
/dev/hda5            1276        2550    10241406    b  W95 FAT32            --FAT32files
/dev/hda6            2551        4973    19462716    7  HPFS/NTFS           --Windowsxp
/dev/hda7            4974        7475    20097283+   7  HPFS/NTFS         --NTFSfiles

Disk /dev/hdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          31      248976   83  Linux                          --/boot
/dev/hdb2              32        4982    39768907+   f  W95 Ext'd (LBA)
/dev/hdb3            4983        4983           0    e  W95 FAT16 (LBA)
/dev/hdb5              32        4982    39768876   8e  Linux LVM              --Ubuntu

hda1 contains the Windows xp bootloader files, Windows98 install, and copy of hdb1 bootsector (dd if=/dev/hdb1 of=/bootsect.lnx bs=512 count=1).hda6 is Windowsxp install.Ubuntu is on hdb5.

What I can't understand is why I can boot successfully from a floppy made with copies of the files on /boot  (/boot/grub/stage1,stage2,menu.lst) but not from harddrive.The windows bootloader seems to be finding the bootsector copy and it starts to run grub (GRUB _) then hangs.](*,)

---


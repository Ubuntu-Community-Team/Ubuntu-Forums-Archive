---
title: "cannot find ubuntu in boot menu after installation"
date: 2018-04-14
forum: Installation &amp; Upgrades
---

### Post by ptzheng on 2018-04-14
Hello community:D
I haved installed Ubuntu 16.04 desktop version for my school's server by USB devices. During installation, I selected the first option: erase the disk and install ubuntu, because i just need one system. But after installtion and restarting the server, i could not find ubuntu in the boot menu, i haved no way to enter the ubuntu system i installed. I have tired to use boot-repair, but it didn't work. In addition, one strange thing is that the system in live CD(USB) could not connect to network.
I have got stuck in this problem for a long time. Could anyone give me some advice? Thanks.[ATTACH=CONFIG]279292[/ATTACH][ATTACH=CONFIG]279293[/ATTACH][ATTACH=CONFIG]279294[/ATTACH]

---

### Post by dino99 on 2018-04-14
/dev/sda1 is a FAT partition, and the boot screenshot is the windows one: so you have not formated your hdd. Maybe the partition is an hidden one, some brand do but i does not know what Dell do.
Linux system need EXT4 format partition, not FAT.

[https://www.wikihow.com/Install-Ubuntu-Linux](https://www.wikihow.com/Install-Ubuntu-Linux)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[https://www.omgubuntu.co.uk/2016/04/10-things-to-do-after-installing-ubuntu-16-04-lts](https://www.omgubuntu.co.uk/2016/04/10-things-to-do-after-installing-ubuntu-16-04-lts)

---

### Post by yancek on 2018-04-14
Your screenshots show a FAT32 500MB partition which is probably an EFI  partition then you have the Linux extr4 partition and swap.  Not enough  info so since you already have the boot repair script, run it again and  instead of trying to repair, select the option to Create BootInfo  summary and post a link to the output here.  That will give us some  useful information and someone should be able to help.

---

### Post by ptzheng on 2018-04-15
> **yancek said:**
> Your screenshots show a FAT32 500MB partition which is probably an EFI  partition then you have the Linux extr4 partition and swap.  Not enough  info so since you already have the boot repair script, run it again and  instead of trying to repair, select the option to Create BootInfo  summary and post a link to the output here.  That will give us some  useful information and someone should be able to help. 

Thanks for your advice and here is my bootinfo summary(sdb is my USB device):
```
============================= Boot Info Summary: ===============================


 => Grub2 (v1.99-2.00) is installed in the MBR of /dev/sda and looks at sector 
    2048 of the same hard drive for core.img, but core.img can not be found at 
    this location.
 => No known boot loader is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/grub.cfg /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi


sda2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.5 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sda3: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb4: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 6.02 2013-10-13... :..(:,:0:4:8:....D:H:L:[.T:[.\:`:d:[.l:p:t:x:|:.:.:.:.:.:.:.:...........
    Boot sector info:  Syslinux looks at sector 1456080 of /dev/sdb4 for its 
                       second stage. SYSLINUX is installed in the /isolinux 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi
```

---

### Post by oldfred on 2018-04-15
Please use code tags if posting longer text or terminal output.
You can easily add code tags with Forum's advanced editor and # icon.

Generally the Summary Report is too large to directly post anyway. Better to just post link it gives.

But what you have posted shows grub in MBR for BIOS boot and in UEFI for UEFI boot?
Which do you want, and then boot Live installed in that boot mode and run Boot-Repair to totally reinstall grub.
If you want BIOS boot, you must first have a bios_grub partition for grub to install. You have ESP - efi system partition for UEFI boot.

---


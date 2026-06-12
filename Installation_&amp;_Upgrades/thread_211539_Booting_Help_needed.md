---
title: "Booting Help needed"
date: 2006-07-08
forum: Installation &amp; Upgrades
---

### Post by anup09 on 2006-07-08
Ok hey.. i had it where is was dual boot Ubuntu and XP Pro Sp2
since XP SP2 messed up i reformated it and now it ask;s me only to boot into XP .. when i run partition Magic.. i see that Ubuntu is still on a patition and i can view the files via file manager on Partition Magic 8.. how do i get GRUB boot loader back installed.

---

### Post by cotcot on 2006-07-08
Load the liveCD. Then in terminal : 
```
sudo su
root (hd0,2)
setup (hd0,0)
```

You have to adapt (hd0,2) according to your partitions. I gave you the example where ubuntu was installed all on 1 partition hda3. hda3 is for grub (hd0,2). It is important that the partition after "root" contains /boot. You can check your partition table with ```
sudo fdisk -l
```
Setup (hd0,0) will install the boot loader in your MBR. If you have a floppy drive you can also install the bootloader on a floppy by using setup (fd0). Floppy in will give you than a boot menu of grub; floppy out will boot windows. It is safer to try this first. 
If you do setup (hd0,0) and it fails do not try it a second time before restoring the previous bootloader with fix MBR.

---


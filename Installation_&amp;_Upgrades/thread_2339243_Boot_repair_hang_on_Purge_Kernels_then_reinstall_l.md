---
title: "Boot repair hang on Purge Kernels then reinstall last kernal sda2 (ins)."
date: 2016-10-06
forum: Installation &amp; Upgrades
---

### Post by zeroday2 on 2016-10-06
Hello,

I am new for ubuntu and after a fresh install of a package, the computer was not able to boot.

I installed ubuntu beside the existing linux system,
 After, I see the I can mount my partition sda2 (where my old system is)...

then I want to repair my old system so I used boot repair but it hange on Purge Kernels then reinstall last kernal sda2 (ins

I created a BootInfo summary below : 

[http://paste.ubuntu.com/23284253/](http://paste.ubuntu.com/23284253/)

Following some solution on the internet I tried this, in the bootrepair I open the terminal and I tried the following command 

[HTML]lubuntu@lubuntu:~$ sudo grub-install /dev/sda
sda   sda1  sda2  sda3  
lubuntu@lubuntu:~$ sudo grub-install /dev/sda
sda   sda1  sda2  sda3  
lubuntu@lubuntu:~$ sudo grub-install /dev/sda
Installing for i386-pc platform.
[/HTML]


I am tired of trying to repair the sytem for the last 4 days and I have a lot of labs to finish for the last week.
So I would like to  if someone could help to solve this problem ?
 and if there is no solution I would like to know if it's posisble to backup my system sda2,
so I could install linux sys 16.04.01 again and restore it ?

Thank you so much, I would be gratful for your help. :)

zeroday

---

### Post by oldfred on 2016-10-06
This may be only problem:
      ```
 Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,050,623     1,048,576 EFI System partition
/dev/sda2       1,050,624   403,252,372   402,201,749 EFI System partition 


```    

You can only have one ESP - EFI system partition per device.
So use gparted to remove boot flag from sda1. Make sure sda1 is FAT32 formatted, it looks like it is.
Or use gdisk can change  code on sda2 from ef00 to 8300 - Linux data.
       [http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

You also show grub installed in BIOS boot mode in gpt's protective MBR. Do not boot in BIOS/Legacy/CSM boot mode, just UEFI. That grub it there then will not matter.

You may have to reinstall grub. But use Boot-Repair's advanced mode and reinstall grub-efi-amd64 which is the UEFI version of grub.

---


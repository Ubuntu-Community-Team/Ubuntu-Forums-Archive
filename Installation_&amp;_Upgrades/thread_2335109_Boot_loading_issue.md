---
title: "Boot loading issue"
date: 2016-08-25
forum: Installation &amp; Upgrades
---

### Post by andreaschr on 2016-08-25
Hi,

I have installed Windows 10 first and then install Ubuntu. On boot I only see the ubuntu loading screen and I cannot choose which operating system to boot either windows / ubuntu. So I have download boot-repair and i have reached a screen which says  GRUB install devices, which one should I choose. Below is the list of options. Thanks

 GRUB install devices:                            
             &#9474;                                                 
             &#9474;    [ ] /dev/sda (750156 MB; SAMSUNG_HD753LJ)       --> Windows 10
             &#9474;    [ ] /dev/sdb (500107 MB; TOSHIBA_DT01ACA050)  --> Ubuntu
             &#9474;    [ ] - /dev/sdb1 (495862 MB; /)                
             &#9474;    [ ] /dev/sdc (4027 MB; Flash_Disk)

---

### Post by oldfred on 2016-08-25
Either sda or sdb.
If BIOS use only sdb, so it will leave the Windows boot loader in sda.

If UEFI it does not matter what you say, it will install grub into the ESP on sda and both Windows & Ubuntu will have boot files in that partition.

Never install to a partition like sdb1.

---


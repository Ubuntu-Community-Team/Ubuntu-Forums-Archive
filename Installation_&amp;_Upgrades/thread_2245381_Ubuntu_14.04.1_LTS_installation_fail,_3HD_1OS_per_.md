---
title: "Ubuntu 14.04.1 LTS installation fail, 3*HD 1*OS per drive"
date: 2014-09-23
forum: Installation &amp; Upgrades
---

### Post by Andrew_Dennison on 2014-09-23
Hi I have a system with 3 hard drives, each with a three separate Ubuntu OS installed...

drive 1 (sda) is Ubuntu 13.04
drive 2 (sdb) is Ubuntu 12.04.3 LTS
drive 3 (sdc) was Ubuntu 12.10

My problem is I have tried to do a clean installation of Ubuntu 14.04.1 LTS from a Live-USB by erasing (sdc) Ubuntu 12.10. When it completes I restart the machine and I press F9 to choose drive to boot from, I select (sdc) drive 3 and all I get is a black screen and a blinking cursor line. The other 2 drives still boot fine. I have tried reinstalling again from USB and in the something else option I get this information...

/dev/sda
/dev/sda1     ext4     Ubuntu 13.04
/dev/sda5     swap    

/dev/sdb    
/dev/sdb1     ext4     Ubuntu 12.04.3 LTS
/dev/sdb5     swap

/dev/sdc
free space     1mb
/dev/sdc1     efi     536mb     33mb (used) 
/dev/sdc2     ext4     Ubuntu 14.04.1 LTS
/dev/sdc3     swap
free space     0mb

I am still relatively new to Ubuntu, but I have followed this same installation processes for a machine with dual boot windows and Ubuntu (same drive) and another with dual boot two versions of Ubuntu (Linux cnc and 14.04 LTS) each on separate drives with no problem. In truth I don't know what the problem is here to fix. Any advise would be greatly appreciated???

---

### Post by grahammechanical on 2014-09-23
The installer defaults to installing the Grub bootloader into sda. There is a panel with a drop-down menu that will let us change the location for the installation of Grub. My suggestion would be to boot to sda. You should get a grub boot menu with Ubuntu 14.04.1 on it. Load 14.04.1 and open a terminal and run

```
sudo update-grub
sudo grub-install /dev/sdc
```

Now when you boot sdc you should get a boot menu with the three versions of Ubuntu. When we have more than one hard drive and we want to change what drive boots then we need Grub installed into the MBR/EFI of each hard disk from the version of Ubuntu on that hard disk.

Regards.

---

### Post by oldfred on 2014-09-23
In addition to grahammechanical's comments, is this a newer system with UEFI (and BIOS)?

If you have an efi partition that would indicate an UEFI install. New systems with UEFI can boot in either UEFI or BIOS mode and how you boot installer is how it installs.
Then in UEFI/BIOS you have to turn on UEFI to boot an UEFI install or turn off UEFI or turn on CSM/BIOS/Legacy boot mode to boot in BIOS mode.

With multiple drives and installs best to see all the details, if just for your info on what is exactly where.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---


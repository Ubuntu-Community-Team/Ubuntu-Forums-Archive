---
title: "Boot issue..."
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by R2-Duck2 on 2010-06-23
Situation: 
 
Windows XP does not boot when selected from the GRUB menu.
No XP install disk available.
PC boots to Ubuntu (Grub2) without problem.
 
sudo fdisk -l shows:
Device Boot Start End Blocks Id System
/dev/sda1 * 1 6100 48996048+ 7 HPFS/NTFS
/dev/sda2 17973 19457 11928262+ 1c Hidden W95 FAT32 (LBA)
/dev/sda3 6100 17972 95363073 5 Extended
/dev/sda5 6100 17602 92386304 83 Linux
/dev/sda6 17602 17972 2975744 82 Linux swap / Solaris 
 
If there is no Windows install disk, it is my understanding an Ubuntu Live CD can be used (or booting from Ubuntu?) and the following commands can be entered from a Terminal:
 
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```
 
The above should reboot the machine into Windows XP, with no GRUB, so Ubuntu would not show. Would presume Ubuntu is still in /dev/sda5?
 
Would booting from an Ubuntu Live CD, and manually installing GRUB with the following command work to get GRUB installed and for the pc to be able to boot from either XP or Ubuntu:
 
```
grub-install /dev/sda
```
 
If this is not the route to go, is there a way to accomplish this? Any suggestions?
 
Thanks for your help. ;)

---

### Post by oldfred on 2010-06-23
per meierfra. mbr.bin may cause problems in some cases better to use lilo
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

But if grub does not let you boot putting a windows boot loader back in may not work either. Both grub and the MBR jump to the windows boot sector to continue booting.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by R2-Duck2 on 2010-06-24
Thanks for the reply, oldfred. ):P
 
The computer is not available to obtain information from it (Boot Info Script).
 
However, for future reference, was wondering, **if** lilo gets XP to boot, would Ubuntu also continue to boot as it has?
 
In essence, will lilo erase grub?

---

### Post by oldfred on 2010-06-24
Yes, lilo would replace grub and only boot the windows partition with the boot flag. Windows has additional boot info in the PBR or partition boot sector which is the area before each partition.

If your windows is not working you may need to repair it. Grub only will boot working windows. Many repairs of XP can be done from linux repair tools, Ubuntu or other repair CDs. Windows also has repair tools on its install CD.

If you are having boot issues this will often provide the info required to identify them.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by R2-Duck2 on 2010-06-24
Thanks, oldfred!! Appreciate the info, and will keep it for future use/reference.
 
Have a great weekend!!

---


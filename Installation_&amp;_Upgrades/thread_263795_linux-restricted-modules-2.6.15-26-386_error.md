---
title: "linux-restricted-modules-2.6.15-26-386 error"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by jetboy on 2006-09-23
whenever i try to update/install or upgrade anything, I get this error:  I am pretty new at this, but have tried several of the fixes mentioned above in the sticky post, and nothing seems to help:  

thanks!

this is an example:





:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  amarok amarok-xine
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-restricted-modules-2.6.15-26-386 (2.6.15.11-4) ...
ld_static: fcdsl/fcdsl-lib.o: bad reloc symbol index (0x60d150 >= 0xd63) for offset 0x27c7b in section `.text'
fcdsl/fcdsl-lib.o: could not read symbols: Bad value
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 712008746 >= 38982 for section `.strtab'
ld_static: fcdslusb2/fcdslusb2-lib.o: invalid string offset 843270432 >= 38982 for section `.strtab'
ld_static: nvidia_legacy/nv-kernel.o: bad reloc symbol index (0x87d8b >= 0x24bf) for offset 0x2ca08 in section `.data'
nvidia_legacy/nv-kernel.o: could not read symbols: Bad value
WARNING: Module /lib/modules/2.6.15-26-386/kernel/drivers/media/video/vpx3220.ko is not an elf object
WARNING: Module /lib/modules/2.6.15-26-386/kernel/sound/i2c/snd-i2c.ko is not an elf object
/sbin/lrm-manager: line 85:  7141 Segmentation fault      depmod -a -q -F /boot/System.map-"$KVER" "$KVER"
dpkg: error processing linux-restricted-modules-2.6.15-26-386 (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 linux-restricted-modules-2.6.15-26-386
E: Sub-process /usr/bin/dpkg returned an error code (1)

---


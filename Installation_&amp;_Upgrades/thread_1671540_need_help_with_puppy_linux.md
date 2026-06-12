---
title: "need help with puppy linux"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by c2tarun on 2011-01-20
I downloaded the puppy linux iso. I don't want to write that iso to any disk (because most of the linux disks are used just once and then the just acquire space in my cd bag). 
I tried to create its bootable pen drive by start-up disk creator. But start-up disk creator is not accepting the iso file for puppy. Can anyone please tell me how to make a bootable pen-drive of puppy linux

---

### Post by ronnielsen1 on 2011-01-20
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

will do what you want.

Another option with puppy is to mount the iso, make a folder on your hard drive containing the following files:

 Frugal
       The files vmlinuz, initrd.gz and pup_xxx.sfs (and maybe z*.sfs, the "zdrv") are copied to a partition. This partition may already have something installed on it and that will not be disturbed. This can be any type of partition, MSDOS, Windows (FAT, NTFS) or Linux (EXT2, EXT3, EXT4 or REISERFS). For most people this is the recommended option.

and then edit your grub menu (change for your situation)

   title Puppy Linux 4.3 frugal 
   rootnoverify (hd0,5)
   kernel (hd0,5)/vmlinuz [COLOR=#CC33CC]root=/dev/ram0[/COLOR] pmedia=atahd 
   initrd (hd0,5)/initrd.gz       Or even just this:


  title Puppy Linux 4.3 frugal 
   rootnoverify (hd0,5)
   kernel /vmlinuz [COLOR=#CC33CC]root=/dev/ram0[/COLOR] pmedia=atahd 
   initrd /initrd.gzhttp://www.puppylinux.com/hard-puppy.htm

---


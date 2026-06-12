---
title: "Doubts about fstab"
date: 2005-09-08
forum: Installation &amp; Upgrades
---

### Post by papangul on 2005-09-08
I'm using Ubuntu without any problems but today when by chance I opened my /etc/fstab I noted something that is unusual:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                       /proc                 proc         defaults        0       0
/dev/hda8              /                         reiserfs    defaults        0       1
/dev/hda1              /boot                  ext2         defaults        0       2
/dev/hda5              /home                 reiserfs    defaults        0       2
/dev/hda6              /usr                   reiserfs      defaults        0       2
/dev/hda9              none                   swap    sw              0       0
/dev/hdb                /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0                 /media/floppy0  auto    rw,user,noauto  0       0  
It's uncommon to have reiserfs partitions without the 'notail' option, should i add it?
During installation do i have to add the 'notail' option manually?

---

### Post by kkvenkit on 2005-09-08
Found online by googling:

notail
By default, reiserfs stores small files and `file tails' directly
		  into the tree. This confuses some utilities like
		  LILO. This option is used to disable
		  packing of files into the tree.

I would therefore not advise you to change /etc/fstab if things are currently working.

---


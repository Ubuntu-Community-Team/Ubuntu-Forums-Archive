---
title: "Feisty cannot find DVD Drive."
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by gwelch925 on 2007-04-25
After doing a clean install of Ubuntu Feisty Fawn, I cannot find my DVD drive. This is pretty peculiar because not only did I install Feisty Fawn using this drive, but due to an issue with GRUB, I also chain-load from the Install CD. So the drive is definitely working, I have also tested it in windows just fine and worked great in Edgy.

So i am clueless to look for answers. If anyone can help, please.

I know in these type of cases people usually ask for the fstab so here you are: 

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=efbcd3ee-9761-4a0d-88da-ffce3d483e78 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=00439695-c7e8-483e-b422-ece4034503fe /home           ext3    defaults        0       2
# /dev/hdb1
UUID=cbedcbe2-7a82-48be-892e-470f172bf314 /media/storage  ext3    defaults        0       2
# /dev/hda4
UUID=12EC459B937B90D1 /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda1
UUID=f6201396-fb56-446e-81d1-5f1c64eb885f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0  

If you need any other information i should be immediately available for comment.

---

### Post by gwelch925 on 2007-04-27
I don't mean to be annoying, but i am going to bump this thread. Please if anyone has any ideas.

---


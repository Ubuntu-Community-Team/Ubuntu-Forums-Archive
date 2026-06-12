---
title: "Boot Loader Problems, I really need help"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by goamind on 2007-03-02
Greetings!
I need help with the following issue:
I have ubuntu installed on a 60Gb HD for 1 month. Yesterday I bought a new SATA II HDD and installed Ubuntu on it. The problem is that the installation has overwritten my formal Grub Loading settings and now I can't boot in my old Ubuntu on the old HDD. 
I really need to do this to backup some data-bases.
Here is how my fstab looks:
/etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda6       /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda9       /media/hda9     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
//mirceas/mircea /home/mircea/public/ smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0
//mirceas/mircea /home/mircea/group/ smbfs credentials=/root/.smbcredentials,dmask=755,fmask=777 0 0


/dev/sda5       /               ext3    defaults,utf8,umask=007,gid=46 0      1
/dev/sda6       none            swap    sw              0       0
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda7       /media/sda7     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda8       /media/sda8     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda9       /media/sda9     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda10       /media/sda10     vfat    defaults,utf8,umask=007,gid=46 0       1

in /boot/grub/menu.lst am partea asta +altele:
title        Ubuntu, kernel 2.6.15-28-386
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.15-28-386 root=/dev/hda8 ro quiet splash
initrd        /boot/initrd.img-2.6.15-28-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.15-28-386 root=/dev/hda8 ro single
initrd        /boot/initrd.img-2.6.15-28-386
boot

title        Ubuntu, kernel 2.6.15-27-386
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.15-27-386 root=/dev/hda8 ro quiet splash
initrd        /boot/initrd.img-2.6.15-27-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.15-27-386 root=/dev/hda8 ro single
initrd        /boot/initrd.img-2.6.15-27-386
boot

title        Ubuntu, kernel 2.6.15-23-386
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/hda8 ro quiet splash
initrd        /boot/initrd.img-2.6.15-23-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/hda8 ro single
initrd        /boot/initrd.img-2.6.15-23-386
boot

title        Ubuntu, memtest86+
root        (hd0,7)
kernel        /boot/memtest86+.bin
boot

This one looks OK, but as far as I remember there is a grub.conf file that I cant find and I do not know what to modiffy.
Thank you very much for your help!
Sincerely,
Mircea

---

### Post by Herman on 2007-03-02
Hello goamind,
I am not sure, but normally when we add an SCSI (or Sata) hard disk it takes over as (hd0) or hard disk number 1, meaning your IDE hard disk will now be made (hd1), or hard disk number 2.

There isn't any grub.conf file in Ubuntu that I know of, some other Linux distros call their equivalent of menu.lst the 'grub.conf' file. You may need to edit one or both of your /boot/grub/menu.lst files.

Where did you get that menu.lst you have shown in your post? That looks to me as if it might have come from your old Ubuntu system in your IDE drive. 

Are you asking what would likely work as an operating system entry in your new installation for booting your old installation?

Maybe try,
```
 title        Ubuntu, kernel 2.6.15-28-386
root        (hd1,7)
kernel        /boot/vmlinuz-2.6.15-28-386 root=/dev/hdb8 ro quiet splash
initrd        /boot/initrd.img-2.6.15-28-386
savedefault
boot
``` That's just a guess.

I recommend that you try pressing your 'c' key from your grub menu when booting for a [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
If you try some of the commands in the link just provided, you should be able to boot up your old operating system in a few minutes. If you take notes of what commands you use, you can add those to  one of your menu.lst files when you have time.

Another approach which might be better in the long run would be to edit your menu.lst in your old (IDE) installation with the above changes and then make an entry in your new grub menu that will bring up your old grub menu.

 Just add a 'configfile' bootiing entry in the grub menu you will be booting with, (the one in the Sata drive), that finds the grub menu in the IDE drive, like this,
```
title       Configfile boot on old Ubuntu installation 
configfile (hd1,7)/boot/grub/menu.lst
```Or you could try to chainload the MBR of the IDE drive,
```
title       Chainload the IDE MBR
root      (hd1)
chainloader +1
```I hope I have interpreted your question correctly,
Regards, Herman :)

---


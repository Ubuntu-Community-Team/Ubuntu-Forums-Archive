---
title: "Cannot mount &quot;/home&quot; during installing"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by hsmwrv on 2007-07-04
I'm installing Ubuntu 7.04 from the desktop CD but having some trouble mounting "/home" partition.

/dev/hda1  /windows  ntfs
/dev/hda5  /              ext3
/dev/hda6                 swap
/dev/hda7  /home      ext3

Above is the partition table of my hard drive and how I want to mount each partition, but the partition guide keeps failing to mount "/home".  Does anyone know what may cause the problem?

There is some information update.  I've finished installing Ubuntu without mounting /dev/hda7 as /home.  As I was trying to mount it manually, I discovered that /dev/hda7 was mounted to /media/cdrom0.  Odd...

---

### Post by louieb on 2007-07-04
Please post your partition table.  From Ubuntu open Applications>Accessories>Terminal and run:```
sudo fdisk -l 
``` (lower case -L)  
Also post the output of  ```
cat /etc/fstab 
```

---

### Post by hsmwrv on 2007-07-05
Here's the output of "sudo fdisk -l"

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         973     7815591    7  HPFS/NTFS
/dev/hda2             974        4866    31270522+   5  Extended
/dev/hda5             974        1581     4883728+  83  Linux
/dev/hda6            1582        1642      489951   82  Linux swap / Solaris
/dev/hda7            1643        4866    25896748+  83  Linux


And the /etc/ fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda5
UUID=1a28d7aa-06cf-4032-9023-278078da93d1 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda7
UUID=831d5302-d654-4f6b-b5c9-7b23d186e77b /media/hda7 ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hda1
UUID=8E74E91874E903B5 /windows ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/hda6
UUID=4f8fc703-ba5d-4fe0-a49d-c523adbc3501 none swap sw 0 0
UUID=831d5302-d654-4f6b-b5c9-7b23d186e77b /media/cdrom0 ext3 user,atime,auto,rw,dev,exec,suid 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdd /media/cdrom2 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0

---

### Post by r0ck80y on 2007-07-05
**UUID=831d5302-d654-4f6b-b5c9-7b23d186e77b **/media/hda7 ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2.....
**UUID=831d5302-d654-4f6b-b5c9-7b23d186e77b** /media/cdrom0 ext3 user,atime,auto,rw,dev,exec,suid 0 0

Same partition mounting at 2 places. Remove the second line (/media/cdrom line), save file and reboot.

---

### Post by louieb on 2007-07-05
Don't know why /home could not be mounted on hda7. Perhaps a bug in the Feisty live installer. If you don't have a lot invested yet you could try the install again. Just use the manual option. The only live CD install I have used is Dapper. So I don't know if things have changed. But for Feisty putting /home on a separate partition was not a problem. OR the psychocats link has a howto on creating a separate home   although its kind of a pain to do.

Nice catch r0ck80y.

---

### Post by hsmwrv on 2007-07-06
> **louieb said:**
> Don't know why /home could not be mounted on hda7. Perhaps a bug in the Feisty live installer. If you don't have a lot invested yet you could try the install again. Just use the manual option. The only live CD install I have used is Dapper. So I don't know if things have changed. But for Feisty putting /home on a separate partition was not a problem. OR the psychocats link has a howto on creating a separate home   although its kind of a pain to do.

Nice catch r0ck80y.

I guess next time I'll try the manual option.

---


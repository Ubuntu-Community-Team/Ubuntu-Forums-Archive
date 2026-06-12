---
title: "2 linux"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by Icebear on 2007-12-25
Hi 

I had 7.10 (64 bit) working well and I got skype and flash to work.

then I installed a 2nd ubuntu so I could play around and keep the first one so the wife could use it for her day to day needs(and it would not matter if I crashed the 2nd ubuntu)

But when I went to restart the first install
I got 
fsck.ext3 unable to resolve 'UUID=eb73a69b-a4b7-ado5-fbde8d'

I have a broken windoze on hda2 (fat 32)
1ist ubuntu hda5 (ext3)
2nd unbuntu hda6 (ext3)
swap last

thanks

I only know a little about linux

---

### Post by louieb on 2007-12-25
It so happens that the uuid will change when a partition gets formated. 
open Applications>Accessories>terminal and run ```
blkid
```to list your partitions and their uuid
then you run to edit 
```
gksudo gedit /etc/fstab
```and match up the uuid from blkid
[Nuts Ubuntu FAQ]("http://louboldt.com/ilinuxmisc.htm")

---

### Post by Icebear on 2007-12-25
hi thanks for the help but I am not sure what uuid to copy to where

studio@studio:~$ blkid
/dev/hda1: LABEL="PQSERVICE" UUID="16D9-B5D2" TYPE="vfat" 
/dev/hda2: LABEL="ACER" UUID="11DF-1F3E" TYPE="vfat" 
/dev/hda5: UUID="2d390cc1-96d7-4856-be5f-3cea58ae4866" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda6: UUID="7ed78aad-a79b-4bd9-8e37-068c022dcb46" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda7: UUID="5b42c610-1ce4-43c2-b6ce-caec21c36bc5" TYPE="swap" 
studio@studio:~$


icebear

---

### Post by rsambuca on 2007-12-25
> **Icebear said:**
> hi thanks for the help but I am not sure what uuid to copy to where

studio@studio:~$ blkid
/dev/hda1: LABEL="PQSERVICE" UUID="16D9-B5D2" TYPE="vfat" 
/dev/hda2: LABEL="ACER" UUID="11DF-1F3E" TYPE="vfat" 
/dev/hda5: UUID="2d390cc1-96d7-4856-be5f-3cea58ae4866" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda6: UUID="7ed78aad-a79b-4bd9-8e37-068c022dcb46" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda7: UUID="5b42c610-1ce4-43c2-b6ce-caec21c36bc5" TYPE="swap" 
studio@studio:~$


icebear

If you post the output of the following command, we can give you exact instructions to fix this:```
cat /etc/fstab
```

---

### Post by Icebear on 2007-12-25
I hope this make sense I am not sure how to record the terminal to the net the best way

studio@studio:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=7ed78aad-a79b-4bd9-8e37-068c022dcb46 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=16D9-B5D2  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=11DF-1F3E  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=2d390cc1-96d7-4856-be5f-3cea58ae4866 /media/hda5     ext3    defaults        0       2
# /dev/hda7
UUID=5b42c610-1ce4-43c2-b6ce-caec21c36bc5 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


Thanks 
Icebear

---

### Post by rsambuca on 2007-12-25
That file is OK.  We have to fix the fstab from your first Ubuntu installation.  To do this, copy and paste the output of the following:```
cat /media/hda5/etc/fstab
```

---

### Post by Icebear on 2007-12-25
thank you very much for your help I really appreicate it

for the frist ubuntu specs

studio@studio:~$ cat /media/hda5/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=2d390cc1-96d7-4856-be5f-3cea58ae4866 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=11DF-1F3E  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=eb73a69b-a4b7-4579-ad05-f9bded87de8d /media/hda6     ext3    defaults        0       2
# /dev/hda7
UUID=5b42c610-1ce4-43c2-b6ce-caec21c36bc5 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
studio@studio:~$ 


icebear

---

### Post by rsambuca on 2007-12-25
> **Icebear said:**
> thank you very much for your help I really appreicate it

for the frist ubuntu specs

studio@studio:~$ cat /media/hda5/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=2d390cc1-96d7-4856-be5f-3cea58ae4866 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=11DF-1F3E  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=eb73a69b-a4b7-4579-ad05-f9bded87de8d /media/hda6     ext3    defaults        0       2
# /dev/hda7
UUID=5b42c610-1ce4-43c2-b6ce-caec21c36bc5 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
studio@studio:~$ 


icebear

You just have to correct the information for the /dev/hda6 line.  To do this, you can use the text editor called gedit.  You will open gedit using root permissions by using 'gksudo'.  Therefore, enter the following command to edit and correct the fstab from your first Ubuntu partition:```
gksudo gedit /media/hda5/etc/fstab
```

Then correct the line I have highlighted in red:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda5
UUID=2d390cc1-96d7-4856-be5f-3cea58ae4866 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda2
UUID=11DF-1F3E /media/hda2 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda6
[COLOR="Red"]**UUID=7ed78aad-a79b-4bd9-8e37-068c022dcb46**[/COLOR]  /media/hda6 ext3 defaults 0 2
# /dev/hda7
UUID=5b42c610-1ce4-43c2-b6ce-caec21c36bc5 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```After you have made the change, then save the file, close gedit, and you should be able to boot properly into your first Ubuntu installation.

---

### Post by Icebear on 2007-12-25
the 1st ubuntu is now back. Thank you so much for your help!!!!!!! :):)

icebear
:popcorn:

---


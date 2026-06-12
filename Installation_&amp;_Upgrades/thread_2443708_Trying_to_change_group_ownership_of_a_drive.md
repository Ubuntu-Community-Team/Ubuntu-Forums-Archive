---
title: "Trying to change group ownership of a drive"
date: 2020-05-19
forum: Installation &amp; Upgrades
---

### Post by Malcolm_Brown on 2020-05-19
I have recently installed Ubuntu 20.04LTE on aToshiba laptop

I have two NTFS drives in addition to the Ubuntu partitions.  I find that root has group ownership of the drives, for example:-

ls -l /media/MMData
total 120
drwxrwxrwx 1 malcolm root     0 May  4 18:33 '$RECYCLE.BIN'
drwxrwxrwx 1 malcolm root 32768 May 18 09:20  AudioBooks
drwxrwxrwx 1 malcolm root  8192 May 14 20:01  Malcolm
drwxrwxrwx 1 malcolm root  4096 May  4 18:49  Marian
drwxrwxrwx 1 malcolm root 32768 Nov 14  2019  mp3Music
drwxrwxrwx 1 malcolm root 45056 Jun  3  2020  Music
drwxrwxrwx 1 malcolm root     0 May 11 12:49 'System Volume Information'


This is causing problems of programs being unable to access files.  I tried to change the group ownership by using:-

sudo chgrp -R malcolm /media/MMData

Group ownership did not change.

The fstab file is as follows (my user id is 1000):-


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=e228379f-272a-4784-8726-9abecd0b86ae /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=3E5E-44D0  /boot/efi       vfat    umask=0077      0       1
UUID=32A04290A0425A8D /media/MMData ntfs-3g defaults,locale=en_GB.utf8,uid=1000 0 0
UUID=5CC26B8DC26B69EA /media/Win1064 ntfs-3g defaults,locale=en_GB.utf8,uid=1000 0 0
/swapfile                                 none            swap    sw              0       0


How can group ownership of a drive be changed?  Your assistance would be appreciated.  Thanks.

---

### Post by dino99 on 2020-05-19
adapt with your own specs: sudo chown -R user:user /path/to/folder for linux ones
or follow [https://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/](https://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/) to build a share

---

### Post by Morbius1 on 2020-05-19
Unmount the partition:
```
sudo umount /media/MMData 
```
Change this:
>  UUID=32A04290A0425A8D /media/MMData ntfs-3g defaults,locale=en_GB.utf8,uid=1000 0 0
To this:
>  UUID=32A04290A0425A8D /media/MMData ntfs-3g defaults,locale=en_GB.utf8,uid=1000[COLOR=#ff0000]**,gid=1000**[/COLOR] 0 0
Remount using this command:
```
sudo mount -a
```

You can't use chgrp, chown, chmod, or ch-anything with an NTFS partition. You must define permissions when you mount it in fstab. As **uid** specifies the owner of the mounted partition **gid** specifies the group.

---

### Post by Malcolm_Brown on 2020-05-19
Thank you so much!  Very helpful.  I now know about gid which I didn't before.  Thanks.

---

### Post by ActionParsnip on 2020-05-19
NTFS can't hold Linux file permissions so the chown / chgrp commands will always do nothing. You set the access at mount time

---


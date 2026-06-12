---
title: "Merging Windows Partition"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by Man_Jide on 2007-01-25
Hello Ubuntu Friends, 
I have being using Ubuntu side by side with Windows XP for some time now till I decided to merge two fat32 partitions (hda5 and hda6) together to have a new hda5. Before the merger, the two fat32 partitions were visible in Ubuntu. After the merger, I now have problem with the new partition whenever Ubuntu is starting.  On checking the log file at /var/log/fsck/checkfs, I saw this:

Log of fsck -C -R -A -a 
Thu Jan 25 21:33:52 2007

fsck 1.39 (29-May-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda5: 193 files, 101453/4434622 clusters
fsck.ext2: Unable to resolve 'UUID=ed8e383c-3687-4fe7-bd4f-68069de27357'

fsck died with exit status 8

Thu Jan 25 21:33:54 2007

The question is, do anyone know how to solve this problem so that my Ubuntu can start with any problem (without stopping when it is scanning the partitions during startup). I discovered that in /media that hda6 is still there although I had already merged it.
Note: The merge was done with Partition Magic in Windows.

Thanks for your support,
Man-Jide

---

### Post by shane2peru on 2007-01-25
If the merger was done in Windows, then Ubuntu doesn't know anything about it.  And if it was already in your fstab then that will cause Ubuntu problems.  Please post your ```
cat /etc/fstab
```  as well as your ```
sudo fdisk -l
```  I know there is a way to see your uid number, I don't remember what the command is though.  Also ```
mount
```  I think that will show the uid if I'm not mistaken.  We will need to remove a line from your fstab.  

Shane

---

### Post by logos34 on 2007-01-25
list disk partitons by UUID:
> ls /dev/disk/by-uuid/ -alh

---

### Post by Man_Jide on 2007-02-02
Hello Shane2peru and Logos34, It looks like my reply did not come over. The information you need are as follows:

**cat /etc/fstab** will give:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=1e184c92-8679-4299-97ec-bda9090d11aa /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=EE74E87574E84247 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=4557-AA2F  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=ed8e383c-3687-4fe7-bd4f-68069de27357 /media/hda6     ext2    defaults        0       2
# /dev/hda3
UUID=295cb46a-95e4-4559-9682-97ca1bbc208c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

**sudo fdisk -l** will give:

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5007    40218696    7  HPFS/NTFS
/dev/hda2            5008        9428    35511682+   f  W95 Ext'd (LBA)
/dev/hda3           12030       12161     1060290   82  Linux swap / Solaris
/dev/hda4            9429       12029    20892532+  83  Linux
/dev/hda5            5008        9428    35511651    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sda: 259 MB, 259522560 bytes
65 heads, 32 sectors/track, 243 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         244      253424    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 64, 32) logical=(243, 44, 32)

**ls /dev/disk/by-uuid/ -alh** will give:

total 0
drwxr-xr-x 2 root root 120 2007-01-29 13:58 .
drwxr-xr-x 6 root root 120 2007-01-29 14:58 ..
lrwxrwxrwx 1 root root  10 2007-01-29 14:58 1e184c92-8679-4299-97ec-bda9090d11aa -> ../../hda4
lrwxrwxrwx 1 root root  10 2007-01-29 14:58 295cb46a-95e4-4559-9682-97ca1bbc208c -> ../../hda3
lrwxrwxrwx 1 root root  10 2007-01-29 14:58 4557-AA2F -> ../../hda5
lrwxrwxrwx 1 root root  10 2007-01-29 13:58 EE74E87574E84247 -> ../../hda1


I hope to get your reply soon.
Thanks,
Man_Jide

---

### Post by shane2peru on 2007-02-02
> **Man_Jide said:**
> 
**cat /etc/fstab** will give:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=1e184c92-8679-4299-97ec-bda9090d11aa /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=EE74E87574E84247 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=4557-AA2F  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=ed8e383c-3687-4fe7-bd4f-68069de27357 /media/hda6     ext2    defaults        0       2
# /dev/hda3
UUID=295cb46a-95e4-4559-9682-97ca1bbc208c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Ok, it looks like the line that says ```
# /dev/hda5
UUID=ed8e383c-3687-4fe7-bd4f-68069de27357 /media/hda6     ext2    defaults        0       2
```  should be commented out.  Here is how we are going to do that.  In the terminal, we are going to backup our fstab first. ```
sudo  cp /etc/fstab /etc/fstab_backup
```  Next we are going to comment out that line with ```
sudo gedit /etc/fstab
```  Look for the line that I posted above and put a # in front of the UUID part.  That will comment that out for you.  Now just click on save and close.  Now we need to A.  Reboot, or B.  in the terminal you can type ```
sudo mount -a
```  That should remount all your partitions.  Let me know if that works for you.

Shane

---

### Post by Man_Jide on 2007-02-02
Hello Shane2Peru,

Thanks for the great help. The problem is solved through the guideline you gave. My Ubuntu no longer hang during booting.

Thanks once more,

Man_Jide

---

### Post by shane2peru on 2007-02-02
Glad to hear it!  :D

Shane

---


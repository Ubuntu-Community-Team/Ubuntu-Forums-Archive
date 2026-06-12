---
title: "The disk drive for /windows is not ready yet or not present"
date: 2014-09-06
forum: Installation &amp; Upgrades
---

### Post by tlotr2 on 2014-09-06
Hi,  I have installed Ubuntu 14.04 x64 along side Windows 8.1 x86 on another hard drive. Now I am getting this message at the start "The disk drive for /windows is not ready yet or not present" Press S to skip or M for manual recovery.   How do I resolve this issue.  I don't want this message at the start cause the OS doesn't load automatically because of this unsless someone presses S to skip it.  My ntfs windows and another partition is getting mounted properly after adding the UUID in /etc/fstab but I am still getting this message at the start.  Please someone help on this. I have googled a lot but still unable to get this message removed from the start.   Also I have even disabled the fast startup in my Windows 8.1 following another tutorial but it seems it doesn't work either.

---

### Post by yancek on 2014-09-06
The only time I see that message is if I have an entry in fstab for a partition on an external drive and the external drive is not attached.  If you have both drives attached, you should not be seeing that message.  Have you run the mount command or re-booted since putting the entry in fstab?

---

### Post by LostFarmer on 2014-09-06
post the  /etc/fstab

---

### Post by tlotr2 on 2014-09-06
Hi LostFarmer,

Here is the contents of the fstab file and yancek, yes I have re-booted my machine couple of times post adding the entires in fstab.

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=2725c74b-0c36-49ed-96de-1c232ed8f70d /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda6 during installation
UUID=26BC-A834  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=4fb8216a-2f89-4974-a07d-0ce4de525742 none            swap    sw              0       0
UUID=AAC4EF7EC4EF4AE1 /media/mount-point ntfs defaults 0 1
UUID=B8E4D711E4D6D12C /media/mount-point2 ntfs defaults 0 1
UUID=1bd5c8af-6f61-422b-b653-7f8c9635369d /media/mount-point3 ext4 defaults 0 1

Here is the output of blkid

/dev/sda1: UUID="2725c74b-0c36-49ed-96de-1c232ed8f70d" TYPE="ext4" 
/dev/sda5: UUID="4fb8216a-2f89-4974-a07d-0ce4de525742" TYPE="swap" 
/dev/sda6: UUID="1bd5c8af-6f61-422b-b653-7f8c9635369d" TYPE="ext4" 
/dev/sdb1: LABEL="Windows" UUID="B8E4D711E4D6D12C" TYPE="ntfs" 
/dev/sdc1: LABEL="Data 2" UUID="AAC4EF7EC4EF4AE1" TYPE="ntfs"

---

### Post by LostFarmer on 2014-09-06
```
# /windows was on **/dev/sda6** during installation
UUID=26BC-A834  /windows        vfat    utf8,umask=007,gid=46 0       1
```  This is the partition that is having problems, is it indeed a FAT32/16 partition ?  Or is it NTFS ?


added: blkid output: 
```
 **/dev/sda6**: UUID="1bd5c8af-6f61-422b-b653-7f8c9635369d" TYPE="ext4"  
```  is sda6 ext4 or fat or ntfs ??  there is something wrong here.

---

### Post by tlotr2 on 2014-09-07
Hi LostFarmer,

Thanks for replying.

When I installed Ubuntu, I created the partition manually. One root partition the other a swap partition and the third a FAT32 partition. Then once the OS was installed I went into disks and then deleted the FAT32 partition and then created a ext4 partition.

So during the installation it was FAT32 sda6 but later on it became a ext4 partition.

---

### Post by tlotr on 2014-09-08
Hi all Ubuntu experts,

Will the issue be solved if I delete the ext4 partition and re-create a FAT32 partition abd label it windows.

Will this resolve my problem?

---

### Post by LostFarmer on 2014-09-08
I do not have any time to give help.  You will have to edit   /etc/fstab to fix problem.  Just deleting  and re-create will not fix problem, the UUID would be incorrect.  

this is my fstab and may not be the best for NTFS partition , your mount-point and UUID would be different and the uid=dad (my user name)
UUID=C6349A63349A55F1 /media/dad/Data ntfs-3g  defaults,uid=dad,gid=dad,dmask=022,fmask=133,windows_names 0 0

---

### Post by tlotr on 2014-09-08
Hi LostFarmer,

Yes the issue got resolved post deleting the entry for /windows from the fstab file.

---


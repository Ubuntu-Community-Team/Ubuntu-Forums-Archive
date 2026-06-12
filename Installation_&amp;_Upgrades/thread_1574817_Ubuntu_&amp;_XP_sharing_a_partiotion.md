---
title: "Ubuntu &amp; XP sharing a partiotion"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by jpaulb on 2010-09-14
I want to have XP & Ubuntu share the same data files, openoffice, mail etc. I have a fat32 partition for this: but I have totally forgotten how to get xp and ubuntu to share.

Must be getting old.;)

---

### Post by tommcd on 2010-09-15
To mount the fat32 partition in Ubuntu, see this:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
To setup the partition for automounting you can ad it to your fstab in Ubuntu:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
Note: An NTFS partition would be a better option since Ubuntu / linux now has the ability to read and write to the NTFS file system.
Windows does not know how to read linux partitions, so linux file systems are not an option here. I think there may be some third party programs that can enable Windows to read linux file systems. See:
[http://www.linuxjournal.com/article/9449](http://www.linuxjournal.com/article/9449)
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)
Hope this helps.

---

### Post by jpaulb on 2010-09-20
Thanks
Just got back.
I did a dry run on a old laptop running windows 2000


When I installed Ubuntu after windows was installed the boot loader GRUB II does not give me the option to boot from the recovery partition. Is there any info about how to include the recovery partition in the boot menu?

---

### Post by tommcd on 2010-09-20
> **jpaulb said:**
> 
I did a dry run on a old laptop running windows 2000 
When I installed Ubuntu after windows was installed the boot loader GRUB II does not give me the option to boot from the recovery partition. Is there any info about how to include the recovery partition in the boot menu?
Do you mean the Windows 2000 recovery partition?
Are you able to boot both Ubuntu and Windows 2000 from the grub2 menu?
Why do you need to boot to the Windows 2000 recovery partition anyway? If that is indeed what you are referring to.
Or so you mean that you can not boot to *recovery mode* in Ubuntu?

Anyway, booting to a recovery partition, or Ubuntu's recovery mode, has nothing to do with sharing files between Windows and Ubuntu using a fat32 partition.
I am not sure where you are going with this.

---

### Post by jpaulb on 2010-09-21
> **tommcd said:**
> Do you mean the Windows 2000 recovery partition?
Are you able to boot both Ubuntu and Windows 2000 from the grub2 menu?
Why do you need to boot to the Windows 2000 recovery partition anyway? If that is indeed what you are referring to.
Or so you mean that you can not boot to *recovery mode* in Ubuntu?

Anyway, booting to a recovery partition, or Ubuntu's recovery mode, has nothing to do with sharing files between Windows and Ubuntu using a fat32 partition.
I am not sure where you are going with this.

It is best I start a new thread.

---

### Post by maestrobwh1 on 2010-09-21
I'd really use NTFS with the ntfs-3g driver.

I have been doing this since ntfs-3g was available.  I have never had data loss on ntfs... have had it on fat32 several times.  It is an antiquated (okay, maybe that is harsh and an opinion) and inferior file system... and if you ever intend on storing a file larger than 4 GB (dvd iso for example) you can't.

---

### Post by jpaulb on 2010-09-23
> **maestrobwh1 said:**
> I'd really use NTFS with the ntfs-3g driver.

I have been doing this since ntfs-3g was available.  I have never had data loss on ntfs... have had it on fat32 several times.  It is an antiquated (okay, maybe that is harsh and an opinion) and inferior file system... and if you ever intend on storing a file larger than 4 GB (dvd iso for example) you can't.

The share partition is not formatted as NTFS. Had to use windows to do that since gparted can not.

---

### Post by jpaulb on 2010-09-25
Now that I have the the other issue solved.
How do I get both Windows and Ubuntu to use the newly created NTFS partition for sharing data, browser and mail etc.

---

### Post by tommcd on 2010-09-26
> **jpaulb said:**
> 
How do I get both Windows and Ubuntu to use the newly created NTFS partition for sharing data, browser and mail etc.
This is covered in the reference I linked to in a previous post.
To mount Windows partitions in Ubuntu:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
And to edit your */etc/fstab* file so the NTFS partition is mounted automatically:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
Windows should find the NTFS partition and and enable you to read and write to it.

---


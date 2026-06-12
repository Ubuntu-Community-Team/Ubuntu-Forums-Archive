---
title: "Had to clean boot folder, deleted files, wont boot"
date: 2015-02-28
forum: Installation &amp; Upgrades
---

### Post by francis-degagne on 2015-02-28
Yes this is idiodic. I've been an Ubuntu user for almost two years...sadly I set up my file system wrong and was always running out of space in the boot folder because it wasn't big enough and I couldn't increase the size.

I am able to run Ubuntu off DVD and see my file system. Can I copy some files back into boot?

I tried reinstalling Ubuntu but stopped because there are no options to install over an existing account, it will only do a wipe and clean install.

Fortunately most of my files are on another hard drive, however my documents folder is risking deletion - or can I still install without losing it?!

I thought I was using 14.04, so didn't think it was an issue to delete the 13 files...boy was I wrong!

Any advice appreciated

---

### Post by egeezer on 2015-02-28
You could run off the DVD and copy your Documents folder to a USB drive (thumb or external), then reinstall.

---

### Post by oldfred on 2015-02-28
I really do not recommend it, but you can overinstall. You only keep your data as anything with settings will get overwritten with the new standard defaults. So still best to have a good backup.
You can choose not to use use the separate /boot partition also, but must use Something Else.
 Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

      
 Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

   RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

    
I prefer to use synaptic to uninstall kernels. But I thought the new versions, now only kept two kernels by default.

 Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

   HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed with newer Ubuntu will also remove old kernels
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does as upgrade only does existing packages, this adds new 
sudo apt-get dist-upgrade  #updates dependencies


 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a

---

### Post by francis-degagne on 2015-03-01
Thanks, I am able to boot from dvd and I can see my old partition, however my profile in the /home directory is not accessible. I suppose I need to learn how to do this through terminal and sudo? I can do basic stuff but navigating between drives isn't my strength...i.e. need more instruction. 

Ideally I would be able to copy those files I deleted back to my boot directory, and bob's your uncle, namely it is looking for /vmlinuz-313.0-44-generic.efi.signed. Wonder if it is possible to find this file somewhere, so far it does not show up in any searches.

Thanks for the link, plenty of preventative measures there. Sadly I have been diligent in back ups but they are useless if I reinstall overtop. 

I also don't have the option to reinstall over an existing installation, I guess it can't see those files, even though I point it to the right drive it says (something) basically can't see the old installation.

---

### Post by Bashing-om on 2015-03-01
francis-degagne; Hello;

Mind you I am going where I have never gone before, BUT; in theory it should be possible to do  a CHange Root into the install from the liveDVD, install the kernel and re-install grub.

That might save the week for you.

[INDENT][INDENT]more than 1 path 
[INDENT][INDENT][INDENT]to an end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by francis-degagne on 2015-03-01
How about restoring the recycle bin, putting the files I deleted back into their proper folders....Wonder how to do that (HINT) ;)

---

### Post by Bashing-om on 2015-03-01
francis-degagne; Maybe:

from the liveDVD file manager 'nautilus' can you see the files you hope are there in the trash ?
Else maybe mount the partition that contains 'trash' and list the contents .

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by francis-degagne on 2015-03-01
can't view anything inside my profile folder in home with file manager.

---

### Post by Bashing-om on 2015-03-01
francis-degagne; OK ;

Let's see what we can do from terminal.
post back:
```

sudo fdisk -lu
sudo parted -l

```
so we know what partition is where and also where '/' and if there is a separate /home partition.
Once known we can mount the file system containing /home - from that liveDVD - and look and see what there is in Trash.

[INDENT][INDENT]a look never did hurt
[/INDENT][/INDENT]

---

### Post by francis-degagne on 2015-03-01
I deleted the tiny partition and created a new boot partition, am hoping to install here

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA KINGSTON SV300S3 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  768MB  767MB  ext4
 3      768MB   120GB  119GB                     lvm

---

### Post by Bashing-om on 2015-03-01
francis-degagne; Yuk !

This:
> 
I deleted the tiny partition and created a new boot partition

means there is no longer an easy reliable means to recover any files. The pointers to the data no longer exist.
I do not have any experience with LVM so can not advise further on that issue.

If it remains a goal to retrieve files from that hard drive you are now at the forensic recovery stage.
You have a lot of homework to do.
see:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

[INDENT][INDENT]haste do
[INDENT][INDENT][INDENT]make waste
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by francis-degagne on 2015-03-01
```
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   234441647   117220823+  ee  GPT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root: 110.7 GB, 110721236992 bytes
255 heads, 63 sectors/track, 13461 cylinders, total 216252416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 8543 MB, 8543797248 bytes
255 heads, 63 sectors/track, 1038 cylinders, total 16687104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004b5af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   925364057   462681997+   7  HPFS/NTFS/exFAT
/dev/sdc2       925364222   976771071    25703425    5  Extended
/dev/sdc5       925364224   960088063    17361920   83  Linux
/dev/sdc6       960090112   976771071     8340480   82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sde: 1048 MB, 1048576000 bytes
64 heads, 32 sectors/track, 250 cylinders, total 512000 sectors
Units = sectors of 1 * 2048 = 2048 bytes
Sector size (logical/physical): 2048 bytes / 2048 bytes
I/O size (minimum/optimal): 2048 bytes / 2048 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          59      511999     1023882    6  FAT16

Disk /dev/sdf: 2047 MB, 2047678976 bytes
64 heads, 63 sectors/track, 991 cylinders, total 3999373 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1             245     3995711     1997733+   6  FAT16

Disk /dev/sdi: 1051 MB, 1051983872 bytes
2 heads, 63 sectors/track, 16306 cylinders, total 2054656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x001ef2da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *          32     2054655     1027312    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   234441647   117220823+  ee  GPT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root: 110.7 GB, 110721236992 bytes
255 heads, 63 sectors/track, 13461 cylinders, total 216252416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 8543 MB, 8543797248 bytes
255 heads, 63 sectors/track, 1038 cylinders, total 16687104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004b5af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   925364057   462681997+   7  HPFS/NTFS/exFAT
/dev/sdc2       925364222   976771071    25703425    5  Extended
/dev/sdc5       925364224   960088063    17361920   83  Linux
/dev/sdc6       960090112   976771071     8340480   82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sde: 1048 MB, 1048576000 bytes
64 heads, 32 sectors/track, 250 cylinders, total 512000 sectors
Units = sectors of 1 * 2048 = 2048 bytes
Sector size (logical/physical): 2048 bytes / 2048 bytes
I/O size (minimum/optimal): 2048 bytes / 2048 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          59      511999     1023882    6  FAT16

Disk /dev/sdf: 2047 MB, 2047678976 bytes
64 heads, 63 sectors/track, 991 cylinders, total 3999373 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1             245     3995711     1997733+   6  FAT16

Disk /dev/sdi: 1051 MB, 1051983872 bytes
2 heads, 63 sectors/track, 16306 cylinders, total 2054656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x001ef2da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *          32     2054655     1027312    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 
```


## Still trying to figure this out
## Don't know the structure holding it together

---

### Post by oldfred on 2015-03-01
I do not know LVM, but you do not use standard partition tools. You have to use LVM tools.
Was this an encrypted install? If so and you cannot mount it with your passphase, you should not be able to recover data as that is what encryption is for. 

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)


 Repair gpt & encryption
[http://ubuntuforums.org/showthread.php?t=2197301](http://ubuntuforums.org/showthread.php?t=2197301)

---

### Post by francis-degagne on 2015-03-03
Perhaps LVM is standard backup service, I didn't choose it, knowingly at least. 

It must say life is simpler running from a live DVD

---

### Post by deadflowr on 2015-03-03
> **francis-degagne said:**
> Perhaps LVM is standard backup service, I didn't choose it, knowingly at least. 

It must say life is simpler running from a live DVD

I believe an lvm-setup is created when you choose full-disk encryption during the install.

---


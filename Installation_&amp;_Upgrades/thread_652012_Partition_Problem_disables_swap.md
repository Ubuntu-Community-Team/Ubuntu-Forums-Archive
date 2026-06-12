---
title: "Partition Problem disables swap"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by ian_o on 2007-12-28
It appears an inadvertent boot of the windows recovery by a guest user (i have not used windows on this pc)  killed my partition table. 
I managed to recovery my partitions to the extent that i can once again boot in ubuntu. Windows still does not boot, which is not that bad- but there are still problems with the recovered partition data that prevents mounting the swap partition or viewing partition data with gparted. All partitions mount and can be viewed under ubuntu (except swap of course).

I used testdisk to recover the partition table best i could which now shows as:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1020     8192000    b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        1020        4589    28667896+   7  HPFS/NTFS
/dev/sda3            4591        8014    27503280   83  Linux
/dev/sda4            8015       24322   130994010    f  W95 Ext'd (LBA)
/dev/sda5            8016       15612    61022868   83  Linux
/dev/sda6           15613       18224    20969056   83  Linux
/dev/sda7           23837       24321     3895720   82  Linux swap / Solaris

The first partition (recovery) generates an error. Does anyone know a way to fix this?
I hope that fixing this error will fix the problem. Alternately, does anyone know another reason why i cannot activate the swap partition?

All assistance appreciated.

---

### Post by taurus on 2007-12-28
What does /etc/fstab look like?

```
cat /etc/fstab
```
See if you can activate swap partition by hand with

```
swapon /dev/sda7
free
```

---

### Post by tgilber1 on 2007-12-28
In regards to the swap, the previous post provides a good way to verify.  The "sudo swapon <swap partition>" command turns on the swap and free will show if the swap is activated.  If the swapon command fails, then try recreating the swap partition with the following

1.  sudo mkswap <swap partition>  #ex.  sudo mkswap /dev/sda7
2.  sudo swapon <swap partition> #ex. sudo swapon /dev/sda7
3.  free # no need for sudo; notice the Swap line shows 2G of memory

Mem:       1029420    1009052      20368          0      15068     170700
-/+ buffers/cache:     823284     206136
Swap:      2048184      32960    2015224



There is an issue with sda1 and sda2 partiton with the boundaries overlapping, i.e., end and begin are 1020.  Since Linux is starting up, I would hesitate to change the it.  **I'd research more or better yet, someone with more expertise could offer some advice**.  

One possible alternative is to resize Windows partition, sda1 to end at 1019.  Note, I say possible alternative, there are risks.  In any event, you could reszie sda1 using either parted or gpart.  

If you decide to try the rescue or resizing options using parted - make sure you back up any critical data because using a repartitioning program (e.g., Parted) may result in the loss of data.

Note:  Parted is a great tool for recovering partitions that have been accidently deleted.

Reference:  [http://www.gnu.org/software/parted/manual/html_mono/parted.html](http://www.gnu.org/software/parted/manual/html_mono/parted.html)


_Parted Examples_
1.  sudo parted /dev/sda or sudo parted sda1
2.  From parted prompt, type rescue
3.  Provide begin and end (e.g., 1 and 1019), then parted will look for file signatures

1.  Open terminal via #Applications#Accessories#Terminal
2.  sudo parted /dev/sda
3.  From the parted prompt, type "print" to view partition tables
4.  If resizing first partition, type " resize 1"
6.  Parted will prompts for the beginning and end blocks, type the appropriate values (e.g., 1 & 1019)

In closing, make sure that you are comfortable with whatever you decide to do.  Importantly, research and verify that information is correct.


> **ian_o said:**
> 
I used testdisk to recover the partition table best i could which now shows as:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1020     8192000    b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        1020        4589    28667896+   7  HPFS/NTFS
/dev/sda3            4591        8014    27503280   83  Linux
/dev/sda4            8015       24322   130994010    f  W95 Ext'd (LBA)
/dev/sda5            8016       15612    61022868   83  Linux
/dev/sda6           15613       18224    20969056   83  Linux
/dev/sda7           23837       24321     3895720   82  Linux swap / Solaris

The first partition (recovery) generates an error. Does anyone know a way to fix this?
I hope that fixing this error will fix the problem. Alternately, does anyone know another reason why i cannot activate the swap partition?

All assistance appreciated.

---

### Post by ian_o on 2007-12-28
Progress!!! Thank you for the help so far!

I had tried swapon previously, but had not found the 'mkswap'. After doing a 'mkswap', swapon now works, so i am gettting closer to a repaired system.

Ok- now i understand that setting sda1 to end at 1019 may solve another technical problem - even if the content of that partition itself is still not correct the structure will be better.

Trying 
   sudo parted /dev/sda
actually reveals another problem. print shows 
    (parted) print
    Error: Can't have a partition outside the disk!
Probably because partition 4 ends at 24322 and the disk shows as having 24321 cylinders!!
looking from another pc the extended partition does not need to go past the last cyclinder contained within so i could also just adjust this number back to 24321 within sda4

So now the problem is how to adjust cylinder numbers. 
Using parted for dev/sda1 allows print to work but shows:
  Number  Start   End     Size    File system  Flags
   1      0.00kB  8389MB  8389MB  fat32
Will using rescue take the values 1 and 1019 and work correctly given start and end show as MB vales?

And how would i fix sda4? The rescue within parted does not appear to take a parameter of what partition it is fixing so i hope if used in /etc/sda4 mode, specifying a partition already,  it will only adjust sda4 ....but if someone could confirm this it will help.

---

### Post by tgilber1 on 2007-12-28
Could you post the entire results of the print command when using parted?  You may want to drop the end value of the Windows partition below the value of the next partition.  As you stated in your latest post, you will want to do the same for the last partition.

---

### Post by ian_o on 2007-12-29
The entire results of the print command in parted are:

(parted) p
Error: Can't have a partition outside the disk!
(parted)

That is all!!!

However if i start parted as sudo parted /dev/sda1 i get
(parted) p

Disk /dev/sda1: 8389MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start   End     Size    File system  Flags
 1      0.00kB  8389MB  8389MB  fat32

(parted)


Starting for any /dev/sda2 or /dev/sda4  produces the same error message as for the entire disk, so the error is produced as soon as it considers partition 2.

for 3 , 5 , 6, 7

ian@lambo:~$ sudo parted /dev/sda3
GNU Parted 1.7.1
Using /dev/sda3
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p

Disk /dev/sda3: 28.2GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start   End     Size    File system  Flags
 1      0.00kB  28.2GB  28.2GB  ext3

(parted)  


ian@lambo:~$ sudo parted /dev/sda5 print

Disk /dev/sda5: 62.5GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start   End     Size    File system  Flags
 1      0.00kB  62.5GB  62.5GB  ext3

Information: Don't forget to update /etc/fstab, if necessary.

ian@lambo:~$ sudo parted /dev/sda6 print

Disk /dev/sda6: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start   End     Size    File system  Flags
 1      0.00kB  21.5GB  21.5GB  ext3

Information: Don't forget to update /etc/fstab, if necessary.

ian@lambo:~$ sudo parted /dev/sda7 print

Disk /dev/sda7: 3989MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start   End     Size    File system  Flags
 1      0.00kB  3989MB  3989MB  linux-swap

Information: Don't forget to update /etc/fstab, if necessary.

ian@lambo:~$ sudo parted /dev/sda4 print
Error: Can't have a partition outside the disk!
Information: Don't forget to update /etc/fstab, if necessary.

ian@lambo:~$

---

### Post by ian_o on 2007-12-29
With parted, rescue is for deleted parttions, not adjusting current partitions. I tried using resize and it adjusts the file system, but did not work for the partition itself.

I think i need  a different utility than parted.

---

### Post by tgilber1 on 2007-12-29
I concur that parted is not up to the task to correct your corrupted filesystem.  It sounds like the best way to fix this problem is to do the following:

[LIST=1]
[*]Copy and backup partitions with corrupted tables  (partimage)
[*]Delete corrupted partitions (fdisk)
[*]Recreate partitions with correct boundaries ((fdisk)
[*]Restore backup (partimage)
[*]Reboot
[/LIST]

When you do a backup, You should think twice about using programs that only copy files (e.g., tar, cp, etc.).  These programs do not copy partition information, mbr, etc.  To properly backup a partition, programs like dd and partimage are available.

The problem with dd command it copies the whole partition, even if it is empty.  It does not provide progress indicator and it can be terribly slow.  Partimage overcomes all these obstacles.  Below is a link that explains more about partimage.  Hopefully, this info will help you out.  Good luck!

Reference:  [http://ubuntuguru.wordpress.com/](http://ubuntuguru.wordpress.com/)  #scroll down to the Partimage Rocks - Interesting read

---

### Post by ian_o on 2007-12-29
Whilst copying partitions to another a backup and restoring them may be the only way to correct the problem-  it is a very very sad state of affairs if it is!!

It sounds less work to write my own utility to adjust the two entries in the partition table!!!

There are two entries in the partition table which have incorrect end settings, but no actual 'corrupt partitions'

The first entry is for a primary partition and states the partition is too long. The file system for the partition has the correct length and verifies correctly. The second error is for an extended partition and all the actual partitions again are fine. Two counts that are one cylinder high and there is no tool which will allow me to correct these few bytes without erasing 100 gig of data and copying it back???

---

### Post by tgilber1 on 2007-12-29
> **ian_o said:**
> Whilst copying partitions to another a backup and restoring them may be the only way to correct the problem-  it is a very very sad state of affairs if it is!!

It sounds less work to write my own utility to adjust the two entries in the partition table!!!

There are two entries in the partition table which have incorrect end settings, but no actual 'corrupt partitions'

The first entry is for a primary partition and states the partition is too long. The file system for the partition has the correct length and verifies correctly. The second error is for an extended partition and all the actual partitions again are fine. Two counts that are one cylinder high and there is no tool which will allow me to correct these few bytes without erasing 100 gig of data and copying it back???

I've run out of options to do it any other way.  However, have you taken a look at using the expert mode of fdisk?

---


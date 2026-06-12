---
title: "Windows update deleted my Ubuntu partitions so broke Grub boot"
date: 2018-01-08
forum: Installation &amp; Upgrades
---

### Post by andy.r2 on 2018-01-08
Windows updated over the weekend.  On re-start, the laptop went into GRUB rescue mode.
/dev/sda1, /dev/sda2 and /dev/sda3 are NTFS partions 
sda4 is an extended partition full of empty space where my Ubuntu partitions were.  I can't remember how many partitions there were.  
I've tried the parted rescue which doesn't find anything.  I get the impression reading around that the start and end must be reasonable guesses to the actual start/end of the partitions that are being looked for.  I find it curious that scanning 250Gb takes just a few seconds and no longer than a much smaller part of the drive selected in the start/end range.
Will it help to get the start/end nearer the actual positions?  If so, how might I find them?
Many thanks!

---

### Post by oldfred on 2018-01-08
If parted rescue is not working have you tried testdisk?
If just one partition, then it would be just a couple of sectors different than start & end of extended partition.
       
backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print 

    
BIOS/MBR versions of Windows have had this bug for years. It just forgets to write Linux partitions back into partition table.
 Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545) 


[https://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](https://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by andy.r2 on 2018-01-08
Hi oldfred, many thanks for your response:D

I have read a number of your posts previously, as you've said, back to 2011!

I am not sure there is just one partion, I really cannot remember.  I think the default installer option recommends a swap partion also and if it does I would have gone with it (although I've got loads of RAM so don't use SWAP much).  Would the swap partition typically be numerically before the ubuntu boot drive?  I can see from GRUB rescue using SET that boot partition is dev/sda5.

Yes, I've tried testdisk, in both the regular and deep scans with nothing found

do you know how accurate the number of sectors should be for parted rescue to be successful?  

I've just come across gpart  which I am running now...

---

### Post by oldfred on 2018-01-08
Have not used parted rescue, but those that have seem to have had no issues as long as sectors were inside search area.
Swap typically was last partition or at end of extended or right of as looking with gparted. And if you have lots of RAM, it would have made swap also large (often too large).

I have used photorec to recover data. It takes a long time, only recovers by type and you have to have a large drive to copy recovered data into.
My case I only really wanted .txt files & it found those. But those are my notes from here, you may have noted that many of my reference answers are the same or similar. :)
And it also found all the old, deleted  copies. I did have a backup that was not too current and had to sort files and then compare to backup file and see if I could tell if I added info or in some cases deleted data. Took forever.
Learned to backup more often.

 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by andy.r2 on 2018-01-16
I quite agree about regular backups.  My backup scheme clearly wasn't frequent enough...I have photorec running as I type....  Nothing found yet....

I've not been able to find the ext4 partition within the extended partition 4.  How many sectors after the start of the extended partition will the ubuntu partition start?

No dual boot system for me once I've got this sorted.

---

### Post by westie457 on 2018-01-16
Hi, forget about using photorec, you will have lots of files recovered with names that will be of no use. All found recovered files will be listed with a number and an extension (examples, 10754.txt, 2468.mp3) which is a nightmare to sort out.

Testdisk will find all partitions on the hard drive - even ones that have been deleted in the past - giving you start and end sectors for each. After running a 'Deeper Search' go through the list of found partitions marking each one you want to recover including all Windows partitions. Set them as (P)rimary or (L)ogical as necessary. You will be informed of any that cannot be recovered. When you are happy with the results tab through to 'Write' the changes to drive, follow the prompts.

With Testdisk you can also have the chance to copy found files within a partition to another location - preferably an external drive or USB stick.
If I remember correctly the copy to location must be connected to the machine and mounted before running testdisk so you can specify the right location.

Hope this helps.

---

### Post by andy.r2 on 2018-01-16
Hi Westie457, as per response #3, I have tried testdisk but it hasn&#8217;t found the partition. I don&#8217;t know if this is due to it being a logical drive?

---

### Post by westie457 on 2018-01-16
Missing/deleted partitions will only show in testdisk after a Deeper Search. The partitions showing after a Quick Search will be those that are available now. 

Post the testdisk output after a deeper search please, also post the output of ```
sudo parted -l #the l is a lower-case L not a 1 or a I
```

Could you post the requested info between [code] tags for easier reading please.

---

### Post by andy.r2 on 2018-01-17
```
Model: ATA Crucial_CT525MX3 (scsi)
Disk /dev/sda: 525GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  525MB  524MB  primary   ntfs         boot
 2      525MB   275GB  274GB  primary   ntfs
 3      275GB   276GB  505MB  primary   ntfs         diag
 4      276GB   525GB  250GB  extended


Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel? i                                                          
Model:   (scsi)
Disk /dev/sdb: 62.1GB
Sector size (logical/physical): 2048B/512B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      1660MB  1662MB  2490kB               EFI


Model: ST310005 28AS (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary               boot

```

SDA is drive of interestand where I would expect to find my ubuntu partion(s), SDB is USB boot drive and SDC is external backup

Testdisk after a deeper scan gives:

```
TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 525 GB / 489 GiB - CHS 63841 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0  32 33    63 221 30    1024000
 2 P HPFS - NTFS             63 221 31 33435 159  4  536117248
 3 P HPFS - NTFS          33435 159  5 33497  17 56     987136


>[  Quit  ]  [ Write  ]
                              Return to main menu
```

Any suggestions appreciated!

---

### Post by oldfred on 2018-01-17
You can force a partition into partition table, but need to know if sda5 was swap and sda6 ext4 or vice-versa. And if only one ext4 partition.
If ext4 was first logical partition, you just make extended then new ext4 logical partition, ignoring swap as it was probably random data or zeros.
Then see if repairs on the "new" ext4 partition work.

Post the output of the two commands in post #2.

 Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

### Post by andy.r2 on 2018-01-18
sfdisk gives:

```
label: dos
label-id: 0x1628c61f
device: /dev/sda
unit: sectors

/dev/sda1 : start=        2048, size=     1024000, type=7, bootable
/dev/sda2 : start=     1026048, size=   536115983, type=7
/dev/sda3 : start=   537143296, size=      987136, type=27
/dev/sda4 : start=   538132478, size=   487477250, type=5
```

and parted gives
```
Model: ATA Crucial_CT525MX3 (scsi)
Disk /dev/sda: 1025610768s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start       End          Size        Type      File system  Flags
 1      2048s       1026047s     1024000s    primary   ntfs         boot
 2      1026048s    537142030s   536115983s  primary   ntfs
 3      537143296s  538130431s   987136s     primary   ntfs         diag
 4      538132478s  1025609727s  487477250s  extended
```

From the GRUB rescue set, I can see that it was looking to SDA5 to boot Ubuntu, so that must be my ext4 ubuntu partition.  

I can guess about SDA5 parittion size, but how would I then go about repairing it?  I'll take a closer look in the threads you link to.

---

### Post by oldfred on 2018-01-18
Manually edit a copy of the sfdisk output with a new line for sda5. Start must be two sectors after start of extended. If all of extended then size is two sectors less also. Linux type is 83. 
Then add that back into your partition table  and see if you can read or run e2fsck on partition.

Keep original copy of sfdisk output just in case you have to restore it.

---

### Post by andy.r2 on 2018-01-19
```
TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 525 GB / 489 GiB - CHS 63841 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0  32 33    63 221 30    1024000
 2 P HPFS - NTFS             63 221 31 33435 138 62  536115983
 3 P Windows RE(store)    33435 159  5 33497  17 56     987136
 4 E extended             33497  50 24 63841  64 31  487477250
No ext2, JFS, Reiser, cramfs or XFS marker
 5 L Linux                33497  50 26 63841  64 29  487477246
 5 L Linux                33497  50 26 63841  64 29  487477246
```

I've no idea what the missing marker is, or how I might correct.  why would SDA5 be listed twice at this part of testdisk?  When I complete the deep scan, SDA4 and SDA5 are not listed.

---

### Post by andy.r2 on 2018-01-19
And here it is in sectors:
```
Model: ATA Crucial_CT525MX3 (scsi)
Disk /dev/sda: 1025610768s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start       End          Size        Type      File system  Flags
 1      2048s       1026047s     1024000s    primary   ntfs         boot
 2      1026048s    537142030s   536115983s  primary   ntfs
 3      537143296s  538130431s   987136s     primary   ntfs         diag
 4      538132478s  1025609727s  487477250s  extended
 5      538132480s  1025609725s  487477246s  logical
```

---

### Post by oldfred on 2018-01-19
Testdisk often picks up similar partitions, as every change even minor ones may be there to find. But do not understand why two identical ones?
But when restoring from testdisk you have to pick non-overlapping partitions to restore, or not part of an old configuration and part newer where they may overlap.

So is partition there and can you see it.

The extended partition is not formatted. So I think it is just a warning that it cannot find format info, which for extended is correct.
It used to be that testdisk did not even show extended partition, but all logical partitions would then be inside it when done.

---


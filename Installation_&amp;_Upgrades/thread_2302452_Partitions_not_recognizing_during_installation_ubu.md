---
title: "Partitions not recognizing during installation ubuntu 14.04"
date: 2015-11-10
forum: Installation &amp; Upgrades
---

### Post by vikram8 on 2015-11-10
I'm trying to install ubuntu 14.04 in my old p4 pc by removing windows ... But in installation typ window nd its not give three options instead of that asking for installing bt not displaying any partition... 

I hv two partitions nd i dont want to do any thing with my other partion because there ary many important stuff stored nd i can take back up... I'm already tried deleting primary parition(in which windows installed)  nd making new ome bt it didnt help....

Plz help me gyz...

---

### Post by yancek on 2015-11-10
To start with to get a little information, boot the Ubuntu installation medium and open a terminal.  Once in the terminal type:  sudo fdisk -l(Lower Case Letter L in the Command) and post the output here.  It will show drive/partition information.  Which installation option did you select?

---

### Post by ajgreeny on 2015-11-10
To see the partitions available at installation you must choose the "**Something Else**" option when it gets to that stage.  The window will refresh and show a list of partitions in the disk or disks in the computer.

---

### Post by vikram8 on 2015-11-10
There is no option come for something else... Thats the problem...

---

### Post by vikram8 on 2015-11-10
> **yancek said:**
> To start with to get a little information, boot the Ubuntu installation medium and open a terminal.  Once in the terminal type:  sudo fdisk -l(Lower Case Letter L in the Command) and post the output here.  It will show drive/partition information.  Which installation option did you select?

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeb64eb64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    b  W95 FAT32
/dev/sda2          206848    51195903    25494528    7  HPFS/NTFS/exFAT
/dev/sda3        51196320   160060319    54432000    f  W95 Ext'd (LBA)
/dev/sda5        51196383   160060319    54431968+   7  HPFS/NTFS/&#1108;×FAT

No option came for selecting installation.... Directly goes to selecting partition for installing

---

### Post by vikram8 on 2015-11-10
I'm using lubuntu its becase of that ?

---

### Post by yancek on 2015-11-11
> I'm using lubuntu its becase of that ? 		

No.  Lubuntu uses the same installer as Ubuntu.  You should see a "Preparing to Install Lubuntu" screen which tells you how much drive space you need to install Lubuntu.  The next screen would be the Installation Type window with the options.  Your fdisk output shows that the entire drive is used by your various windows partitions so there is no disk space on which to install Lubuntu.

What you could do is shrink the windows partition, probably sda2 and create another partition out of that space while installing Lubuntu and format it with a Linux filesystem.  If you have a recent version of windows, post xp, you should do this with the Disk Management tool in windows, reboot to make sure it still works and probably run chkdsk.

If you shrink the partition (actually you never indicate which windows you have??) and still don't get the options then you probably have a bad iso or burn of Lubuntu.

---

### Post by vikram8 on 2015-11-11
I tried by deleting nd formatting primary windows drive i do it with windows dvd bt nothing happed even tried with formating ubuntu live try bt its not able to format or making new drive (ext4) with ubuntu live try ... Now i'm downloading ubuntu iso hope it work....

I delete that drive nd start installing lubuntu bt same thing happen no option i think prob. In my iso ...

Btw i'm using win7...

---

### Post by yancek on 2015-11-11
Windows 7 has Disk Management and you should be able to use it to shrink one of your partitions to make room for Lubuntu.
Did you do an md5 checksum on the Lubuntu iso to verify the download?

---

### Post by vikram8 on 2015-11-11
No i didnt do check...i said i completely deleted windows partition and tried bt same result... Whatever i'm downloading ubuntu now hope that work ...

---

### Post by vikram8 on 2015-11-14
I'm trying to install Ubuntu/Lubuntu 32bit 14.04 in my old P4 PC in place of windows7 bt its not recognizing my any partition even not showing three option. Directly going to installation page. I DON'T WANT TO FORMAT MY OTHER DRIVE BECAUSE THERE IMP. STUFF STORED AND I'M UNABLE TO TAKE BACKUP.

fdisk -l output i dont Know About These-

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeb64eb64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    b  W95 FAT32
/dev/sda2          206848    51195903    25494528    7  HPFS/NTFS/exFAT
/dev/sda3        51196320   160060319    54432000    f  W95 Ext'd (LBA)
/dev/sda5        51196383   160060319    54431968+   7  HPFS/NTFS/exFAT

What I'm Already Tried-

1) Tried formatting C drive with LIVE TRY but didnt work.
2) I Deleted C drive with windows DVD and then tried making new ext4 drive with LIVE TRY but its not able to creat new drive.
3) Also tried with installation setup to make new drive but same result its not able to find space.
4) Then I make a new drive with win7 dvd but its also not able to find it.
5) Also check md5 sum
Plz Help Me Guyz

---

### Post by mörgæs on 2015-11-14
Are you able to run Gparted from a live boot of Lubuntu?

---

### Post by howefield on 2015-11-14
Duplicate threads merged.

---

### Post by vikram8 on 2015-11-14
> **mörgæs said:**
> Are you able to run Gparted from a live boot of Lubuntu?

I actually dnt knw abt which gparted are you talking about... But yes i go to partitioning option from lubuntu live dvd and try to formating or creating new partition but didnt work its not able to format or creat new drive...

---

### Post by vikram8 on 2015-11-14
> **howefield said:**
> Duplicate threads merged.

Yep i thaught reposting may help...

---

### Post by Bashing-om on 2015-11-14
vikram8; Hello;

Allow me to poke my nose into this.
As yancek advises, you have all 4 primary partitions taken up with Windows. In the msdos partitioning scheme there is a addressing limit of 4 partitions . We must make provisions - if you want to dual boot - for the 'buntu install .
One way to accomplish this is to make up a 'recovery' disk for  Windows and delete that partition on the hard drive . Shrink the Windows' operating system down, and add that space to the unallocated space from the deleted recovery partition.

Once you have contiguous unallocated space .. the installer will be happy to install 'buntu . 

[INDENT][INDENT]just my 2 pounds worth
[/INDENT][/INDENT]

---

### Post by vikram8 on 2015-11-15
> **Bashing-om said:**
> vikram8; Hello;

Allow me to poke my nose into this.
As yancek advises, you have all 4 primary partitions taken up with Windows. In the msdos partitioning scheme there is a addressing limit of 4 partitions . We must make provisions - if you want to dual boot - for the 'buntu install .
One way to accomplish this is to make up a 'recovery' disk for  Windows and delete that partition on the hard drive . Shrink the Windows' operating system down, and add that space to the unallocated space from the deleted recovery partition.

Once you have contiguous unallocated space .. the installer will be happy to install 'buntu . 

[INDENT][INDENT]just my 2 pounds worth
[/INDENT][/INDENT]

Actually i deleted my Windows partition then tried with unallocated unit but installation setup didnt detect that space and also not able to creat new partition with live try...

And i dont want dual boot i want to use Ubuntu in place of windows

---

### Post by Bashing-om on 2015-11-15
vikram8; Ouch !!

OK. single install, ubuntu . Installer being stubborn.
Next up is to check and see about meta data on that hard drive confusing the installer.
what returns:
```

sudo wipefs /dev/sda

```
Note that you should not just trust me that that command is safe (even though it is), you should run "man wipefs" and confirm for yourself that the command will just list all visible filesystems (and in this case, RAID metadata) and their offsets.
'sda' represents that 1st hard drive, if there are other drives ((2nd == sdb) adjust the target device as required .

As there must be a reason, must be a cause .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by vikram8 on 2015-11-15
> **Bashing-om said:**
> vikram8; Ouch !!

OK. single install, ubuntu . Installer being stubborn.
Next up is to check and see about meta data on that hard drive confusing the installer.
what returns:
```

sudo wipefs /dev/sda

```
Note that you should not just trust me that that command is safe (even though it is), you should run "man wipefs" and confirm for yourself that the command will just list all visible filesystems (and in this case, RAID metadata) and their offsets.
'sda' represents that 1st hard drive, if there are other drives ((2nd == sdb) adjust the target device as required .

As there must be a reason, must be a cause .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]



Ok... If i use sda2(26 gb partition of my windows correct me  if i'm wrong) instead sda i think its more safe because as said i dont want to erase my data in ither drive.

I search about that command and i wanna ask you wiping signature is safe ? And what if i accidentally wipe signature of my other drive there any chance to lose data?

---

### Post by Bashing-om on 2015-11-15
vikram8; Well ..

It is always advised to check and understand any command !
All I can say here is that the command is safe . but do as advised and read for yourself 
```

man wipefs

```
You want to look at the devices .. as in sda not a partition .
My result:
```

sysop@1404mini:~$ sudo wipefs /dev/sda
[sudo] password for sysop: 
wipefs: WARNING: /dev/sda: appears to contain 'dos' partition table
sysop@1404mini:~$

```
Where formerly I did have a raid setup; Reverted to Master Boot Record (dos) . 

[INDENT][INDENT]buy a man a fish ............
[/INDENT][/INDENT]

---


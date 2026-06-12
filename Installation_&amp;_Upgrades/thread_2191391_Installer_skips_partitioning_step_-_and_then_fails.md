---
title: "Installer skips partitioning step - and then fails because no root mount point"
date: 2013-12-02
forum: Installation &amp; Upgrades
---

### Post by Computersleuth2 on 2013-12-02
I have an HP Pavilion a1000y with a 2.6 GHz Celeron CPU and 1 GB of ram.  The disk interface is EIDE, and is self-configured by the BIOS as UDMA-5.  I partitioned the disk using GParted before I went to install Ubuntu.  I could not find anything with GParted that would allow me to set a mount point for a partition.

When I attempted to install Linux Mint, and then a bit later Ubuntu Studio, the installer skipped past (I think it was) step 3 and jumped from step 2 to 4.  If I remember correctly, step 3 gives you the opportunity to partition the drive and to set mount points for each partition.  When the installer got to step 4, there were no partitions listed . . . I nonetheless hit the 'Install' button (or whatever it was that would continue with the installation) to see if it would continue.  Instead, I got a message back saying it could not find a root mount point.

After seeing this fail multiple times, with both Mint and Studio, I attempted a re-install of Windows XP - this went without a hitch.

I see this as a bug, but I hold no hope that it will be fixed - after all, the hardware is old.  But I nonetheless wanted to document this so that others might find this without putting out the effort to fight this.

That said, if anyone has a fix to this, I would be greatly appreciative.  Thanks.

- Dave

---

### Post by oldfred on 2013-12-02
If you partition in advance you still have to use Something Else or manual install.
And you should get this screen, depending on version or something very similar.

---

### Post by Computersleuth2 on 2013-12-02
> **oldfred said:**
> If you partition in advance you still have to use Something Else or manual install.
And you should get this screen, depending on version or something very similar.

Thanks for responding.

I did not get the screen that said "This computer currently has multiple operating systems on it . . .".  Even when XP was already loaded.

The other screen with the list of partitions, etc . . . I got that screen, but there was no bar across the top and the list was empty.  Down at the bottom, where it said "Device for bootloader installation," it had one item in the drop-down box:  "/dev/sda".

This entire issue is weird for several reasons:  1) the fact that XP is loaded says that the MBR and partition table exists, and they're valid.  2) GParted (by itself) properly does the partitioning (even though the installer doesn't).  3) because the list of partitions is empty, this suggests the installer appears to not recognize the disk/disk interface, or the partition table is alien to it (unlikely).

Now, I purchased this disk as a used item.  The woman at the computer shop said she had reformatted it.  I put it through all the tests supported from the machine's BIOS - these tests completed without error.  I checked the jumper settings (it's a WD Caviar); they are set as specified by WDC.

Your thoughts?

Please note that the installer behaves the same whether XP is loaded or if no other OS is loaded.

---

### Post by oldfred on 2013-12-02
If it was reformatted was it RAID or gpt? I thought gparted had issues with those also as they can leave meta-data on a drive that some tools do not see but others do.

If not running RAID you can run this. It will not damage anything unless you real have RAID.
 sudo dmraid -E -r /dev/sda

Post this from live installer.

sudo parted -l

---

### Post by Computersleuth2 on 2013-12-02
Hi oldfred,

Here's my terminal session with the commands you suggested:

mint@mint ~/Desktop $ sudo dmraid -E -r /dev/sda
Do you really want to erase "pdc" ondisk metadata on /dev/sda ? [y/n] :y
mint@mint ~/Desktop $ sudo parted -l
Model: ATA WDC WD400BB-60BN (scsi)
Disk /dev/sda: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  15.7GB  15.7GB  primary   ntfs         boot
 2      15.7GB  40.0GB  24.3GB  extended
 5      15.7GB  40.0GB  24.3GB  logical   ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Invalid partition table - recursive partition on /dev/sr0.         
Ignore/Cancel? I                                                          
Model: TSSTcorp CDW/DVD TS-H492A (scsi)
Disk /dev/sr0: 942MB
Sector size (logical/physical): 2048B/2048B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags


mint@mint ~/Desktop $

*** I'd say the invalid partition table message is particulary interesting . . . this could be the problem . . .

That said, I really don't know what "pdc" ondisk metadata is . . . I'm guessing that's for RAID?

---

### Post by Computersleuth2 on 2013-12-02
Hi oldfred,

This command:  'sudo dmraid -E -r /dev/sda' allowed me to delete the 'pdc' metadata.  Apparently, this data influenced how the installer worked.  Once the pdc metadata was deleted, and then I used GParted to wipe the disk and create a new Partition Table, the installation ran through the problem area.  The installation is currently running and appears to be executing without further problems.

Thanks for your help.

- Dave

---

### Post by oldfred on 2013-12-02
Glad you got it resolved. 

Error message on CD/DVD (sr0) are not important. Install is oversize for CD and with DVD it gets confused. Not sure why.

---


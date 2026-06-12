---
title: "Help: PC freezes after replacing HDD"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by GailHard on 2011-03-26
Hello experts - I hope you can help me with this problem.

I have a PC with Windows XP SP2. It had two HDDs, one (IDE) with partitions C: (boot) and D:, and another (IDE) 200GB disk, E:.

Recently, the second disk caused the system to issue filesystem error messages on boot. I decided to image it to another location on the home LAN, and then to copy the image to a new disk.
So I have used "Live Ubuntu" "ddrescue" to salvage the disk image (with only about several k of error sectors) to another file on an SMB share. 

I then got a new 500 GB SATA HDD, used a "Promise 4302" IDE-to-SATA PCI controller to interface to it, loaded the "Live Ubuntu" and used "ddrescue" to copy the old disk image to the new HDD. (The Ubuntu kernel 2.6 recognized the SATA disk and its "Promise" controller with no problems). So far, all according to instructions.

Now, according to instructions, the next step is to boot the XP system and let it do CHKDISK /F on the new disk. 

The problem is: the computer freezes (hangs) in the initial step of the boot.

I tried to do a "Repair install" using an XP install CD - again the PC freezes after the message: "Inspecting your hardware".

Using the same XP install CD, it tried going into the "XP Recovery console" (in order to do "CHKDISK /F") - again, the PC freezes after "inspecting your hardware".

Booting the same PC from an Ubunbtu Live CD, situation is much better. When Ubuntu boots, it says: "Incomplete multi-sector transfer, Input/output error", but then it continues normally.

lshw says:
Hardware: HP Pavilion A305W, Trigem Glendale motherboard, CPU: Intel Celeron 2.7 GHz
Memory: 2GB DIMM DDR
Storage: IDE Intel 82801 (ICH4)
Logical: /dev/sda 
/dev/sda1 Volume 0: FAT32 5692 MiB, primary fat initialized
/dev/sda2 Volume 1: NTFS 31 GiB, primary ntfs bootable initialized, modified by chkdsk: true, state: dirty, upgrade on mount: true, resize log file: true, mounted on NT4: true
Logical: /dev/sdb
Promise SATA 300 TX4 disk controller, Disk: Size: 186 GiB, Capacity: 465 GiB, Capability: NTFS initialized, modified by chkdsk: true, state: dirty, upgrade on mount: true, resize log file: true, mounted on NT4: true
IDE CDROMs: 0 and 1

Running fdisk -l on /dev/sdb: 
Disk /dev/sdb: 500 GB, 500105249280 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device      Boot Start        End        Blocks        Id  System 
/dev/sdb1           1          60802    488392033   83  Linux
Warning: Partition 1 does not end on cylinder boundary.

I read somewhere that I should change the partition ID from 83 to 0 or 7 (NTFS). But using fdisk (or cfdisk) and changing the partition ID (=type) (and doing "w" - namely: save) - does not actually change the ID.

What to do?

Thanks in advance - GailH

---

### Post by GailHard on 2011-03-31
Here are some new developments:

I had a secondary HDD fail, in a Windows XP SP2 system (disk E).
Booting from "Ubuntu Rescue Remix" live CD, I used ddrescue to image that 200GB disk to a new disk (500 GB SATA HDD), without formatting the new disk first - that's according to ddrescue instructions. 
The new disk uses a "Promise 4302" IDE-to-SATA PCI controller, since the motherboard doesn't have SATA headers.
The Ubuntu kernel 2.6 recognized the SATA disk and its "Promise" controller with no problems. 
So far, all according to instructions. (except that on boot, a little warning crops up: "Incomplete multi-sector transfer, Input/output error"), but then all continues normally.

The problem is, Windows XP hangs at "Inspecting your hardware". Windows Recovery Console hangs at: "NTDETECT is checking your hardware". (Same in Safe Mode). The problem is squarely with the new disk. When I disconnect its SATA cable, XP boots with no problems. When I trick XP like this: disconnect the HDD SATA cable, let XP go through the initial boot, then reconnect the SATA cable: then XP sees the disk, but Computer Management -> Storage Management shows: "unknown partition".

Back to Linux: The restored disk is /dev/sdb.
"parted" says the partition type is "loop", in other words, no partition table.
When I go:
>ls /dev | grep sd 
>sda
>sda1
>sda2
>sdb

There is no sdb1.

What to do? Should I go: "parted mklabel msdos"? I don't want to corrupt the data.

Gparted: when running Gparted, there is a warning sign with /dev/sdb, and when you click on it, it says: "ntfs resize failed to 

check 'dev/sdb1' mount state: no such file or directory"

testdisk says:
"Partition Start End Size in sectors
P NTFS 0 0 24320 238 390715857 1 63 [DISK2_VOL1]
NTFS, 200GB/185GiB"
(DISK2_VOL1 is the original volume name of the restored disk. 200GB it its original size).  _testdisk is able to mount the NTFS file system and browse the directory structure._

lshw says:
Hardware: HP Pavilion A305W, Trigem Glendale motherboard, CPU: Intel Celeron 2.7 GHz
Memory: 2GB DIMM DDR
Storage: IDE Intel 82801 (ICH4)
Logical: /dev/sda 
/dev/sda1 Volume 0: FAT32 5692 MiB, primary fat initialized
/dev/sda2 Volume 1: NTFS 31 GiB, primary ntfs bootable initialized, modified by chkdsk: true, state: dirty, upgrade on mount: true, resize log file: true, mounted on NT4: true
Logical: /dev/sdb
Promise SATA 300 TX4 disk controller, Disk: Size: 186 GiB, Capacity: 465 GiB, Capability: NTFS initialized, modified by chkdsk: true, state: dirty, upgrade on mount: true, resize log file: true, mounted on NT4: true
IDE CDROMs: 0 and 1

Running fdisk -l on /dev/sdb: 
Disk /dev/sdb: 500 GB, 500105249280 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   
Device      Boot Start        End        Blocks        Id  System 
/dev/sdb1           1          60802    488392033   83  Linux
Warning: Partition 1 does not end on cylinder boundary.

What to do? Should I go: "parted mklabel msdos"? I don't want to corrupt the data.

Thanks in advance - GailH

---

### Post by Hedgehog1 on 2011-03-31
When a SATA drive is added to an all IDE system, the boot order is often re-arranged (and this causes a fair amount of confusion).

So we can help you solve this, please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

---

### Post by GailHard on 2011-04-01
> **Hedgehog1 said:**
> When a SATA drive is added to an all IDE system, the boot order is often re-arranged (and this causes a fair amount of confusion).
So we can help you solve this, please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) Follow the instruction on the website and post the results here.
***The Hedge ***:KS
Like I said in the second post, by doing a little trick (disconnecting the SATA cable and reconnecting after the XP splash screen is on) the PC boots in XP fine.

The problem now is, seems that using ddrescue, the disk was not restored correctly  (maybe because the Partition ID is 83 and not 07?) When I go: Computer Management -> Storage Management, it shows: Disk1 "unknown partition".

I will try the "bootinfoscript", but I think the main issue is: how to tweak the partition table (or "disk label") so that XP likes it. (And as I said in the original post, maybe there is no partition table at present, so I have to create one).

---

### Post by Hedgehog1 on 2011-04-01
Gail,

I did a ddresuce about 4 weeks ago. I copied the contents of a 640gig drive (with a dual boot of Win7 and Ubuntu) onto a 1tb drive. Once the copy was complete, I unplugged the 640 and left the 1tb connected.

The drive booted, and all data (including the partition map) was there.  It was (as far as the PC was concerned) the same drive, it just had extra unallocated space at the end (and no more bad sectors).  Once the new drive booted, I physically removed the 640 gig drive and mounted the 1tb drive in it's place.  I am typing from this system now.

I know this simple set of steps works.  Both drives on the same system, boot off of USB/CD, and do ddrescue (*and go watch TV for a while*).

The one difference between our situations is I went SATA to SATA, and you went IDE to SATA. *You should see what looks like you old drive.  You did disconnect the old drive after the copy, right? If you don't bad things happen that confuse OSes when both 'identical' drives are still connected.*

***The Hedge***

:KS

---

### Post by GailHard on 2011-04-01
> **Hedgehog1 said:**
> I did a ddresuce about 4 weeks ago. I copied the contents of a 640gig drive (with a dual boot of Win7 and Ubuntu) onto a 1tb drive. 
...*** The Hedge*** :KSIn my case, the target disk was over a network SMB share, on a Dlink-323 NAS, and once I've installed the new SATA disk, I've used ddrescue again, to restore the disk back (this is ok according to ddrescue instructions). Each way it took 10 hours, due to LAN and NAS performance. So I am reluctant to repeat this exercise.

Note that testdisk is able to mount the NTFS file system which is on the restored disk and also browse the directory structure. But lshw does not list a /dev/sdb1 (partition), and neither does Gparted. 

Therefore, my conclusion is that we need to either fix the partition table, or create a new one. Can you direct me to a place which explains how to do that?

---

### Post by Hedgehog1 on 2011-04-01
The test disk wiki says that:

> TestDisk can
 * Fix partition table, recover deleted partition
...

I am guessing here - but putting an empty partition map on the disk, and then using TestDisk to 'recover' your restored partition (that looks deleted because it not in the map) may work.

I have not done this before, however, so take this 'best guess' at face value.

***The Hedge***

:KS

---

### Post by GailHard on 2011-04-01
> **Hedgehog1 said:**
> So we can help you solve this, please boot off the LiveCD/LiveUSB, select 'TRY', and then: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.
***The Hedge ***:KSI ran boot_info_script. Here are the interesting results for the ddisk in question:
______________________________________________________________________________
sda1: _________________________________________________________________________
 
File system: vfat
Boot sector type: Recovery:Fat 32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM
 
sda2: _________________________________________________________________________
 
File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM
 
sdb: _________________________________________________________________________
 
File system: ntfs
Boot sector type: Windows XP
Boot sector info: According to the info in the boot sector, sdb starts at sector 63. But according to the info from fdisk, sdb starts at sector 0. 
According to the info in the boot sector, sdb has 390715856 sectors, but according to the info from fdisk, it has 976773168 sectors.
Operating System:
Boot files/dirs: 
______________________________________________________________________________
 
Apparently the boot sector holds the data for the original disk (200 GB), while fdisk gives the data for the disk it was restored to (500 GB).
But what about the partition table?

---

### Post by Hedgehog1 on 2011-04-02
> File system: ntfs
Boot sector type: Windows XP
Boot sector info: According to the info in the boot sector, sdb starts at sector 63. But according to the info from fdisk, sdb starts at sector 0. 
According to the info in the boot sector, sdb has 390715856 sectors, but according to the info from fdisk, it has 976773168 sectors.
Operating System:
Boot files/dirs: 

Thanks for running the script.  This actually tells us what is wrong:

For an MBR partitioned disk, there is a reserved a block of space at the beginning of the disk for the partition map. This is normally (as I recall) sectors 0-62.  The first partition should begin no sooner than sector 63.

On your disk, you restored your data starting at sector 0 because you did not have an MBR partition map defined.  Essentially, you dumped your data onto the space needed for the MBR.

In short: This disk is not viable in it's current state. :(

You will need to start over, first by creating an MBR, and then restoring your data on the drive again outside the MBR area.


***The Hedge***

:KS

---

### Post by LostFarmer on 2011-04-02
To verify 'Hedgehog1' conclusion, I think it very likely correct.

From a terminal run ```
dd if=dev/sdb bs=512 count=1 | hexdump
```  will need to run as root.

Look at both sites , near bottom of pages titled " Location of Error messages" look at right side there is the error messages.  Does yours look like the 1st "MBR's" or 2nd "Volume Boot Record" link ?  The first is correct and 2nd says Hedgebog1 is correct.
[http://thestarman.pcministry.com/asm/mbr/Win2kmbr.htm](http://thestarman.pcministry.com/asm/mbr/Win2kmbr.htm)
[http://thestarman.pcministry.com/asm/mbr/NTFSBR.htm](http://thestarman.pcministry.com/asm/mbr/NTFSBR.htm)

[CENTER]
[FONT=Times New Roman][SIZE=6][/SIZE][/FONT]


[FONT=Times New Roman][SIZE=6][/SIZE][/FONT][/CENTER]

---

### Post by GailHard on 2011-04-05
LostFarmer: The 1st sector is indeed NTFS, not MBR. I attached it at the end of this post. 
 
But this raises these questions:
 
1. Does every disk have to have the MBR, 64 sectors and only then start the data partition? Note that the original disk (F:) did not have a bootable partition.
 
2. The disk was cloned (salvaged) with ddrescue. ddrescue is supposed to clone the disk "strictly raw". If the answer to the 1st question is affirmative, then the restored disk should have had the "canoncial" MBR, and not start with the NTFS record.
 
3. Another interesting point: I can mount the disk like this: mount -t ntfs /dev/sdb, then I can browse the file system directories and see the files.
 
_Output of: hexdump -C -n 512 /dev/sdb_:
 
```
 
[FONT=Courier New][SIZE=2]00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]00000010  00 00 00 00 00 f8 00 00  3f 00 f0 00 3f 00 00 00  |........?...?...|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]00000020  00 00 00 00 80 00 80 00  d0 d9 49 17 00 00 00 00  |..........I.....|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]00000030  00 00 0c 00 00 00 00 00  9d 9d 74 01 00 00 00 00  |..........t.....|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]00000040  f6 00 00 00 01 00 00 00  50 5c 04 60 99 04 60 3c  |........P\.`..`<|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|[/SIZE][/FONT]
[SIZE=2][FONT=Courier New]00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  [/FONT][FONT=Courier New]|...s......f...@f[/FONT][FONT=Courier New]|[/FONT][/SIZE]
[FONT=Courier New][SIZE=2]00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 80 46  |mpressed...Pre.F|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]000001d0  c3 ff 74 22 dd ff 41 6c  74 2b 44 65 6c 20 00 00  |..t"..Alt+Del ..|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]00000200[/SIZE][/FONT]
 

```

---

### Post by GailHard on 2011-04-05
> **Hedgehog1 said:**
> On your disk, you restored your data starting at sector 0 because you did not have an MBR partition map defined. Essentially, you dumped your data onto the space needed for the MBR.
... You will need to start over, first by creating an MBR, and then restoring your data on the drive again outside the MBR area. ***The Hedge ***:KSHedgehog1: Can I move the partition to sector 63, (using dd or Gparted), then create the MBR and point it to the partition? (This can save a lot of time)

---

### Post by Hedgehog1 on 2011-04-05
> **GailHard said:**
> Hedgehog1: Can I move the partition to sector 63, (using dd or Gparted), then create the MBR and point it to the partition? (This can save a lot of time)
 
Gail - I am inclined to call you 'Alice' as this gets curiouser and curiouser.
 
You absolutely can move the data on the disk over using gparted. Two things to take note of:
 
* gparted can take a very long time moving NTFS partitons, and sometime messes them up if they are badly fragmented.
 
* I think that gparted will move in 1 meg increments. That is fine, as long as the data is out of the way of the partition map that little bit of disk space 'wasted' is harmless.
 
**[SIZE=3]EDIT: I had incorrect identified this as a MBR partiton table, it is in fact NTFS volumn table![/SIZE]**
 
```
 
[FONT=Courier New][SIZE=2]00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|[/SIZE][/FONT]

```
 
 
 
***The Hedge***
 
:KS

---

### Post by Skapunker on 2011-04-05
> **GailHard said:**
> LostFarmer: The 1st sector is indeed NTFS, not MBR. I attached it at the end of this post. 
 
But this raises these questions:
 
1. Does every disk have to have the MBR, 64 sectors and only then start the data partition? Note that the original disk (F:) did not have a bootable partition.
 
2. The disk was cloned (salvaged) with ddrescue. ddrescue is supposed to clone the disk "strictly raw". If the answer to the 1st question is affirmative, then the restored disk should have had the "canoncial" MBR, and not start with the NTFS record.
 
3. Another interesting point: I can mount the disk like this: mount -t ntfs /dev/sdb, then I can browse the file system directories and see the files.


1. Yes, the MBR is what holds the information about the partition table.  That being gone is the reason your partition does not show up.

2. Since you drive was failing it may not have been able to copy the mbr.

3. This works because instead of using the mbr, you're telling linux it's an ntfs so then it can mount it.

To recover your partition table I would recommend using testdisk since you've already used it.  Just use this [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) guide and have it find your ntfs partition and once it does change the type to primary and have it write the new partition table.  You should be good after this.  Good luck and let me know how it goes.

---

### Post by Hedgehog1 on 2011-04-05
> **Hedgehog1 said:**
> ...Assuming that this is really from the drive in question, then the MBR just needs to be updated to be told where the partition(s) are.

The **testdisk** function offers that.

> **Skapunker said:**
> ...To recover your partition table I would recommend using testdisk since you've already used it.  Just use this [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) guide and have it find your ntfs partition and once it does change the type to primary and have it write the new partition table.  You should be good after this.  Good luck and let me know how it goes.

I sense a consensus based on the updated information.  Cool.

***The Hedge***

:KS

---

### Post by Skapunker on 2011-04-05
> **Hedgehog1 said:**
> I sense a consensus based on the updated information.  Cool.

***The Hedge***

:KS

Yep, definitely.

---

### Post by LostFarmer on 2011-04-05
Before using 'testdisk' you must move the data by 1 track '63 sectors' .

[Hedgehog1]("http://ubuntuforums.org/member.php?u=1230016") the code posted by [GailHard]("http://ubuntuforums.org/member.php?u=1268847") is of an NTFS Volume Boot Record not of a MBR.  Read the links in my post #10

---

### Post by Skapunker on 2011-04-05
> **LostFarmer said:**
> Before using 'testdisk' you must move the data by 1 track '63 sectors' .

[Hedgehog1]("http://ubuntuforums.org/member.php?u=1230016") the code posted by [GailHard]("http://ubuntuforums.org/member.php?u=1268847") is of an NTFS Volume Boot Record not of a MBR.  Read the links in my post #10

I would recommend not moving anything and just running testdisk to fix it.  Testdisk can fix the missing mbr.  Since Gail imaged the drive using ddrescue the data is where it should be, even if it was not able to copy over the mbr.  Moving the data may just make things worse, take a lot more time, and be unnecessary.

---

### Post by Hedgehog1 on 2011-04-05
So I am still trying to understand here: The NTFS volumne table needs to fall after the MBR partiton map, yes? If that is the case, the data is off by 1 track/63 sectors. It either has to be moved or restored to a location AFTER where them MBR needs to go, right?
 
My little hedgie brain is starting to melt under the strain...
 
This means that the disk SHOULD have had an MBR added first, and then the data restored to the 'right' of that, correct?
 
***The 'boarding on a hard disk crash himself' Hedge***
 
:KS

---

### Post by LostFarmer on 2011-04-05
> So I am still trying to understand here:  The NTFS volumnetable neede to  fall after the MBR partiton map, yes?  If that is the case, the data is  off by 1 track/63 sectors.  it either has to be moved or restored to a  location AFTER where them MBR needs to go, right?  correct , it will not work if left as is. The Partition Table and MBR boot code would over write the Volume data/code.

> This means that the disk SHOULD have had an MBR added first, and then the data restored to the 'right' of that, correct?
   If the hdd is cloned then one does not need to premake a partition, but if one clones the partition then a partition must be made first. That is the way it should work.

added:  If one images lets say sda1 to a file, and then restores the image file to sdb , then one will have this problem. If the image was of sda then restoring it to sdb should work and no pre-made partition table would be needed.  In fact it would be over written by what ever partitions was on sda.

---

### Post by Hedgehog1 on 2011-04-05
> **LostFarmer said:**
> correct , it will not work if left as is. The Partition Table and MBR boot code would over write the Volume data/code.
 
If the hdd is cloned then one does not need to premake a partition, but if one clones the partition then a partition must be made first. That is the way it should work.
 
added: If one images lets say sda1 to a file, and then restores the image file to sdb , then one will have this problem. If the image was of sda then restoring it to sdb should work and no pre-made partition table would be needed. In fact it would be over written by what ever partitions was on sda.
 
So this is why my disk-to-disk copy was just fine a few weeks back - I copied sda to sdb.
 
Gail is suffering because she copied sda1 to sdb. If she had copied sda1 to sdb1, she would have been OK as that would be apples-to-apples (partiton to partition) instead of apples-to-oranges (partition to disk).
 
So she still needs to either move or restore the data to the first partiton location.
 
***The Hedge***
 
:KS
 
*p.s. So the conclusion from posts #9 and #10 were correct, and I got fooled byt the NTFS partion table. I hate it when that happens...*

---

### Post by Skapunker on 2011-04-05
Because of a reply to a thread I had started by Gail I had been assuming that Gail had done something like /sda to /sdb.  If Gail had done something like /sda1 to /sdb like LostFarmer is saying then it would be off.

So we're just making different assumptions, knowing how Gail did the image would help.

I've backed up failing drives using using /sda to /sdb and run into similar issues where the mbr was corrupted, but imaging /sda to /sdb1 could also explain what's going on.

---

### Post by GailHard on 2011-04-05
.

---

### Post by LostFarmer on 2011-04-06
Looks like [GailHard]("http://ubuntuforums.org/member.php?u=1268847") made a post then deleted the data , with the post saying 
> Using "Ubuntu Rescue Remix" live CD, the original ddrescue command was: from that /dev/sdb _(not sdb1)_ to a _file_, on a networked NAS device (DNS-323) which I had mounted using smbmount. 
   

[GailHard]("http://ubuntuforums.org/member.php?u=1268847")  did you perhaps on my post #10 type in the dd command wrong and used 'if=\dev\hdb1' vice 'if=\dev\hdb'  ?  if so that can explain the false problem.  (I did have to look back and be sure I did not make the typo, that would have been a very possibility.)

 I do not know how ddrescue works when it finds a bad sector but would think it would write 0's in that spot  in the output file not just shrink the file size.

---

### Post by GailHard on 2011-04-06
> **LostFarmer said:**
> [GailHard]("http://ubuntuforums.org/member.php?u=1268847") did you perhaps on my post #10 type in the dd command wrong and used 'if=\dev\hdb1' vice 'if=\dev\hdb' ? if so that can explain the false problem.Guys, thank you for your continued attention to this issue.
 
I do not remember if in my original ddrescue command I've used /dev/sdb, or was it /dev/sdb1.
 
Here's what I'm going to do. In WinXP, I will re-format the new 500GB disk (the one which carries now the restored file) so it will have a good MBR and partition table, and then I will re-restore the partition from the networked file using a ddrescue restore-style command.
 
The problem is, as I mentioned in the beginning of this thread, it seems that Windows XP can't access that disk (chksdk returns the error: "cannot access that disk). Also, in the "Storage Management" console, you do see the disk, but "Format" is greyed out.
I will report back in a day or two.

---

### Post by Skapunker on 2011-04-07
Try using fdisk and/or gparted from a live cd to format it instead.  Then once you have the drive formatted instead of using ddrescue again since you have an image of your drive and just need the data mount the image using ```
mount -t ntfs -o loop image
``` (this should work since you said you were able to mount the drive using ```
mount -t ntfs /dev/sdb
``` and browse the files but we may have to use mmls to find and then specify the offset for the partition).  Then you can just copy the data from the image to your newly formatted drive.

---

### Post by GailHard on 2011-04-07
[SIZE=2]OK guys, it seems that the XP boot problem needs to be taken care of first.[/SIZE]
 
[SIZE=2]Let's call the boot disk "Disk0" and the secondary disk: "Disk1". This entire thread deals with Disk1. [/SIZE]
[SIZE=2]Disk0 is the boot disk having the boot partition, and it's working fine. Disk0 is an IDE disk: master, and the old Disk1 [/SIZE][SIZE=2]was slave. (The old Disk1 had problems, so I've replaced it with a new SATA disk, using a "Promise 300" PCI controller).[/SIZE]
[SIZE=2]Like I said in the beginning of this thread, I had the problem that when the _new_ Disk1 is present in the PC, Windows XP [/SIZE][SIZE=2]hangs during the first stage of boot ("Inspecting your hardware"). Linux does not have a problem booting.[/SIZE]
[SIZE=2](My conclusion: probably something in connection with the BIOS, since I read somewhere that Windows makes extensive use of the [/SIZE][SIZE=2]BIOS, and Linux - much less). [/SIZE]
[SIZE=2]I assumed that XP refused to boot because it didn't like the partition table or MBR on disk1. So here's what I did:[/SIZE]
[SIZE=2]1. Turn on the PC. You see a message that the PCI controller for Disk1 is loading its own on-card BIOS, and identifies [/SIZE][SIZE=2]Disk1. (Note: if I don't connect Disk1 at this stage, the SATA PCI controller says: "No disks found", and doesn't load its [/SIZE][SIZE=2]own BIOS).[/SIZE]
[SIZE=2]2. Disconnect the SATA cable from Disk1. (Note: if I don't disconnect Disk1 at this stage, Win XP hangs at "Inspecting [/SIZE][SIZE=2]your hardware").[/SIZE]
[SIZE=2]3. Windows XP splash screen shows up.[/SIZE]
[SIZE=2]4. Reconnect the SATA cable for Disk1.[/SIZE]
[SIZE=2]5. Windows XP boots and I log in.[/SIZE]
[SIZE=2]I can see Disk1 fine. I then went into: Computer Management -> Storage management -> Disk Management, deleted [/SIZE][SIZE=2]the partitions on Disk1, and created an NTFS partition. It's now "Drive F:".[/SIZE]
 
[SIZE=2]So now I'd like to restore the old Disk1 image into the new Disk1.[/SIZE]
[SIZE=2]The problem is: when I reboot the machine, XP still hangs at "inspecting your hardware". (Before starting to load any [/SIZE][SIZE=2]drivers). So the assumption above (that XP [SIZE=2]hangs on boot due to a bad MBR on Disk1) is incorrect; [/SIZE]even if I successsfully restore Disk1, then XP will still hang on boot[/SIZE][SIZE=2]. This problem needs to be solved first.[/SIZE]
 
[SIZE=2]Do you have any ideas? I read somewhere that "resetting the CMOS" (what's that?) may help. [/SIZE]
[SIZE=2]Remember also that when I fool XP's first stage by going through steps 1 thru 5 above, XP does boot normally.[/SIZE]

---

### Post by LostFarmer on 2011-04-07
Due to the problem is a XP hardware problem , I would suggest the best bet is to use a XP forum help.
Some that I do look at :
[http://www.computing.net/](http://www.computing.net/)
[http://www.windowsbbs.com/](http://www.windowsbbs.com/)

My self know not a thing about SATA or the add in card.  You could try resetting the BIOS/CMOS, a long shot. There may be a jumper to move or take out the battery for about 10min or so.  Be sure when you are messing inside of comp to remove the power cord not just turn it off.

> [SIZE=2] "resetting the CMOS"[/SIZE] just reread, look in the comp manual to see how it should be done.  You might also try changing the IDE hdd connection from Primary IDE connecter  to secondary IDE connecter or other way around.  Have no idea if any of the above may/not work.

---

### Post by Skapunker on 2011-04-08
Resetting the cmos shouldn't make any difference.  It could be an mbr issue with disk0, but I think it's most likely disk1 is still causing the issue.  Try using fdisk on Ubuntu to completely delete the partitions and create a new one, instead of using Windows.  I've had Windows still have issues with a drive that was corrupted even after formatting, and using fdisk usually fixes it.  It may not make much sense, but it won't take long to try.  If you don't know how to use fdisk at about the middle of the first post this page [http://ubuntuforums.org/showthread.php?t=282018]("http://ubuntuforums.org/showthread.php?t=282018") has a good quick guide on it.

---

### Post by GailHard on 2011-04-14
After doing much research, reading many hardware posts, I've reached the conclusion that the problem lies with the BIOS (Phoenix 3.24). It does not identify the disk which is driven by the PCI-SATA controller. It causes the computer to hang at the initial stage of the boot (before loading any drivers).

There are ways to tweak BIOS'es and fix this, but it seems that  the Phoenix 3.24 (dated 2003) is not customizable enough to enable that. (It does not have a menu item for AHCI).

So what I've decided to do is to replace the motherboard.

I will do that and report.

---

### Post by Hedgehog1 on 2011-04-15
> **GailHard said:**
> After doing much research, reading many hardware posts, I've reached the conclusion that the problem lies with the BIOS (Phoenix 3.24). It does not identify the disk which is driven by the PCI-SATA controller. It causes the computer to hang at the initial stage of the boot (before loading any drivers).

There are ways to tweak BIOS'es and fix this, but it seems that  the Phoenix 3.24 (dated 2003) is not customizable enough to enable that. (It does not have a menu item for AHCI).

So what I've decided to do is to replace the motherboard.

I will do that and report.

Ouch!  That hurts! * Ever notice that everything turns out to be harder that it was supposed to be?*

Hopefully you can get a faster processor out of the deal...

Thanks for the update!

***The Hedge***

:KS

---


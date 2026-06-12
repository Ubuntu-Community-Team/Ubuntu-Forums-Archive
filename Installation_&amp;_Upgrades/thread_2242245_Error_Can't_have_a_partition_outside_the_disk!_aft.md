---
title: "Error: Can't have a partition outside the disk! after resizing Windows"
date: 2014-08-31
forum: Installation &amp; Upgrades
---

### Post by Raggylad on 2014-08-31
Over on the 'Package System Broken' thread we have come up with and intersting error message in terminal:

```
Error: Can't have a partition outside the disk! 

```

after resizing Windows before starting a fresh dual boot install of 14.04.1.  The link to the relevant bit is onwards from here (starting at #190 on page 19) :

[http://ubuntuforums.org/showthread.php?t=2238992&page=19](http://ubuntuforums.org/showthread.php?t=2238992&page=19)

(Only read back if you wan't the back history of unsuccessful attempts to repair a weirdly damaged install of 12.04 !)

Gparted shows the following:

[ATTACH=CONFIG]256014[/ATTACH]

and we get the following from " sudo parted -l":

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA MD01200-AVDW-RO (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  67.9GB  67.9GB  primary  ntfs         boot

Error: Can't have a partition outside the disk!  
```

and this from "sudo fdisk -lu":

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bd2c32a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   132592559    66295256    7  HPFS/NTFS/exFAT


```

I'm being given great assistance by @Kansasnoob and @Bashing-om, but we really want to crack this error before we procede with the fresh install.

Very grateful for any help or advice that can be offered.

EDIT: Have now deleted code that reflected the presence of an external second (250 GB) HD - this was a red herring; the error message has been occurring without the external drive connected.

---

### Post by nadrach on 2014-08-31
Not sure if I am reading this right, but as far as I remember, on a dual (or multi) boot system, Windows always has to be the first partition, Linux goes into the next one. However, there needs to be a partition, not just free unallocated space.
You appear to have a 120 GB fixed disk of which only 67.9GB is allocated, and a 250GB portable disk almost all of which is allocated, in both cases configured as ntfs.
Both partitions start at the beginning of the disk and are Window formatted.
It seems as if you have free space, but not partitioned ready for Linux to load into. It needs a blank partition to work with.
For the dual boot you need to create a blank partition for the Linux to go into, on the 120GB disk, starting at 132592560 and ending at 234441648 (basically the unallocated space). Run Linux from the USB and use the disk partition program to do this. Format it anything simple ... FAT or ext2 will do.
Then run the Linux Install. Tell it to use this blank partition. It will divide it up for root and swap, reformat it (probably ext4 and swap) and, as you have with the portable disk, there will probably be a little left at the top that does not fit the block size (488392128 to 488397168 for the portable). Then it will amend or create a suitable boot loader to allow you to choose what to load at boot time.

---

### Post by kansasnoob on 2014-08-31
I thought that we were most recently working with the 250 GB drive disconnected. Do you still get that error message with the 250 GB drive disconnected?

If so fix your OP so people are not confused by the info regarding /dev/sdb. Or if it must remain connected then we can narrow it down to the specific drive by running:

```
sudo parted /dev/sda unit s print
```

```
sudo parted /dev/sdb unit s print
```

And for fdisk:

```
sudo fdisk -lu /dev/sda
```

```
sudo fdisk -lu /dev/sdb
```

I hadn't thought of it, but just for testing purposes you could right-click the unallocated space, select New, and then create a  primary partition there (any filesystem type will work for now because we'll change it before or during installation anyway). Then see if parted -l is still showing that error after creating the new partition, but don't change any other partitions.

---

### Post by Raggylad on 2014-09-01
> **kansasnoob said:**
> I thought that we were most recently working with the 250 GB drive disconnected. Do you still get that error message with the 250 GB drive disconnected?



My mistake.  We have been working with the 250 GB USB drive disconnected.  I had temporarily reconnected to get some files and forgot to disconnect before copying the code and posting the OP.  I noticed this after reading #2 and checked that the original error message still occurred - it did.

I'll correct the OP.

---

### Post by kansasnoob on 2014-09-01
> **Raggylad said:**
> My mistake.  We have been working with the 250 GB USB drive disconnected.  I had temporarily reconnected to get some files and forgot to disconnect before copying the code and posting the OP.  I noticed this after reading #2 and checked that the original error message still occurred - it did.

I'll correct the OP.

Thank you :D

---

### Post by westie457 on 2014-09-01
Adding my 2 cents here.
The size of the drive is being reported wrong.
255(heads)*63(sectors/tracks)*14593(cylinders) = 234436545(sectors)

The info from 'fdisk -lu' shows 234441648.
This difference is quite small at about 2.5 MB.

May I suggest running 'testdisk' over the drive and check what that reports.

---

### Post by kansasnoob on 2014-09-02
> **westie457 said:**
> Adding my 2 cents here.
The size of the drive is being reported wrong.
255(heads)*63(sectors/tracks)*14593(cylinders) = 234436545(sectors)

The info from 'fdisk -lu' shows 234441648.
This difference is quite small at about 2.5 MB.

May I suggest running 'testdisk' over the drive and check what that reports.

Thanks, could someone provide more detail about using Testdisk in this scenario? I've used it to recover partitions and data but never in a scenario like this.

---

### Post by westie457 on 2014-09-02
@kansasnoob
Testdisk will show immediately any errors/incorrect settings for the drive geometry. Though in this case everything is going to be in order I think.

I followed most of the thread that lead to this issue and understand that the OP has resized the Windows partition. Is that correct?

Testdisk running a 'quick search' will find the current partition and a 'deeper search' should find the old one (and probably a lot more). Comparing the start and finish points for both might show where the problem is.
Once we know that info we might be able to work on a plan for recovery.

In the meantime I am not going to suggest any commands for repair simply because they will most likely cause serious borking of the system.

@raggylad
testdisk is in the repo's and must be run as root ( it will let you know when it cannot run).```
sudo apt-get install testdisk
testdisk #to run, depending on environment will either run or tell you that you are not root. Hit Enter
```

More info and some basic steps here. [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
Either create a log file and post it here or post screenshots of each screen as they appear starting from the fourth screen which shows the current partitons on the drive.
Hopefully we will get somewhere with this.

---

### Post by kansasnoob on 2014-09-02
> I followed most of the thread that lead to this issue and understand that the OP has resized the Windows partition. Is that correct?

Yes, using only Vista's own partitioning tool per my instructions.

We know that the parted -l output was OK prior to:

(1) Mucking about in a failed attempt to salvage that Wubi install. That shouldn't have caused a problem - we just never could get apt and dpkg to play nice.

(2) Deleting the prior Wubi install. Which makes me think:

[I]Hmmmm, I need to do some research .............. thinking out-loud is sometimes beneficial :)

If memory serves correctly the problems with Wubi began due to it running out of room???

I don't know much about the Wubi file system, only that it doesn't survive hard resets well. So I should research this just a bit :-k[/I]

(3) Using Vista's own tools to defrag and resize multiple times. Gosh, I'd always thought that was the safest way to play with Windows :redface:

---

### Post by kansasnoob on 2014-09-02
I've been studying and found nothing specific regarding the deletion of Wubi from Windows but I started reading more about Testdisk and like this particular page:

[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

I think at this point it's best we just see the info provided by Analyse because we're not wanting to recover anything, particularly not the borked Wubi install we just got rid of.

So lets back up and go one step at a time:

Step #1: Boot the Ubuntu live DVD and install & run 'testdisk' as previously instructed, then follow these instructions:

[http://www.cgsecurity.org/wiki/Running_TestDisk](http://www.cgsecurity.org/wiki/Running_TestDisk)

Do choose to Create a new log file when prompted:

> Use arrow keys to select, then press Enter key:
[ Create ]  Create a new log file
[ Append ]  Append information to log file
[ No Log ]  Don't record anything

I would guess you'll be able to save that log file to a flash drive from the live session or post the whole log here at the forums either using copy-n-paste which you've done a lot of the past couple of weeks or possibly even compressing the log file and then attaching it to a forum post????

Step #2: When prompted to Select a media (use Arrow keys, then press Enter) that should show only your Windows drive as long as you have no external drive connected.

Step #3: Next step is to select the partition table type. You should select [Intel  ]  Intel/PC partition.

Step #4:  Move on to Analyse:

[http://www.cgsecurity.org/wiki/Menu_Analyse#Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse#Analyse)

Step #5: Move on to Partition checks:

[http://www.cgsecurity.org/wiki/Menu_Analyse#Partition_checks](http://www.cgsecurity.org/wiki/Menu_Analyse#Partition_checks)

Step #6: Move on to File system checks:

[http://www.cgsecurity.org/wiki/Menu_Analyse#Filesystem_checks](http://www.cgsecurity.org/wiki/Menu_Analyse#Filesystem_checks)

Step #7: This gets tricky and is very important! The next step is Partition recovery but we do NOT want to recover any data or partitions! So I think it wise to make no edits whatsoever without additional advice:

[http://www.cgsecurity.org/wiki/Menu_Analyse#Partition_recovery](http://www.cgsecurity.org/wiki/Menu_Analyse#Partition_recovery)

Notice at the end of that section it provides this info:

> Structure: Ok should appear if everything is ok, i.e., no primary partition between two extended partitions, one or no bootable partitions, no partitions using the same disk space.

When you are satisfied with the edited partition table, press Enter. If you've made any edits, TestDisk gives you a choice of writing that data to the drive's partition table, or of running a more detailed analysis.

Quit
    Quits (exits) from the TestDisk program without making any changes (unless you pressed the ENTER key while Write was highlighted). 
Search!
    The quick first scan may have miss some partitions. Search! will also search for FAT32 backup boot sector, NTFS backup boot superblock, ext2/ext3 backup superblock to detect more partitions, it will scan each cylinder. 
Write
    Writes the changes that have been made in TestDisk's memory buffer to the hard drive. **[COLOR="#FF0000"]If you are unsure of the changes (often to the MBR's partition table), then don't use this function! [/COLOR]**
Extd Part
    If there is logical partition, this flag lets you decide if the extended partition will used all available disk space or only the required (minimal) space. 

I recommend NOT writing any changes until you've posted the results of the Testdisk session and clarifying what it's recommending.

---

### Post by westie457 on 2014-09-03
@ kansasnoob
The 'cannot have a partition outside of disk' error appears in a lot of Boot Repair info reports. I think this is caused by the size of the ISO for the live environment being too 'large'. It won't hurt to run the report only function of Boot repair to see if that gives more details.

@raggylad
Go to here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) Take the 2nd Option (install Boot Repair) and run the commands given.When everything completes you should have the Boot Repair main window showing. Click on the 'Create a boot info' button. Post the resulting pastebin link so we can see what this is reporting.

---

### Post by kansasnoob on 2014-09-03
> The 'cannot have a partition outside of disk' error appears in a lot of Boot Repair info reports. I think this is caused by the size of the ISO for the live environment being too 'large'. It won't hurt to run the report only function of Boot repair to see if that gives more details.

I did not know that. So on my own main box with a gazillion partitions I used the live DVD and yep, there the error is:

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  157GB  157GB   primary   ext4            boot
 2      157GB   210GB  52.4GB  primary   ext4
 3      210GB   232GB  21.8GB  primary   ext4
 4      232GB   500GB  268GB   extended
 6      232GB   252GB  20.5GB  logical   ext4
 7      252GB   273GB  20.4GB  logical   ext4
 8      273GB   293GB  20.4GB  logical   ext4
 9      293GB   313GB  20.4GB  logical   ext4
10      313GB   334GB  20.4GB  logical   ext4
11      334GB   354GB  20.4GB  logical   ext4
12      354GB   374GB  20.0GB  logical   ext4
13      374GB   395GB  20.4GB  logical   ext4
14      395GB   415GB  20.1GB  logical   ext4
15      415GB   435GB  20.1GB  logical   ext4
16      435GB   455GB  20.4GB  logical   ext4
17      455GB   476GB  20.4GB  logical   ext4
18      476GB   498GB  21.9GB  logical   ext4
 5      498GB   500GB  2517MB  logical   linux-swap(v1)


Model: ATA WDC WD800BB-63JK (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  29.4GB  29.4GB  primary  ntfs


Model: ATA WDC WD1600AABB-5 (scsi)
Disk /dev/sdc: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  158GB  158GB   primary   ext4            boot
 2      158GB   160GB  2136MB  extended
 5      158GB   160GB  2136MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
**[COLOR="#FF0000"]Error: Can't have a partition outside the disk![/COLOR]**                           

```

Then the output from same box with an installed Trusty showing no error:

```
lance@lance-desktop:~$ sudo parted -l
[sudo] password for lance: 
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  157GB  157GB   primary   ext4            boot
 2      157GB   210GB  52.4GB  primary   ext4
 3      210GB   232GB  21.8GB  primary   ext4
 4      232GB   500GB  268GB   extended
 6      232GB   252GB  20.5GB  logical   ext4
 7      252GB   273GB  20.4GB  logical   ext4
 8      273GB   293GB  20.4GB  logical   ext4
 9      293GB   313GB  20.4GB  logical   ext4
10      313GB   334GB  20.4GB  logical   ext4
11      334GB   354GB  20.4GB  logical   ext4
12      354GB   374GB  20.0GB  logical   ext4
13      374GB   395GB  20.4GB  logical   ext4
14      395GB   415GB  20.1GB  logical   ext4
15      415GB   435GB  20.1GB  logical   ext4
16      435GB   455GB  20.4GB  logical   ext4
17      455GB   476GB  20.4GB  logical   ext4
18      476GB   498GB  21.9GB  logical   ext4
 5      498GB   500GB  2517MB  logical   linux-swap(v1)


Model: ATA WDC WD800BB-63JK (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  29.4GB  29.4GB  primary  ntfs


Model: ATA WDC WD1600AABB-5 (scsi)
Disk /dev/sdc: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  158GB  158GB   primary   ext4            boot
 2      158GB   160GB  2136MB  extended
 5      158GB   160GB  2136MB  logical   linux-swap(v1)

```

So in all likelihood it's yet another Trusty bug ](*,)

I'm sure sorry I put Raggylad through what may well have been a wild goose chase, I could have checked that on my box in five minutes any time :oops:

---

### Post by Bashing-om on 2014-09-03
westie457; kansasnoob;

Me 3 ->
> 
The 'cannot have a partition outside of disk' error appears in a lot of Boot Repair info reports. I think this is caused by the size of the ISO for the live environment being too 'large'. It won't hurt to run the report only function of Boot repair to see if that gives more details.
[color=red]I did not know that.[/color]

So this has not been in vain, we did learn something here !

[INDENT][INDENT]as we go merrily on our way
[/INDENT][/INDENT]

---

### Post by Raggylad on 2014-09-03
So, do I need to install and run Testdisk ? Or what ?  I'm a bit confused here (and that is 'charactersistic' Brit understatement !).

---

### Post by Raggylad on 2014-09-03
> **westie457 said:**
> 
@raggylad
Go to here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) Take the 2nd Option (install Boot Repair) and run the commands given.When everything completes you should have the Boot Repair main window showing. Click on the 'Create a boot info' button. Post the resulting pastebin link so we can see what this is reporting.

Here is the pastebin link:

[http://paste.ubuntu.com/8226822/](http://paste.ubuntu.com/8226822/)

---

### Post by westie457 on 2014-09-03
Well raggylad we are still not certain that there is an error with the partition.
So yes please go ahead with the install and running of testdisk.
Could you also provide the link to the Boot Repair report. This is to prove whether there is an error or a false flag of an error.

At the moment I am looking at safe ways to force Windows to run a chkdsk automatically at boot time.

---

### Post by westie457 on 2014-09-03
The report came through as I was typing my last reply.

Having given it a quick perusal apart from the error there is nothing unusual with the report. The error AFAICT has nothing to do with the Live environment and is on the hard drive.

I am about to try a very safe way to force Windows to run a CHKDSK at boot time. Will let you if it works and how to do it.

Be right back.

Edit: The very safe way did not force CHKDSK to run. Maybe I did not do it right.

---

### Post by kansasnoob on 2014-09-03
Sorry to seemingly just disappear, real life drug me away from the desk.

I've tested with various live DVD's - different flavors - 14.04.1, 14.04, and even 12.04.1 - using two different PC's and I always get that error when running "sudo parted -l" in a live session but NOT in a session from the installed OS.

I'm going to try one or two more things before leaping to a conclusion so please be patient :)

---

### Post by kansasnoob on 2014-09-03
The latest Gparted live image displays a different error:

> Error: Invalid partition table - recursive partition on /dev/sr0.

[ATTACH=CONFIG]256113[/ATTACH]

One more test to go before I'm convinced it's just a bug ;)

---

### Post by kansasnoob on 2014-09-03
Macpup also shows it's a /dev/sr0 error so I'm convinced:

[ATTACH=CONFIG]256114[/ATTACH]

I'll put together some partitioning steps ASAP and we'll go from there.

What if I'm wrong?

Well, creating the partitions with Gparted will take about 5 minutes to complete. If we encounter errors we'll stop.

The installation will take 20 to 30 minutes to complete. If the whole thing fails you may need to restore the Windows MBR to be able to boot Vista which may take about 15 minutes with the live DVD.

No big deal - we just need to be sure to leave the Windows partition alone since it's working well now!

---

### Post by kansasnoob on 2014-09-03
I think it's time to get on with the partitioning and see what happens. I'm just using a spare 80 GB drive as a mock-up for these screenshots. **[COLOR="#FF0000"]Please be sure to have all external devices such as USB drives disconnected during partitioning and installation! And we want to leave the Windows partition alone![/COLOR]**

Using the live DVD open Gparted, right-click the unallocated space, select New, and a new window will open. The defaults should be correct other than size. So just change ***Free space following (MiB)*** to 4200:

[ATTACH=CONFIG]256120[/ATTACH]

Then just click on Add and that window will close showing we still have unallocated space to assign for SWAP so right-click on the unallocated space, select New, and this time we'll change ***Create as*** to Extended Partition:

[ATTACH=CONFIG]256121[/ATTACH]

After clicking on Add you'll see you still have unallocated space within the new extended partition where we want to create a logical SWAP partition so once again right-click unallocated, select New, and this time change ***File system*** to linux-swap:

[ATTACH=CONFIG]256122[/ATTACH]

After clicking on Add you should see something similar to this:

[ATTACH=CONFIG]256123[/ATTACH]

So just click on the green check mark to apply those changes. If Gparted completes that process without complaining you should see that you've created /dev/sda2 which will be used as your Ubuntu root (/) partition, and /dev/sda5 which will be used as SWAP (mine shows /dev/sdb but remember it's only a mock-up):

[ATTACH=CONFIG]256124[/ATTACH]

Does that all jive so far? Please post a screenshot just so I can be sure and then I'll provide detailed installation info ............. sometime tomorrow.

BTW there are reasons I'm using that exact partitioning layout:

(1) I think you indicated at one point that you may wish to remove Win Vista altogether in the future. That's why I recommend giving Ubuntu a primary root partition rather than a logical root. I've seldom seen it happen but some hardware (particularly with an older BIOS) can complain about having only logical partitions so we'll just play it safe.

(2) I want to give you a bit over 4 GB of SWAP to hopefully ensure decent suspend and hibernate behavior if you choose to use those features. I have no in house laptops so I've not tested those features in Trusty though.

(3) While some users recommend a separate /home I've long since moved away from that in favor of external storage such as you appear to already use for backing up and restoring any data. I've also found that the hidden dot config files in /home frequently need to be purged after a reinstall where /home is reused - why carry borked config files over to a fresh install?

---

### Post by Raggylad on 2014-09-04
@Kansasnoob,

Thanks for this (#21).  I can't go through it now, but will be back on in about 24 hours.

---

### Post by kansasnoob on 2014-09-04
I'm following up on this buggy behavior over at the dev sub-forum:

[http://ubuntuforums.org/showthread.php?t=2242825](http://ubuntuforums.org/showthread.php?t=2242825)

Nothing for Raggylad to worry about but maybe others will want to wade into the deep end :guitar:

---

### Post by kansasnoob on 2014-09-04
> **Raggylad said:**
> @Kansasnoob,

Thanks for this (#21).  I can't go through it now, but will be back on in about 24 hours.

Cool, take your time. It's a pleasure working with someone that displays your level of patience :D

---

### Post by Raggylad on 2014-09-04
> **kansasnoob said:**
> Cool, take your time. It's a pleasure working with someone that displays your level of patience :D

Thanks, you are very kind to say so.

In 'real' life, I teach applied systems integration - albeit in the mechanical engineering field - so I know that these things take time.  So long as I have a workable fallback (and I have two in the 14.04 live disc and W Vista), I'm content to let things run in the interests of achieving a a 'true' dual boot that is stable.  I'm also learning more about Linux than I (as a simple user) ever expected to; the day one stops learning, one is effectively dead !

---

### Post by Bashing-om on 2014-09-04
> **Raggylad said:**
> Thanks, you are very kind to say so.

In 'real' life, I teach applied systems integration - albeit in the mechanical engineering field - so I know that these things take time.  So long as I have a workable fallback (and I have two in the 14.04 live disc and W Vista), I'm content to let things run in the interests of achieving a a 'true' dual boot that is stable.  I'm also learning more about Linux than I (as a simple user) ever expected to; the day one stops learning, one is effectively dead !

Hear hear !

Each morning I sit down before this terminal, and I ask, "what can I learn today".
With the guidance and help of many, I too progress on in my comprehension of this wonderful operating system.

We will, one way or another, get up up on a stable system.

Open Source -> ubuntu
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT]

---

### Post by westie457 on 2014-09-04
@kansasnoob & @Bashing-om & @raggylad
Concerning the 'cannot have partition outside' error here is the post where I asked oldfred about this issue, immediately after is his response. [http://ubuntuforums.org/showthread.php?t=2213412&p=12968718#post12968718](http://ubuntuforums.org/showthread.php?t=2213412&p=12968718#post12968718)

For me if has been a pleasurable experience to help on this issue. I have learned a bit more.
I would have helped in the thread that led to this one if it wasn't for the fact that after about post #6 I needed scuba apparatus. That one was so far over my head I was drowning.

---

### Post by kansasnoob on 2014-09-04
> **westie457 said:**
> @kansasnoob & @Bashing-om & @raggylad
Concerning the 'cannot have partition outside' error here is the post where I asked oldfred about this issue, immediately after is his response. [http://ubuntuforums.org/showthread.php?t=2213412&p=12968718#post12968718](http://ubuntuforums.org/showthread.php?t=2213412&p=12968718#post12968718)

For me if has been a pleasurable experience to help on this issue. I have learned a bit more.
I would have helped in the thread that led to this one if it wasn't for the fact that after about post #6 I needed scuba apparatus. That one was so far over my head I was drowning.

Aha .........

>  If you have installer DVD still mounted it gives that error 

Seems similar to what I'm being told here:

[http://ubuntuforums.org/showthread.php?t=2242825&p=13115086#post13115086](http://ubuntuforums.org/showthread.php?t=2242825&p=13115086#post13115086)

> Did you have a disk in the CD/DVD drive in your first example? ( and not in 2nd 

I'm going to do a repeat test with a live USB ASAP ........................... dealing with storm damage cleanup ATM.

---

### Post by westie457 on 2014-09-05
> [COLOR=#000000]I'm going to do a repeat test with a live USB ASAP ........................... dealing with storm damage cleanup ATM.[/COLOR]

Do not be surprised when the error shows. It has been a few weeks since I checked with a Live USB (no DVDs here), I think the error does appear.

IIRC the ISO gets mounted as /dev/sr0 and the OS is mounted as /dev/loop.

We know that the Ubuntu ISO is more than 700MB. It might be worth checking with a Lubuntu ISO (slightly less than 700MB - the limit for a CD). The error might not appear.

---

### Post by Raggylad on 2014-09-05
For the avoidance of doubt and the possibility of going down blind alleys - my live disc ISO is on a DVD, not a CD.

(Not sure if this matters ?)  :?

---

### Post by kansasnoob on 2014-09-05
> **westie457 said:**
> Do not be surprised when the error shows. It has been a few weeks since I checked with a Live USB (no DVDs here), I think the error does appear.

IIRC the ISO gets mounted as /dev/sr0 and the OS is mounted as /dev/loop.

We know that the Ubuntu ISO is more than 700MB. It might be worth checking with a Lubuntu ISO (slightly less than 700MB - the limit for a CD). The error might not appear.

No error shown with Ubuntu GNOME 14.04.1 live USB:

[http://ubuntuforums.org/showthread.php?t=2242825&p=13115729#post13115729](http://ubuntuforums.org/showthread.php?t=2242825&p=13115729#post13115729)

So it seems like a live DVD thing, and on one of the PC's I used for testing I did use an Lubuntu 14.04 live DVD because it's graphics chip is not capable of running either Unity or GNOME Shell and even the smaller Lubuntu image displays that error.

So I know it's a bug. I'll probably see what Debian live shows next and then file a bug report when I have enough info to make it relevant.

---

### Post by Raggylad on 2014-09-05
> **kansasnoob said:**
> I think it's time to get on with the partitioning and see what happens. I'm just using a spare 80 GB drive as a mock-up for these screenshots. **[COLOR=#FF0000]Please be sure to have all external devices such as USB drives disconnected during partitioning and installation! And we want to leave the Windows partition alone![/COLOR]**

Using the live DVD open Gparted, right-click the unallocated space, select New, and a new window will open. The defaults should be correct other than size. So just change ***Free space following (MiB)*** to 4200:

[ATTACH=CONFIG]256120[/ATTACH]

Then just click on Add and that window will close showing we still have unallocated space to assign for SWAP so right-click on the unallocated space, select New, and this time we'll change ***Create as*** to Extended Partition:

[ATTACH=CONFIG]256121[/ATTACH]

After clicking on Add you'll see you still have unallocated space within the new extended partition where we want to create a logical SWAP partition so once again right-click unallocated, select New, and this time change ***File system*** to linux-swap:

[ATTACH=CONFIG]256122[/ATTACH]

After clicking on Add you should see something similar to this:

[ATTACH=CONFIG]256123[/ATTACH]

So just click on the green check mark to apply those changes. If Gparted completes that process without complaining you should see that you've created /dev/sda2 which will be used as your Ubuntu root (/) partition, and /dev/sda5 which will be used as SWAP (mine shows /dev/sdb but remember it's only a mock-up):

[ATTACH=CONFIG]256124[/ATTACH]

Does that all jive so far? Please post a screenshot just so I can be sure and then I'll provide detailed installation info ............. sometime tomorrow.

BTW there are reasons I'm using that exact partitioning layout:

(1) I think you indicated at one point that you may wish to remove Win Vista altogether in the future. That's why I recommend giving Ubuntu a primary root partition rather than a logical root. I've seldom seen it happen but some hardware (particularly with an older BIOS) can complain about having only logical partitions so we'll just play it safe.

(2) I want to give you a bit over 4 GB of SWAP to hopefully ensure decent suspend and hibernate behavior if you choose to use those features. I have no in house laptops so I've not tested those features in Trusty though.

(3) While some users recommend a separate /home I've long since moved away from that in favor of external storage such as you appear to already use for backing up and restoring any data. I've also found that the hidden dot config files in /home frequently need to be purged after a reinstall where /home is reused - why carry borked config files over to a fresh install?

@Kansasnoob,

Well, I _think_ I've done all that and Gparted did it without complaint.  As to whether I've done it correctly ......

Here's the screenshot of what I got from Gparted at the end:

[ATTACH=CONFIG]256186[/ATTACH]

---

### Post by Bashing-om on 2014-09-05
Raggylad; Hey;

Can try it and see how it plays out, but, a mighty small 'swap' partition. I do not recall how much ram you said you presently have, and IF you do not hibernate - a small 'swap' may never be an issue.

[INDENT][INDENT]her's hoping 
[/INDENT][/INDENT]

---

### Post by westie457 on 2014-09-05
As Bashing-om has stated, give it a try. If you find that you need to use 'swap' I believe it is a relatively easy process to convert the unallocated partition to be used as swap and then edit fstab to mount it at boot time.

See you on the dark side.

---

### Post by kansasnoob on 2014-09-05
I disagree ............ STOP! It's not right!

Let's start off the right way!

When I did those instructions I crunched things to try and get by with 5 screenshots so let me do things different, it'll just take more than one post.

In the meanwhile, if you've not started the installation, I'd prefer you use Gparted to just delete those newly created partitions.

---

### Post by kansasnoob on 2014-09-05
Actually on second look you need only delete /dev/sda5 and /dev/sda3. Your /dev/sda2 is OK. Hold on just a bit so I can explain.

But even if you delete all of the new partitions you now know how easy and fast it is to create new partitions. Just hold on while I run a few errands.

Remember the most important thing is NOT touching /dev/sda1 because Windows resides there.

---

### Post by Raggylad on 2014-09-05
> **Bashing-om said:**
> Raggylad; Hey;

Can try it and see how it plays out, but, a mighty small 'swap' partition. I do not recall how much ram you said you presently have, and IF you do not hibernate - a small 'swap' may never be an issue.
[INDENT][INDENT]her's hoping 
[/INDENT]
[/INDENT]


4GB of RAM - it's an old-ish business machine.

---

### Post by Raggylad on 2014-09-05
> **kansasnoob said:**
> Actually on second look you need only delete /dev/sda5 and /dev/sda3. Your /dev/sda2 is OK. Hold on just a bit so I can explain.

But even if you delete all of the new partitions you now know how easy and fast it is to create new partitions. Just hold on while I run a few errands.

Remember the most important thing is NOT touching /dev/sda1 because Windows resides there.

Gparted doesn't want to let me delete those two partitions.  If you look in the left hand column of the screenshot, there is a key symbol (locked ?) by each:

---

### Post by Raggylad on 2014-09-05
Sorry - here's the screenshot:

[ATTACH=CONFIG]256188[/ATTACH]

---

### Post by kansasnoob on 2014-09-05
> **Raggylad said:**
> @Kansasnoob,

Well, I _think_ I've done all that and Gparted did it without complaint.  As to whether I've done it correctly ......

Here's the screenshot of what I got from Gparted at the end:

[ATTACH=CONFIG]256186[/ATTACH]

Sorry to seemingly freak out in my last two posts, but I don't like the "just pull the trigger and see what happens" approach to things.

And I think these trials and tribulations actually prove to be worthwhile for those who appreciate learning some basic *nuts-n-bolts* about installation, reinstallation, and partitioning. I'll put it this way - I'm not a very smart guy. I went to tech school and learned auto/diesel repair long before A/C and electronic ignition were even the norm, let alone on-board computers. So believe me, if I can do this - *you can do this* :D 

Anyway I can easily see what went wrong or (more accurately) what confused you, and it's understandable. You created the first partition just as I instructed in [post #21]("http://ubuntuforums.org/showthread.php?t=2242245&page=3&p=13114807#post13114807"). But then Gparted showed that you had two unallocated spaces - 1 to the left of the new partition (1.00 MiB), and one to the right of the new partition (4.10 GiB). I had not thought to say anything about the possibility of that happening so this comes down to ***bad instruction on my part*** :oops:

So, why did that happen? Quite simply due to the physical limitations of a hard drive we sometimes get small unallocated chunks of space between partitions. There can actually be a number of technical reasons for that, some of which I don't fully understand even though they've been explained to me, but I multi-boot a lot in the process of QA testing so I have more physical partitions than any sane person would have:

[ATTACH=CONFIG]256189[/ATTACH]

You'll notice there that I have four such small unallocated spaces ranging in size from just over 1 MiB to just under 2.5 MiB, but it's not worth trying to fix that. In fact I shouldn't even use the word fix, there is nothing to fix. All added together they amount to less than 5 MiB so it just doesn't matter. In my case though it may be partly due to that drive having an ever increasing number of bad sectors:

[ATTACH=CONFIG]256190[/ATTACH]

Anyway in my next post I'll explain exactly what to do, assuming that you have waited. Have you waited?

---

### Post by kansasnoob on 2014-09-05
> **Raggylad said:**
> Gparted doesn't want to let me delete those two partitions.  If you look in the left hand column of the screenshot, there is a key symbol (locked ?) by each:

OK, now that you have a SWAP partition, albeit a small one, when you boot the live image it automatically sniffs out any existing SWAP space and mounts it.

But let me back up a bit. By now you've probably figured out Linux device designations. Like /dev/sda is your entire internal drive, when you plug in your external drive it's recognized as /dev/sdb, etc.

Your Windows partition is /dev/sda1, and the first partition you created (44.46 GiB) is /dev/sda2, the logical SWAP is /dev/sda5, and the extended partition it resides in is /dev/sda3.

Clear so far? 

So in answer to this last question, first you need only delete /dev/sda5 and then /dev/sda3. Your /dev/sda2 can stay - in fact it's perfect.

To delete the SWAP partition and the extended partition it resides in you first need to right-click on the linux-swap partition and select Swapoff. Then you can delete /dev/sda5 and then /dev/sda3.

---

### Post by kansasnoob on 2014-09-05
So in these screenshots I'm using that 80Gb drive again for mock-ups. For the same physical limitations mentioned earlier I can't make the partition sizes and free (aka: unallocated) spaces identical in size to what you see but when you created the first partition you did fine. You just ended up with a small free space to the left of /dev/sda2 that we don't even want to use or worry about. You just should have used the free space to the right to create the extended and SWAP partitions like this:

[ATTACH=CONFIG]256191[/ATTACH]

[ATTACH=CONFIG]256192[/ATTACH]

[ATTACH=CONFIG]256193[/ATTACH]

[ATTACH=CONFIG]256194[/ATTACH]

[ATTACH=CONFIG]256195[/ATTACH]

Sorry I didn't take into account that you could end up with that insignificant free space to the left of the first new partition.

---

### Post by Bashing-om on 2014-09-05
kansasnoobl: Raggylad;

^^^ +5 ...in all this keep in mind Westie's post 6, We hope when all this is done the disk reported size/partitioning coincides .

[INDENT][INDENT]try'n to keep up here
 [/INDENT][/INDENT]

---

### Post by kansasnoob on 2014-09-05
> **Bashing-om said:**
> kansasnoobl: Raggylad;

^^^ +5 ...in all this keep in mind Westie's post 6, We hope when all this is done the disk reported size/partitioning coincides .

[INDENT][INDENT]try'n to keep up here
 [/INDENT][/INDENT]

Regarding that parted error I've gotten as far as knowing it's an upstream bug in Debian. Earlier today I tested with Debian Live (GNOME DE) version 7.6:

```
user@debian:~$ sudo parted -l
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  157GB  157GB   primary   ext4            boot
 2      157GB   210GB  52.4GB  primary   ext4
 3      210GB   232GB  21.8GB  primary   ext4
 4      232GB   500GB  268GB   extended
 6      232GB   252GB  20.5GB  logical   ext4
 7      252GB   273GB  20.4GB  logical   ext4
 8      273GB   293GB  20.4GB  logical   ext4
 9      293GB   313GB  20.4GB  logical   ext4
10      313GB   334GB  20.4GB  logical   ext4
11      334GB   354GB  20.4GB  logical   ext4
12      354GB   374GB  20.0GB  logical   ext4
13      374GB   395GB  20.4GB  logical   ext4
14      395GB   415GB  20.1GB  logical   ext4
15      415GB   435GB  20.1GB  logical   ext4
16      435GB   455GB  20.4GB  logical   ext4
17      455GB   476GB  20.4GB  logical   ext4
18      476GB   498GB  21.9GB  logical   ext4
 5      498GB   500GB  2517MB  logical   linux-swap(v1)


Model: ATA WDC WD800BB-63JK (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  29.4GB  29.4GB  primary   ntfs
 2      29.4GB  75.6GB  46.3GB  primary   ext4
 3      75.6GB  80.0GB  4404MB  extended
 5      75.6GB  80.0GB  4403MB  logical   linux-swap(v1)


Model: ATA WDC WD1600AABB-5 (scsi)
Disk /dev/sdc: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  158GB  158GB   primary   ext4            boot
 2      158GB   160GB  2136MB  extended
 5      158GB   160GB  2136MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
**[COLOR="#FF0000"]Error: Can't have a partition outside the disk![/COLOR]**      
```

And I checked it's version of 'parted':

```
user@debian:~$ apt-cache policy parted
parted:
  Installed: 2.3-12
  Candidate: 2.3-12
  Version table:
 *** 2.3-12 0
        500 http://http.debian.net/debian/ wheezy/main i386 Packages
        100 /var/lib/dpkg/status
```

So I just need to lump all of my findings together, possibly retest with the appropriate version of Gparted live, and then file a bug report :)

---

### Post by kansasnoob on 2014-09-05
> **Bashing-om said:**
> Raggylad; Hey;

Can try it and see how it plays out, but, a mighty small 'swap' partition. I do not recall how much ram you said you presently have, and IF you do not hibernate - a small 'swap' may never be an issue.

[INDENT][INDENT]her's hoping 
[/INDENT][/INDENT]

Why would you have recommended that? Why not explain what happened and why?

I'll grant you it could have been fixed after installing but why start with a partitioning layout that's not quite correct?

Remember Raggylad was previously running Precise so it's possible that Trusty could display hardware compatibility issues we can't yet be aware of. I Googled to see if I could find any known bugs related to his hardware and found none but we could still discover some yet unknown issue. So lets do it right so we're not going in circles trying this, and trying that, and getting nowhere.

One of the reasons I'm trying to be as specific as possible about partitioning and installation is so Raggylad will know how to easily reinstall when the time comes ;)

I mean if Trusty doesn't work out well for him he may wish to reinstall using the archived 12.04.1 image, or perform a reinstall of 16.04 when it becomes available, or he may end up with a borked install for any number of reasons and decide that starting over is just easier and quicker than trying to sort things out :)

---

### Post by kansasnoob on 2014-09-05
@ Raggylad,

Hopefully the next screenshot you post will resemble this:

[ATTACH=CONFIG]256197[/ATTACH]

Then I'll post some screenshots to show how to proceed safely with the installation :D

---

### Post by Raggylad on 2014-09-06
> **kansasnoob said:**
> 

Anyway in my next post I'll explain exactly what to do, assuming that you have waited. Have you waited?

@Kansasnoob,

I've waited !  I was up in the middle of the night (fox trying to get into the hen house & then couldn't sleep) but then zonked out before doing any more.  I'm patient & prefer to take things step by step so not at all freaked out !

---

### Post by Raggylad on 2014-09-06
> **kansasnoob said:**
> OK, now that you have a SWAP partition, albeit a small one, when you boot the live image it automatically sniffs out any existing SWAP space and mounts it.

But let me back up a bit. By now you've probably figured out Linux device designations. Like /dev/sda is your entire internal drive, when you plug in your external drive it's recognized as /dev/sdb, etc.

Your Windows partition is /dev/sda1, and the first partition you created (44.46 GiB) is /dev/sda2, the logical SWAP is /dev/sda5, and the extended partition it resides in is /dev/sda3.

Clear so far? 

So in answer to this last question, first you need only delete /dev/sda5 and then /dev/sda3. Your /dev/sda2 can stay - in fact it's perfect.

To delete the SWAP partition and the extended partition it resides in you first need to right-click on the linux-swap partition and select Swapoff. Then you can delete /dev/sda5 and then /dev/sda3.

Quite clear.  I've deleted /dev/sda/5 and /dev/sda3.  Screenshot:

[ATTACH=CONFIG]256209[/ATTACH]

---

### Post by Raggylad on 2014-09-06
> **kansasnoob said:**
> @ Raggylad,

Hopefully the next screenshot you post will resemble this:

[ATTACH=CONFIG]256197[/ATTACH]

Then I'll post some screenshots to show how to proceed safely with the installation :D

@Kansasnoob,

Here's what I've got now:

[ATTACH=CONFIG]256210[/ATTACH]

Looking OK ?

---

### Post by kansasnoob on 2014-09-06
> **Raggylad said:**
> @Kansasnoob,

Here's what I've got now:

[ATTACH=CONFIG]256210[/ATTACH]

Looking OK ?

**[COLOR="#FF0000"]Close enough[/COLOR]**. I had actually recommended making SWAP a logical partition as opposed to a primary partition but what you have now is OK.

I'll try to explain without getting too technical. Up until recently physical hard drives had a 4 primary partition limit but in order to work around that a person could limit themselves to 3 primary partitions and create 1 extended partition that can contain a large number of logical partitions. With that current arrangement you still only have 3 primary partitions so you should be fine.

I always try to look ahead though, and just for instance Windows 8 likes to use a minimum of 2 primary partitions (no idea what Windows 9 will want yet) so if you were to decide to replace Vista with Windows 8 you'd still be OK, but if you were to replace Vista with Windows 8 and also upgrade to a larger hard drive you may end up wishing SWAP was logical.

But quite honestly, at this point in time, if you were to both upgrade Windows and the hard drive it would be best to have the existing hard drive removed while Windows was being installed. Then the existing drive could be connected via USB and the Ubuntu partitions could be copied to the new drive as either primary or logical partitions.

So I think we should just go for it :)

In my next post I'll explain exactly how to perform the installation based on that last screenshot, so **[COLOR="#FF0000"]make no more changes![/COLOR]**

---

### Post by kansasnoob on 2014-09-06
OK it's time to install. Please read this all before beginning. **[COLOR="#FF0000"]No mistakes are allowed during this procedure[/COLOR]** so ask questions before beginning if anything is even slightly less than crystal clear. Be sure you have no external devices connected such as a USB drive.

Since you're totally new to this you may want to look here for a basic overview:

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

But that shows using the install alongside option and due to [this bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192") you do NOT want to do that! That's why we created our own partitions in advance. Just **[COLOR="#FF0000"]do NOT mess with /dev/sda or /dev/sda1[/COLOR]**. Are you clear on device designations?

When you get to the ***Installation type*** screen you want to choose the option called ***Something else***, then click on ***Continue*** in the lower right hand corner of the window and after a few minutes a new window will open:

[ATTACH=CONFIG]256215[/ATTACH]

In that example you can see that it displays the entire drive and all of the partitions. This is where **[COLOR="#FF0000"]knowing your device designations is of the utmost importance[/COLOR]**. And in that example my SWAP is on /dev/sda5 whereas yours is on /dev/sda3.

Based on your last screenshot you should see the following device designations - from top to bottom:

```
/dev/sda   - **[COLOR="#FF0000"]this is your entire drive, leave it alone![/COLOR]**
/dev/sda1  - **[COLOR="#FF0000"]this is your Windows partition, leave it alone![/COLOR]**
/dev/sda2  - this is the 44 GB partition you created for Ubuntu's / (aka; root), it's the only partition you want to change
/dev/sda3  - this is the SWAP partition you created, no further change to it is needed
```

**[COLOR="#FF0000"]If you mess with /dev/sda or /dev/sda1 you will erase your Windows OS and all of the data!!!![/COLOR]**

So highlight only /dev/sda2, then click on ***Change*** and a new window will open:

[ATTACH=CONFIG]256216[/ATTACH]

You can see there that the default is do not use and the format box is not checked so we need to make some changes:

Size:        Leave it alone - we created the size we want
Use as:      Ext4 journaling file system
Format the partition must be checked
Moint point: /

So after applying those changes it should look like this:

[ATTACH=CONFIG]256217[/ATTACH]

After clicking on OK you'll be asked to confirm those changes (this is your last chance to abort):

[ATTACH=CONFIG]256218[/ATTACH]

After clicking on ***Continue*** you'll be back here: 

[ATTACH=CONFIG]256219[/ATTACH]

Notice that /dev/sda2 now shows ext4 as type, / as the Mount point, and the format box is checked. Those are the only changes you need to make so after clicking on ***Install now*** the installation will proceed other than you having to answer a few basic questions and entering your login info.

I'll be keeping my fingers crossed.

---

### Post by Raggylad on 2014-09-06
@Kansasnoob,

Great; have read through all that and got it.  Paper notes of critical points made !

(NB: not quite my first fresh install - a couple since 2009- but definitely the first where I haven't taken the easy option !).

Back in a while.

---

### Post by Raggylad on 2014-09-06
Not good !  Installer crashed right towards the end of the install process.  

Aport has collected data and sent a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1366416](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1366416)

Ummmmm ....

It's late here in UK, so I'm going to log out.  Back in 12 hours or so.

---

### Post by kansasnoob on 2014-09-06
> **Raggylad said:**
> Not good !  Installer crashed right towards the end of the install process.  

Aport has collected data and sent a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1366416](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1366416)

Ummmmm ....

It's late here in UK, so I'm going to log out.  Back in 12 hours or so.

Arrrrgh ](*,)

From looking at the logs it appears that we did nothing wrong, I left a couple of comments there.

I may need to go back to writing lyrics for my parody of Stuck in the Middle With You:

[http://ubuntuforums.org/showthread.php?t=2237479](http://ubuntuforums.org/showthread.php?t=2237479)

---

### Post by kansasnoob on 2014-09-06
I'm just thinking out loud here, that sometimes seems to be when I do my best thinking :)

I'm reasonably certain that this installer crash had nothing to do with the parted -l error. The ubiquity partman log looks OK to me but I'd still like to see a new screenshot of Gparted in case I'm missing something.

As a general rule of thumb any time I have an installation fail I boot the live DVD again and run that Check disc for defects again just to be sure the disc was not damaged in handling or something like that, but that's seldom the case. It's still always worth checking though and it doesn't take very long.

Since it appears that it was actually an apt failure I wonder if you were using a wired or wireless connection? If you were using a wireless connection maybe the connection was dropped during package installation??? That's just a guess based on this:

```
Sep  6 21:37:51 ubuntu ubiquity: Setting up ubuntu-restricted-addons (20) ...
Sep  6 21:37:51 ubuntu ubiquity: Processing triggers for libc-bin (2.19-0ubuntu6) ...
Sep  6 21:37:54 ubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Sep  6 21:37:54 ubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Sep  6 21:37:54 ubuntu /plugininstall.py: log-output -t ubiquity umount /target/run
Sep  6 21:37:54 ubuntu /plugininstall.py: log-output -t ubiquity umount /target/dev
Sep  6 21:37:54 ubuntu kernel: [ 3472.843779] plugininstall.p[14944]: segfault at f2f58000 ip b6e7fef2 sp bf8054e0 error 5 in libapt-pkg.so.4.12.0[b6e2b000+143000]
```

If a failed internet connection is the cause then maybe installing without selecting Download updates and Install third party software would let it complete succesfully???

Just a bit from the ubiquity syslog:

```
Sep  6 21:41:36 ubuntu kernel: [   94.362493] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found
Sep  6 21:41:36 ubuntu kernel: [   94.362497] b43-phy0 ERROR: Firmware file "b43-open/ucode13.fw" not found
Sep  6 21:41:36 ubuntu kernel: [   94.362500] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```

But a bit later it says:

```
Sep  6 21:42:12 ubuntu NetworkManager[1949]: <info> Activation (eth0) successful, device activated.
```

Interestingly it looks like grub installed successfully:

```
Sep  6 21:30:50 ubuntu grub-installer: info: Installing grub on '/dev/sda'
Sep  6 21:30:50 ubuntu grub-installer: info: grub-install does not support --no-floppy
Sep  6 21:30:50 ubuntu grub-installer: info: Running chroot /target grub-install  --force "/dev/sda"
Sep  6 21:30:50 ubuntu grub-installer: Installing for i386-pc platform.
Sep  6 21:31:07 ubuntu grub-installer: Installation finished. No error reported.
Sep  6 21:31:07 ubuntu grub-installer: info: grub-install ran successfully
```

So maybe we can still recover this without a new install??? I have serious doubts about that.

Then seemingly blowing a hole in my failed connection theory:

```
Sep  6 21:35:41 ubuntu /plugininstall.py: **[COLOR="#FF0000"]Downloads verified successfully[/COLOR]**
```

And all goes well until it pukes here:

```
Sep  6 21:37:54 ubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Sep  6 21:37:54 ubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Sep  6 21:37:54 ubuntu /plugininstall.py: log-output -t ubiquity umount /target/run
Sep  6 21:37:54 ubuntu /plugininstall.py: log-output -t ubiquity umount /target/dev
Sep  6 21:37:54 ubuntu kernel: [ 3472.843779] plugininstall.p[14944]: segfault at f2f58000 ip b6e7fef2 sp bf8054e0 error 5 in libapt-pkg.so.4.12.0[b6e2b000+143000]
```

I could use some other thinkers here ;)

---

### Post by westie457 on 2014-09-07
@raggylad

Using 'kansasnoob's guide in post #51 it looks as though /sda3 (the swap partition) has been created but not activated.
As stated earlier with 4GB of RAM is not strictly necessary so is probably not related to the installation error that you have.
Before going through the 'Something Else' options for drive set-up and reinstalling would you like to try the routine that I use when an installation fails or when there is a system lock-up?
It usually works for me and is safe.

Boot up and at the Grub menu select 'Advanced options' and hit Enter.
Next screen select the first line that has (Recovery options) and hit Enter.

I cannot remember the order of the options that appear in the Menu screen so will highlight them here so you can see which to go for in the following order.
#1 [COLOR=#ff0000]FSCK[/COLOR] Checks the file-systems for errors and corrects them (often not needed but never hurts to run).
#2 Plug a network cable in and select [COLOR=#ff0000]Enable Network[/COLOR] (usually needed for the next step)
#3 [COLOR=#ff0000]DPKG,[/COLOR]Runs the dpkg --configure -a command. Checks the installed packages, downloads and fixes broken packages and applies any updates to the packages. Can take a long time. be patient.
#4 [COLOR=#ff0000]Root[/COLOR] Opens a root terminal -sudo is not needed here so be careful **(only run the following here) **```
apt-get update
apt-get upgrade
update-grub
exit
```
#5 [COLOR=#ff0000]CLEAN [/COLOR]Attempts to free up space by removing obsolete packages.
#6 [COLOR=#ff0000]Boo[/COLOR][COLOR=#ff0000]t[/COLOR] The first one in the list and self-explanatory.

In the above follow the on-screen prompts as they appear - mostly they should be hit ENTER.

Hopefully this will work for you, If it does not then it might be quicker to re-install.

---

### Post by westie457 on 2014-09-07
@kansasnoob

Through searching the web segfaults are caused by the OS attempting to write to protected areas of memory
I genuinely do not know how to de-bug errors at code level. The routine in my previous post cures the system most of the time.

---

### Post by kansasnoob on 2014-09-07
> **westie457 said:**
> @kansasnoob

Through searching the web segfaults are caused by the OS attempting to write to protected areas of memory
I genuinely do not know how to de-bug errors at code level. The routine in my previous post cures the system most of the time.

It would probably be a good idea to run a memory test. I seem to recall a read only problem early on with the borked Wubi install. I wish I'd thought of running a memory test long ago.

---

### Post by Raggylad on 2014-09-07
@Kansasnoob, @Westie457,

Before I run the procedures suggested by Westie457, it's worth noting:

- My internet connection was a wired one throughout the install (and still is - it's how I prefer to connect whenever possible)
- Grub appears to have installed successfully
- Windows is still there and working as well as it ever did
- Ubuntu appears to have installed; I'm running on the installed version, not the live disc, to do this
- Software Updater is offering me 61+MB of updates

I'll wait for your comments before doing anything rash.

---

### Post by kansasnoob on 2014-09-07
So, more thinking out loud ................ it makes sense to rule out a couple of things and find out just where we're at, so I'd try the following:

(1) Boot the live DVD and run Check disc for defects again just to rule that out as a problem.

(2) Run a Memory test using the live DVD. This can unfortunately take quite a while but it's something we should have done some time ago :oops:

(3) Try booting without the live DVD and see if you even get a grub boot menu. If so does it list both Windows and Ubuntu? If so will either or both boot?

(4) Depending on the outcome of (3) try some of the aforementioned options in Recovery mode. Or we may be able to enter a TTY if boot stalls using Ctrl+Alt+F1. In addition to the commands provided by ***westie457*** I find the following command frequently provides useful info:

```
sudo apt-get -f install
```

Probably need to know where those first three (or four) things lead us before deciding what to do next - sort of like following a trail of breadcrumbs.

---

### Post by kansasnoob on 2014-09-07
> **Raggylad said:**
> @Kansasnoob, @Westie457,

Before I run the procedures suggested by Westie457, it's worth noting:

- My internet connection was a wired one throughout the install (and still is - it's how I prefer to connect whenever possible)
- Grub appears to have installed successfully
- Windows is still there and working as well as it ever did
- Ubuntu appears to have installed; I'm running on the installed version, not the live disc, to do this
- Software Updater is offering me 61+MB of updates

I'll wait for your comments before doing anything rash.

Far out!

You posted while I was typing and thinking.

So while booted into your installed Ubuntu see what these show:

```
df -H
```

```
free -m
```

```
sudo parted -l
```

```
sudo dpkg --configure -a
```

```
sudo apt-get -f install
```

And I do think it's wise to run a memtest when it's convenient for you. But plan on it taking a long time.

---

### Post by Raggylad on 2014-09-07
@Kansasnoob,

Sorry about the delay - time spent shutting down, rebooting with live disc, shutting down again and booting with installed version !

Here are the results from the commands above:
```

nick@nick-HP-Compaq-6910p:~$ df -H
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        47G  3.9G   41G   9% /
none            4.1k     0  4.1k   0% /sys/fs/cgroup
udev            2.2G  4.1k  2.2G   1% /dev
tmpfs           423M  1.3M  421M   1% /run
none            5.3M     0  5.3M   0% /run/lock
none            2.2G  156k  2.2G   1% /run/shm
none            105M   37k  105M   1% /run/user
nick@nick-HP-Compaq-6910p:~$ free-m
No command 'free-m' found, did you mean:
 Command 'freedm' from package 'freedm' (universe)
free-m: command not found
nick@nick-HP-Compaq-6910p:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          4025       1201       2823        177         45        630
-/+ buffers/cache:        525       3499
Swap:         4198          0       4198
nick@nick-HP-Compaq-6910p:~$ sudo parted -l
[sudo] password for nick: 
Model: ATA MD01200-AVDW-RO (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  67.9GB  67.9GB  primary  ntfs            boot
 2      67.9GB  116GB   47.7GB  primary  ext4
 3      116GB   120GB   4403MB  primary  linux-swap(v1)


nick@nick-HP-Compaq-6910p:~$ sudo dpkg --configure -a
nick@nick-HP-Compaq-6910p:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 104 not to upgrade.
nick@nick-HP-Compaq-6910p:~$ 
```

(ignore the finger problem half way through !):)

---

### Post by kansasnoob on 2014-09-07
That mostly looks good. Notice there is no error displayed by parted -l now :D

This sort of concerns me:

> 104 not to upgrade

So lets do a simulated run to see what would happen if we tried to apply the updates:

```
sudo apt-get update
```

Then I'm curious to see this output:

```
sudo apt-get dist-upgrade -s
```

---

### Post by Raggylad on 2014-09-07
And here's what we got to that:
```

nick@nick-HP-Compaq-6910p:~$ sudo apt-get update
[sudo] password for nick: 
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty InRelease
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/main Translation-en_GB
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/restricted Translation-en_GB
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/restricted Translation-en
Ign http://gb.archive.ubuntu.com trusty InRelease                              
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://extras.ubuntu.com trusty InRelease  
Ign http://gb.archive.ubuntu.com trusty-updates InRelease
Hit http://security.ubuntu.com trusty-security Release.gpg
Hit http://extras.ubuntu.com trusty Release.gpg
Ign http://gb.archive.ubuntu.com trusty-backports InRelease
Hit http://security.ubuntu.com trusty-security Release
Hit http://extras.ubuntu.com trusty Release                           
Hit http://gb.archive.ubuntu.com trusty Release.gpg                   
Get:1 http://gb.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Hit http://gb.archive.ubuntu.com trusty-backports Release.gpg         
Hit http://security.ubuntu.com trusty-security/main Sources           
Hit http://gb.archive.ubuntu.com trusty Release 
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://extras.ubuntu.com trusty/main Sources                               
Get:2 http://gb.archive.ubuntu.com trusty-updates Release [59.7 kB]            
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://gb.archive.ubuntu.com trusty-backports Release                      
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://gb.archive.ubuntu.com trusty/main Sources                           
Hit http://security.ubuntu.com trusty-security/main Translation-en    
Hit http://gb.archive.ubuntu.com trusty/restricted Sources
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://gb.archive.ubuntu.com trusty/universe Sources              
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://gb.archive.ubuntu.com trusty/multiverse Sources
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/main i386 Packages
Ign http://extras.ubuntu.com trusty/main Translation-en
Hit http://gb.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://gb.archive.ubuntu.com trusty/universe i386 Packages
Hit http://gb.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com trusty/main Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/main Translation-en
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en
Get:3 http://gb.archive.ubuntu.com trusty-updates/main Sources [116 kB]
Get:4 http://gb.archive.ubuntu.com trusty-updates/restricted Sources [1,408 B]
Get:5 http://gb.archive.ubuntu.com trusty-updates/universe Sources [82.7 kB]
Get:6 http://gb.archive.ubuntu.com trusty-updates/multiverse Sources [3,230 B]
Get:7 http://gb.archive.ubuntu.com trusty-updates/main i386 Packages [304 kB]
Get:8 http://gb.archive.ubuntu.com trusty-updates/restricted i386 Packages [5,820 B]
Get:9 http://gb.archive.ubuntu.com trusty-updates/universe i386 Packages [199 kB]
Get:10 http://gb.archive.ubuntu.com trusty-updates/multiverse i386 Packages [8,437 B]
Hit http://gb.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://gb.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://gb.archive.ubuntu.com trusty-backports/main Sources
Hit http://gb.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://gb.archive.ubuntu.com trusty-backports/universe Sources
Hit http://gb.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://gb.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://gb.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://gb.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://gb.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com trusty-backports/universe Translation-en
Fetched 781 kB in 4s (176 kB/s)
Reading package lists... Done
nick@nick-HP-Compaq-6910p:~$ sudo apt-get dist-upgrade -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed
  linux-headers-3.13.0-35 linux-headers-3.13.0-35-generic
  linux-image-3.13.0-35-generic linux-image-extra-3.13.0-35-generic
The following packages will be upgraded:
  accountsservice apport apport-gtk evolution-data-server
  evolution-data-server-common evolution-data-server-online-accounts firefox
  fonts-opensymbol gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2
  gir1.2-edataserver-1.2 gir1.2-freedesktop gir1.2-glib-2.0 gir1.2-gtk-3.0
  gir1.2-gudev-1.0 irqbalance krb5-locales libaccountsservice0 libc-bin
  libc-dev-bin libc6 libc6-dbg libc6-dev libcamel-1.2-45 libebackend-1.2-7
  libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18 libgail-3-0 libgcrypt11
  libgirepository-1.0-1 libgpgme11 libgssapi-krb5-2 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libgudev-1.0-0 libk5crypto3 libkrb5-3 libkrb5support0
  liblzo2-2 libnm-gtk-common libnm-gtk0 liboxideqt-qmlplugin libpam-systemd
  libreoffice-avmedia-backend-gstreamer libreoffice-ogltrans
  libreoffice-pdfimport libreoffice-presentation-minimizer
  libreoffice-style-human libsmbclient libssl1.0.0 libsystemd-daemon0
  libsystemd-journal0 libsystemd-login0 libudev1 libunity-core-6.0-9
  libunity-gtk2-parser0 libunity-gtk3-parser0 libwbclient0 linux-generic
  linux-headers-generic linux-image-generic linux-libc-dev multiarch-support
  net-tools network-manager-gnome openssl python-gi python-gi-cairo
  python-gobject python-samba python3-apport python3-distupgrade python3-gi
  python3-gi-cairo python3-problem-report rsyslog samba-common
  samba-common-bin samba-libs shotwell shotwell-common smbclient
  systemd-services ubuntu-drivers-common ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk udev unity unity-gtk-module-common
  unity-gtk2-module unity-gtk3-module unity-services uno-libs3 ure
  usb-creator-common usb-creator-gtk xserver-common xserver-xorg-core
  xserver-xorg-video-intel
104 to upgrade, 4 to newly install, 0 to remove and 0 not to upgrade.
Inst libc6-dev [2.19-0ubuntu6] (2.19-0ubuntu6.3 Ubuntu:14.04/trusty-updates [i386]) []
Inst libc-dev-bin [2.19-0ubuntu6] (2.19-0ubuntu6.3 Ubuntu:14.04/trusty-updates [i386]) []
Inst linux-libc-dev [3.13.0-32.57] (3.13.0-35.62 Ubuntu:14.04/trusty-updates [i386]) []
Inst libc6-dbg [2.19-0ubuntu6] (2.19-0ubuntu6.3 Ubuntu:14.04/trusty-updates [i386]) []
Inst libc-bin [2.19-0ubuntu6] (2.19-0ubuntu6.3 Ubuntu:14.04/trusty-updates [i386]) []
Inst libc6 [2.19-0ubuntu6] (2.19-0ubuntu6.3 Ubuntu:14.04/trusty-updates [i386])
Conf libc6 (2.19-0ubuntu6.3 Ubuntu:14.04/trusty-updates [i386])
Conf libc-bin (2.19-0ubuntu6.3 Ubuntu:14.04/trusty-updates [i386])
Inst libgcrypt11 [1.5.3-2ubuntu4] (1.5.3-2ubuntu4.1 Ubuntu:14.04/trusty-updates [i386])
Inst libssl1.0.0 [1.0.1f-1ubuntu2.4] (1.0.1f-1ubuntu2.5 Ubuntu:14.04/trusty-updates [i386])
Inst udev [204-5ubuntu20.3] (204-5ubuntu20.5 Ubuntu:14.04/trusty-updates [i386]) []
Inst libudev1 [204-5ubuntu20.3] (204-5ubuntu20.5 Ubuntu:14.04/trusty-updates [i386])
Inst libk5crypto3 [1.12+dfsg-2ubuntu4] (1.12+dfsg-2ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Inst libgssapi-krb5-2 [1.12+dfsg-2ubuntu4] (1.12+dfsg-2ubuntu4.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkrb5-3 [1.12+dfsg-2ubuntu4] (1.12+dfsg-2ubuntu4.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libkrb5support0 [1.12+dfsg-2ubuntu4] (1.12+dfsg-2ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Inst libpam-systemd [204-5ubuntu20.3] (204-5ubuntu20.5 Ubuntu:14.04/trusty-updates [i386]) []
Inst systemd-services [204-5ubuntu20.3] (204-5ubuntu20.5 Ubuntu:14.04/trusty-updates [i386]) []
Inst libsystemd-daemon0 [204-5ubuntu20.3] (204-5ubuntu20.5 Ubuntu:14.04/trusty-updates [i386])
Inst libsystemd-login0 [204-5ubuntu20.3] (204-5ubuntu20.5 Ubuntu:14.04/trusty-updates [i386])
Inst libgtk-3-common [3.10.8-0ubuntu1.1] (3.10.8-0ubuntu1.2 Ubuntu:14.04/trusty-updates [all])
Inst libgail-3-0 [3.10.8-0ubuntu1.1] (3.10.8-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libgtk-3-0 [3.10.8-0ubuntu1.1] (3.10.8-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst libgpgme11 [1.4.3-0.1ubuntu5] (1.4.3-0.1ubuntu5.1 Ubuntu:14.04/trusty-updates [i386])
Inst libgudev-1.0-0 [1:204-5ubuntu20.3] (1:204-5ubuntu20.5 Ubuntu:14.04/trusty-updates [i386])
Inst liblzo2-2 [2.06-1.2ubuntu1] (2.06-1.2ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst libunity-gtk2-parser0 [0.0.0+14.04.20140403-0ubuntu1] (0.0.0+14.04.20140403-0ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst libunity-gtk3-parser0 [0.0.0+14.04.20140403-0ubuntu1] (0.0.0+14.04.20140403-0ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst libwbclient0 [2:4.1.6+dfsg-1ubuntu2.14.04.2] (2:4.1.6+dfsg-1ubuntu2.14.04.3 Ubuntu:14.04/trusty-updates [i386])
Inst linux-image-3.13.0-35-generic (3.13.0-35.62 Ubuntu:14.04/trusty-updates [i386])
Inst libsmbclient [2:4.1.6+dfsg-1ubuntu2.14.04.2] (2:4.1.6+dfsg-1ubuntu2.14.04.3 Ubuntu:14.04/trusty-updates [i386]) []
Inst smbclient [2:4.1.6+dfsg-1ubuntu2.14.04.2] (2:4.1.6+dfsg-1ubuntu2.14.04.3 Ubuntu:14.04/trusty-updates [i386]) []
Inst samba-common-bin [2:4.1.6+dfsg-1ubuntu2.14.04.2] (2:4.1.6+dfsg-1ubuntu2.14.04.3 Ubuntu:14.04/trusty-updates [i386]) []
Inst python-samba [2:4.1.6+dfsg-1ubuntu2.14.04.2] (2:4.1.6+dfsg-1ubuntu2.14.04.3 Ubuntu:14.04/trusty-updates [i386]) []
Inst samba-libs [2:4.1.6+dfsg-1ubuntu2.14.04.2] (2:4.1.6+dfsg-1ubuntu2.14.04.3 Ubuntu:14.04/trusty-updates [i386]) []
Inst samba-common [2:4.1.6+dfsg-1ubuntu2.14.04.2] (2:4.1.6+dfsg-1ubuntu2.14.04.3 Ubuntu:14.04/trusty-updates [all])
Inst ubuntu-drivers-common [1:0.2.91.5] (1:0.2.91.6 Ubuntu:14.04/trusty-updates [i386])
Inst unity-gtk-module-common [0.0.0+14.04.20140403-0ubuntu1] (0.0.0+14.04.20140403-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst unity-gtk2-module [0.0.0+14.04.20140403-0ubuntu1] (0.0.0+14.04.20140403-0ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst unity-gtk3-module [0.0.0+14.04.20140403-0ubuntu1] (0.0.0+14.04.20140403-0ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst libsystemd-journal0 [204-5ubuntu20.3] (204-5ubuntu20.5 Ubuntu:14.04/trusty-updates [i386])
Inst multiarch-support [2.19-0ubuntu6] (2.19-0ubuntu6.3 Ubuntu:14.04/trusty-updates [i386])
Conf multiarch-support (2.19-0ubuntu6.3 Ubuntu:14.04/trusty-updates [i386])
Inst net-tools [1.60-25ubuntu2] (1.60-25ubuntu2.1 Ubuntu:14.04/trusty-updates [i386])
Inst rsyslog [7.4.4-1ubuntu2] (7.4.4-1ubuntu2.1 Ubuntu:14.04/trusty-updates [i386])
Inst accountsservice [0.6.35-0ubuntu7] (0.6.35-0ubuntu7.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libaccountsservice0 [0.6.35-0ubuntu7] (0.6.35-0ubuntu7.1 Ubuntu:14.04/trusty-updates [i386])
Inst gir1.2-freedesktop [1.40.0-1ubuntu0.1] (1.40.0-1ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libgirepository-1.0-1 [1.40.0-1ubuntu0.1] (1.40.0-1ubuntu0.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst gir1.2-glib-2.0 [1.40.0-1ubuntu0.1] (1.40.0-1ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Inst irqbalance [1.0.6-2] (1.0.6-2ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst krb5-locales [1.12+dfsg-2ubuntu4] (1.12+dfsg-2ubuntu4.2 Ubuntu:14.04/trusty-updates [all])
Inst openssl [1.0.1f-1ubuntu2.4] (1.0.1f-1ubuntu2.5 Ubuntu:14.04/trusty-updates [i386])
Inst ubuntu-release-upgrader-gtk [1:0.220.2] (1:0.220.4 Ubuntu:14.04/trusty-updates [all]) []
Inst ubuntu-release-upgrader-core [1:0.220.2] (1:0.220.4 Ubuntu:14.04/trusty-updates [all]) []
Inst python3-gi-cairo [3.12.0-1] (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [i386]) []
Inst python3-gi [3.12.0-1] (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [i386]) []
Inst gir1.2-gtk-3.0 [3.10.8-0ubuntu1.1] (3.10.8-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst python3-distupgrade [1:0.220.2] (1:0.220.4 Ubuntu:14.04/trusty-updates [all])
Inst python3-problem-report [2.14.1-0ubuntu3.2] (2.14.1-0ubuntu3.3 Ubuntu:14.04/trusty-updates [all])
Inst python3-apport [2.14.1-0ubuntu3.2] (2.14.1-0ubuntu3.3 Ubuntu:14.04/trusty-updates [all])
Inst apport [2.14.1-0ubuntu3.2] (2.14.1-0ubuntu3.3 Ubuntu:14.04/trusty-updates [all])
Inst apport-gtk [2.14.1-0ubuntu3.2] (2.14.1-0ubuntu3.3 Ubuntu:14.04/trusty-updates [all])
Inst evolution-data-server-online-accounts [3.10.4-0ubuntu1.1] (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst evolution-data-server [3.10.4-0ubuntu1.1] (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst libcamel-1.2-45 [3.10.4-0ubuntu1.1] (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst evolution-data-server-common [3.10.4-0ubuntu1.1] (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [all])
Inst libedataserver-1.2-18 [3.10.4-0ubuntu1.1] (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst libebackend-1.2-7 [3.10.4-0ubuntu1.1] (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst libebook-contacts-1.2-0 [3.10.4-0ubuntu1.1] (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst libedata-book-1.2-20 [3.10.4-0ubuntu1.1] (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst libebook-1.2-14 [3.10.4-0ubuntu1.1] (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst libecal-1.2-16 [3.10.4-0ubuntu1.1] (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst libedata-cal-1.2-23 [3.10.4-0ubuntu1.1] (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst firefox [31.0+build1-0ubuntu0.14.04.1] (32.0+build1-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst fonts-opensymbol [2:102.6+LibO4.2.4-0ubuntu2] (2:102.6+LibO4.2.6.3-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst gir1.2-ebook-1.2 [3.10.4-0ubuntu1.1] (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst gir1.2-ebookcontacts-1.2 [3.10.4-0ubuntu1.1] (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst gir1.2-edataserver-1.2 [3.10.4-0ubuntu1.1] (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst gir1.2-gudev-1.0 [1:204-5ubuntu20.3] (1:204-5ubuntu20.5 Ubuntu:14.04/trusty-updates [i386])
Inst libgtk-3-bin [3.10.8-0ubuntu1.1] (3.10.8-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst network-manager-gnome [0.9.8.8-0ubuntu4.2] (0.9.8.8-0ubuntu4.3 Ubuntu:14.04/trusty-updates [i386]) []
Inst libnm-gtk0 [0.9.8.8-0ubuntu4.2] (0.9.8.8-0ubuntu4.3 Ubuntu:14.04/trusty-updates [i386]) []
Inst libnm-gtk-common [0.9.8.8-0ubuntu4.2] (0.9.8.8-0ubuntu4.3 Ubuntu:14.04/trusty-updates [all])
Inst libreoffice-ogltrans [1:4.2.4-0ubuntu2] (1:4.2.6.3-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst uno-libs3 [4.2.4-0ubuntu2] (4.2.6.3-0ubuntu1 Ubuntu:14.04/trusty-updates [i386]) [ure:i386 ]
Inst ure [4.2.4-0ubuntu2] (4.2.6.3-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst libreoffice-avmedia-backend-gstreamer [1:4.2.4-0ubuntu2] (1:4.2.6.3-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst libreoffice-presentation-minimizer [1:4.2.4-0ubuntu2] (1:4.2.6.3-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst libreoffice-style-human [1:4.2.4-0ubuntu2] (1:4.2.6.3-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst xserver-common [2:1.15.1-0ubuntu2] (2:1.15.1-0ubuntu2.1 Ubuntu:14.04/trusty-updates [all])
Inst xserver-xorg-core [2:1.15.1-0ubuntu2] (2:1.15.1-0ubuntu2.1 Ubuntu:14.04/trusty-updates [i386])
Inst unity [7.2.2+14.04.20140714-0ubuntu1] (7.2.2+14.04.20140714-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libunity-core-6.0-9 [7.2.2+14.04.20140714-0ubuntu1] (7.2.2+14.04.20140714-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst unity-services [7.2.2+14.04.20140714-0ubuntu1] (7.2.2+14.04.20140714-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst linux-image-extra-3.13.0-35-generic (3.13.0-35.62 Ubuntu:14.04/trusty-updates [i386])
Inst linux-generic [3.13.0.32.38] (3.13.0.35.42 Ubuntu:14.04/trusty-updates [i386]) []
Inst linux-image-generic [3.13.0.32.38] (3.13.0.35.42 Ubuntu:14.04/trusty-updates [i386]) []
Inst linux-headers-3.13.0-35 (3.13.0-35.62 Ubuntu:14.04/trusty-updates [all]) []
Inst linux-headers-3.13.0-35-generic (3.13.0-35.62 Ubuntu:14.04/trusty-updates [i386]) []
Inst linux-headers-generic [3.13.0.32.38] (3.13.0.35.42 Ubuntu:14.04/trusty-updates [i386])
Inst python-gi-cairo [3.12.0-1] (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [i386]) []
Inst python-gi [3.12.0-1] (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Inst python-gobject [3.12.0-1] (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst shotwell-common [0.18.0-0ubuntu4.1] (0.18.0-0ubuntu4.2 Ubuntu:14.04/trusty-updates [all]) [shotwell:i386 ]
Inst shotwell [0.18.0-0ubuntu4.1] (0.18.0-0ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Inst usb-creator-gtk [0.2.56.1] (0.2.56.2 Ubuntu:14.04/trusty-updates [i386]) []
Inst usb-creator-common [0.2.56.1] (0.2.56.2 Ubuntu:14.04/trusty-updates [i386])
Inst xserver-xorg-video-intel [2:2.99.910-0ubuntu1] (2:2.99.910-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst liboxideqt-qmlplugin [1.0.0~bzr501-0ubuntu2] (1.1.2-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst libreoffice-pdfimport [1:4.2.4-0ubuntu2] (1:4.2.6.3-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf libc-dev-bin (2.19-0ubuntu6.3 Ubuntu:14.04/trusty-updates [i386])
Conf linux-libc-dev (3.13.0-35.62 Ubuntu:14.04/trusty-updates [i386])
Conf libc6-dev (2.19-0ubuntu6.3 Ubuntu:14.04/trusty-updates [i386])
Conf libc6-dbg (2.19-0ubuntu6.3 Ubuntu:14.04/trusty-updates [i386])
Conf libgcrypt11 (1.5.3-2ubuntu4.1 Ubuntu:14.04/trusty-updates [i386])
Conf libssl1.0.0 (1.0.1f-1ubuntu2.5 Ubuntu:14.04/trusty-updates [i386])
Conf libudev1 (204-5ubuntu20.5 Ubuntu:14.04/trusty-updates [i386])
Conf udev (204-5ubuntu20.5 Ubuntu:14.04/trusty-updates [i386])
Conf libkrb5support0 (1.12+dfsg-2ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Conf libk5crypto3 (1.12+dfsg-2ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Conf libkrb5-3 (1.12+dfsg-2ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Conf libgssapi-krb5-2 (1.12+dfsg-2ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Conf libsystemd-daemon0 (204-5ubuntu20.5 Ubuntu:14.04/trusty-updates [i386])
Conf systemd-services (204-5ubuntu20.5 Ubuntu:14.04/trusty-updates [i386])
Conf libpam-systemd (204-5ubuntu20.5 Ubuntu:14.04/trusty-updates [i386])
Conf libsystemd-login0 (204-5ubuntu20.5 Ubuntu:14.04/trusty-updates [i386])
Conf libgtk-3-common (3.10.8-0ubuntu1.2 Ubuntu:14.04/trusty-updates [all])
Conf libgtk-3-0 (3.10.8-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf libgail-3-0 (3.10.8-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf libgpgme11 (1.4.3-0.1ubuntu5.1 Ubuntu:14.04/trusty-updates [i386])
Conf libgudev-1.0-0 (1:204-5ubuntu20.5 Ubuntu:14.04/trusty-updates [i386])
Conf liblzo2-2 (2.06-1.2ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libunity-gtk2-parser0 (0.0.0+14.04.20140403-0ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf libunity-gtk3-parser0 (0.0.0+14.04.20140403-0ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf libwbclient0 (2:4.1.6+dfsg-1ubuntu2.14.04.3 Ubuntu:14.04/trusty-updates [i386])
Conf linux-image-3.13.0-35-generic (3.13.0-35.62 Ubuntu:14.04/trusty-updates [i386])
Conf samba-libs (2:4.1.6+dfsg-1ubuntu2.14.04.3 Ubuntu:14.04/trusty-updates [i386])
Conf libsmbclient (2:4.1.6+dfsg-1ubuntu2.14.04.3 Ubuntu:14.04/trusty-updates [i386])
Conf samba-common (2:4.1.6+dfsg-1ubuntu2.14.04.3 Ubuntu:14.04/trusty-updates [all])
Conf smbclient (2:4.1.6+dfsg-1ubuntu2.14.04.3 Ubuntu:14.04/trusty-updates [i386])
Conf python-samba (2:4.1.6+dfsg-1ubuntu2.14.04.3 Ubuntu:14.04/trusty-updates [i386])
Conf samba-common-bin (2:4.1.6+dfsg-1ubuntu2.14.04.3 Ubuntu:14.04/trusty-updates [i386])
Conf ubuntu-drivers-common (1:0.2.91.6 Ubuntu:14.04/trusty-updates [i386])
Conf unity-gtk-module-common (0.0.0+14.04.20140403-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf unity-gtk2-module (0.0.0+14.04.20140403-0ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf unity-gtk3-module (0.0.0+14.04.20140403-0ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf libsystemd-journal0 (204-5ubuntu20.5 Ubuntu:14.04/trusty-updates [i386])
Conf net-tools (1.60-25ubuntu2.1 Ubuntu:14.04/trusty-updates [i386])
Conf rsyslog (7.4.4-1ubuntu2.1 Ubuntu:14.04/trusty-updates [i386])
Conf libaccountsservice0 (0.6.35-0ubuntu7.1 Ubuntu:14.04/trusty-updates [i386])
Conf accountsservice (0.6.35-0ubuntu7.1 Ubuntu:14.04/trusty-updates [i386])
Conf libgirepository-1.0-1 (1.40.0-1ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-glib-2.0 (1.40.0-1ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-freedesktop (1.40.0-1ubuntu0.2 Ubuntu:14.04/trusty-updates [i386])
Conf irqbalance (1.0.6-2ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf krb5-locales (1.12+dfsg-2ubuntu4.2 Ubuntu:14.04/trusty-updates [all])
Conf openssl (1.0.1f-1ubuntu2.5 Ubuntu:14.04/trusty-updates [i386])
Conf python3-distupgrade (1:0.220.4 Ubuntu:14.04/trusty-updates [all])
Conf ubuntu-release-upgrader-core (1:0.220.4 Ubuntu:14.04/trusty-updates [all])
Conf python3-gi (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-gtk-3.0 (3.10.8-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf ubuntu-release-upgrader-gtk (1:0.220.4 Ubuntu:14.04/trusty-updates [all])
Conf python3-gi-cairo (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf python3-problem-report (2.14.1-0ubuntu3.3 Ubuntu:14.04/trusty-updates [all])
Conf python3-apport (2.14.1-0ubuntu3.3 Ubuntu:14.04/trusty-updates [all])
Conf apport (2.14.1-0ubuntu3.3 Ubuntu:14.04/trusty-updates [all])
Conf apport-gtk (2.14.1-0ubuntu3.3 Ubuntu:14.04/trusty-updates [all])
Conf libcamel-1.2-45 (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf evolution-data-server-common (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [all])
Conf libedataserver-1.2-18 (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf libebackend-1.2-7 (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf evolution-data-server-online-accounts (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf libebook-contacts-1.2-0 (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf libedata-book-1.2-20 (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf libebook-1.2-14 (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf libecal-1.2-16 (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf libedata-cal-1.2-23 (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf evolution-data-server (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf firefox (32.0+build1-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf fonts-opensymbol (2:102.6+LibO4.2.6.3-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf gir1.2-edataserver-1.2 (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-ebookcontacts-1.2 (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-ebook-1.2 (3.10.4-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf gir1.2-gudev-1.0 (1:204-5ubuntu20.5 Ubuntu:14.04/trusty-updates [i386])
Conf libgtk-3-bin (3.10.8-0ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf libnm-gtk-common (0.9.8.8-0ubuntu4.3 Ubuntu:14.04/trusty-updates [all])
Conf libnm-gtk0 (0.9.8.8-0ubuntu4.3 Ubuntu:14.04/trusty-updates [i386])
Conf network-manager-gnome (0.9.8.8-0ubuntu4.3 Ubuntu:14.04/trusty-updates [i386])
Conf uno-libs3 (4.2.6.3-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf ure (4.2.6.3-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf libreoffice-ogltrans (1:4.2.6.3-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf libreoffice-avmedia-backend-gstreamer (1:4.2.6.3-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf libreoffice-presentation-minimizer (1:4.2.6.3-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf libreoffice-style-human (1:4.2.6.3-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf xserver-common (2:1.15.1-0ubuntu2.1 Ubuntu:14.04/trusty-updates [all])
Conf xserver-xorg-core (2:1.15.1-0ubuntu2.1 Ubuntu:14.04/trusty-updates [i386])
Conf unity-services (7.2.2+14.04.20140714-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libunity-core-6.0-9 (7.2.2+14.04.20140714-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf unity (7.2.2+14.04.20140714-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf linux-image-extra-3.13.0-35-generic (3.13.0-35.62 Ubuntu:14.04/trusty-updates [i386])
Conf linux-image-generic (3.13.0.35.42 Ubuntu:14.04/trusty-updates [i386])
Conf linux-headers-3.13.0-35 (3.13.0-35.62 Ubuntu:14.04/trusty-updates [all])
Conf linux-headers-3.13.0-35-generic (3.13.0-35.62 Ubuntu:14.04/trusty-updates [i386])
Conf linux-headers-generic (3.13.0.35.42 Ubuntu:14.04/trusty-updates [i386])
Conf linux-generic (3.13.0.35.42 Ubuntu:14.04/trusty-updates [i386])
Conf python-gi (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf python-gi-cairo (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [i386])
Conf python-gobject (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf shotwell-common (0.18.0-0ubuntu4.2 Ubuntu:14.04/trusty-updates [all])
Conf shotwell (0.18.0-0ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Conf usb-creator-common (0.2.56.2 Ubuntu:14.04/trusty-updates [i386])
Conf usb-creator-gtk (0.2.56.2 Ubuntu:14.04/trusty-updates [i386])
Conf xserver-xorg-video-intel (2:2.99.910-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf liboxideqt-qmlplugin (1.1.2-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf libreoffice-pdfimport (1:4.2.6.3-0ubuntu1 Ubuntu:14.04/trusty-updates [i386])
nick@nick-HP-Compaq-6910p:~$ 
```

---

### Post by kansasnoob on 2014-09-07
Please go ahead and apply those available upgrades:

```
sudo apt-get dist-upgrade
```

That includes a kernel update so you'll have to reboot afterwards, then after the reboot post the output of:

```
uname -r
```

That'll tell me if grub and initrd are updating properly.

One thing concerns me a little bit but we'll look at that closer after updating. Based on the ubiquity logs from that bug report it looked like you did choose to install the third party software, in fact that seems to be where apt puked during the install, but it looks like "extras" are being ignored:

> Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_GB

But if applying these updates goes OK we should be able to fix that super easy - I hope ;)

---

### Post by kansasnoob on 2014-09-07
I may be away from the desk for a while this afternoon, so don't think I vanished if I'm slow getting back.

---

### Post by Raggylad on 2014-09-07
Update seemed to go OK.  Here's the result of "uname -r":

```
nick@nick-HP-Compaq-6910p:~$ uname -r
3.13.0-35-generic
nick@nick-HP-Compaq-6910p:~$
```

---

### Post by kansasnoob on 2014-09-07
> **Raggylad said:**
> Update seemed to go OK.  Here's the result of "uname -r":

```
nick@nick-HP-Compaq-6910p:~$ uname -r
3.13.0-35-generic
nick@nick-HP-Compaq-6910p:~$
```

That looks great!

So lets go to System Settings > Software & Updates:

[ATTACH=CONFIG]256237[/ATTACH]

Click on the Other Software tab and make sure Independent is checked:

[ATTACH=CONFIG]256238[/ATTACH]

If you had to check that run:

```
sudo apt-get update
```

Then, whether or not you had to check that, lets see what this tells us:

```
sudo apt-get install ubuntu-restricted-extras
```

(You'll have to use the Tab key to navigate the debconf windows regarding the msft font pkgs eula)

```
sudo apt-get install ubuntu-restricted-addons
```

I'm keeping my fingers crossed.

---

### Post by Raggylad on 2014-09-07
'Independent' was already checked.

Here's what those two commands resulted in:

```
nick@nick-HP-Compaq-6910p:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for nick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cabextract gstreamer0.10-plugins-bad-multiverse libfaac0 libmjpegutils-2.1-0
  libmpeg2encpp-2.1-0 libmplex2-2.1-0 ttf-mscorefonts-installer unrar
Recommended packages:
  libavcodec-extra-53
The following NEW packages will be installed
  cabextract gstreamer0.10-plugins-bad-multiverse libfaac0 libmjpegutils-2.1-0
  libmpeg2encpp-2.1-0 libmplex2-2.1-0 ttf-mscorefonts-installer
  ubuntu-restricted-extras unrar
0 to upgrade, 9 to newly install, 0 to remove and 0 not to upgrade.
Need to get 464 kB of archives.
After this operation, 1,424 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ trusty/multiverse libfaac0 i386 1.28-6 [34.2 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe libmjpegutils-2.1-0 i386 1:2.1.0+debian-2.1 [24.0 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe libmpeg2encpp-2.1-0 i386 1:2.1.0+debian-2.1 [71.0 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe libmplex2-2.1-0 i386 1:2.1.0+debian-2.1 [45.0 kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe cabextract i386 1.4-4 [41.6 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu/ trusty/multiverse ttf-mscorefonts-installer all 3.4+nmu1ubuntu1 [27.8 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu/ trusty/multiverse gstreamer0.10-plugins-bad-multiverse i386 0.10.21-1ubuntu3 [81.3 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu/ trusty/multiverse ubuntu-restricted-extras i386 60 [2,916 B]
Get:9 http://gb.archive.ubuntu.com/ubuntu/ trusty/multiverse unrar i386 1:5.0.10-1 [137 kB]
Fetched 464 kB in 0s (555 kB/s)
Preconfiguring packages ...
Selecting previously unselected package libfaac0:i386.
(Reading database ... 195433 files and directories currently installed.)
Preparing to unpack .../libfaac0_1.28-6_i386.deb ...
Unpacking libfaac0:i386 (1.28-6) ...
Selecting previously unselected package libmjpegutils-2.1-0.
Preparing to unpack .../libmjpegutils-2.1-0_1%3a2.1.0+debian-2.1_i386.deb ...
Unpacking libmjpegutils-2.1-0 (1:2.1.0+debian-2.1) ...
Selecting previously unselected package libmpeg2encpp-2.1-0.
Preparing to unpack .../libmpeg2encpp-2.1-0_1%3a2.1.0+debian-2.1_i386.deb ...
Unpacking libmpeg2encpp-2.1-0 (1:2.1.0+debian-2.1) ...
Selecting previously unselected package libmplex2-2.1-0.
Preparing to unpack .../libmplex2-2.1-0_1%3a2.1.0+debian-2.1_i386.deb ...
Unpacking libmplex2-2.1-0 (1:2.1.0+debian-2.1) ...
Selecting previously unselected package cabextract.
Preparing to unpack .../cabextract_1.4-4_i386.deb ...
Unpacking cabextract (1.4-4) ...
Selecting previously unselected package ttf-mscorefonts-installer.
Preparing to unpack .../ttf-mscorefonts-installer_3.4+nmu1ubuntu1_all.deb ...
Unpacking ttf-mscorefonts-installer (3.4+nmu1ubuntu1) ...
Selecting previously unselected package gstreamer0.10-plugins-bad-multiverse.
Preparing to unpack .../gstreamer0.10-plugins-bad-multiverse_0.10.21-1ubuntu3_i386.deb ...
Unpacking gstreamer0.10-plugins-bad-multiverse (0.10.21-1ubuntu3) ...
Selecting previously unselected package ubuntu-restricted-extras.
Preparing to unpack .../ubuntu-restricted-extras_60_i386.deb ...
Unpacking ubuntu-restricted-extras (60) ...
Selecting previously unselected package unrar.
Preparing to unpack .../unrar_1%3a5.0.10-1_i386.deb ...
Unpacking unrar (1:5.0.10-1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for update-notifier-common (0.154.1) ...
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arial32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arialb32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/comic32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/courie32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/georgi32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/impact32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/times32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/trebuc32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/verdan32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/webdin32.exe

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Extracting cabinet: /tmp/tmprXpvc4.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: /tmp/tmppDazwA.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: /tmp/tmpXvtNHu.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: /tmp/tmpYiHaJz.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /tmp/tmpCKEOpt.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /tmp/tmpf3P1tm.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /tmp/tmpnDPjHy.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: /tmp/tmpVo92aP.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: /tmp/tmpcYJKWw.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: /tmp/tmppH7EmB.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: /tmp/tmpxLI6u5.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
Processing triggers for fontconfig (2.11.0-0ubuntu4.1) ...
Setting up libfaac0:i386 (1.28-6) ...
Setting up libmjpegutils-2.1-0 (1:2.1.0+debian-2.1) ...
Setting up libmpeg2encpp-2.1-0 (1:2.1.0+debian-2.1) ...
Setting up libmplex2-2.1-0 (1:2.1.0+debian-2.1) ...
Setting up cabextract (1.4-4) ...
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu1) ...
Setting up gstreamer0.10-plugins-bad-multiverse (0.10.21-1ubuntu3) ...
Setting up ubuntu-restricted-extras (60) ...
Setting up unrar (1:5.0.10-1) ...
update-alternatives: using /usr/bin/unrar-nonfree to provide /usr/bin/unrar (unrar) in auto mode
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
nick@nick-HP-Compaq-6910p:~$ sudo apt-get install ubuntu-restricted-addons
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-addons is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
nick@nick-HP-Compaq-6910p:~$
```

'... already the newest version.' ?!

---

### Post by kansasnoob on 2014-09-07
> **Raggylad said:**
> 'Independent' was already checked.

Here's what those two commands resulted in:

```
nick@nick-HP-Compaq-6910p:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for nick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cabextract gstreamer0.10-plugins-bad-multiverse libfaac0 libmjpegutils-2.1-0
  libmpeg2encpp-2.1-0 libmplex2-2.1-0 ttf-mscorefonts-installer unrar
Recommended packages:
  libavcodec-extra-53
The following NEW packages will be installed
  cabextract gstreamer0.10-plugins-bad-multiverse libfaac0 libmjpegutils-2.1-0
  libmpeg2encpp-2.1-0 libmplex2-2.1-0 ttf-mscorefonts-installer
  ubuntu-restricted-extras unrar
0 to upgrade, 9 to newly install, 0 to remove and 0 not to upgrade.
Need to get 464 kB of archives.
After this operation, 1,424 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ trusty/multiverse libfaac0 i386 1.28-6 [34.2 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe libmjpegutils-2.1-0 i386 1:2.1.0+debian-2.1 [24.0 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe libmpeg2encpp-2.1-0 i386 1:2.1.0+debian-2.1 [71.0 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe libmplex2-2.1-0 i386 1:2.1.0+debian-2.1 [45.0 kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe cabextract i386 1.4-4 [41.6 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu/ trusty/multiverse ttf-mscorefonts-installer all 3.4+nmu1ubuntu1 [27.8 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu/ trusty/multiverse gstreamer0.10-plugins-bad-multiverse i386 0.10.21-1ubuntu3 [81.3 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu/ trusty/multiverse ubuntu-restricted-extras i386 60 [2,916 B]
Get:9 http://gb.archive.ubuntu.com/ubuntu/ trusty/multiverse unrar i386 1:5.0.10-1 [137 kB]
Fetched 464 kB in 0s (555 kB/s)
Preconfiguring packages ...
Selecting previously unselected package libfaac0:i386.
(Reading database ... 195433 files and directories currently installed.)
Preparing to unpack .../libfaac0_1.28-6_i386.deb ...
Unpacking libfaac0:i386 (1.28-6) ...
Selecting previously unselected package libmjpegutils-2.1-0.
Preparing to unpack .../libmjpegutils-2.1-0_1%3a2.1.0+debian-2.1_i386.deb ...
Unpacking libmjpegutils-2.1-0 (1:2.1.0+debian-2.1) ...
Selecting previously unselected package libmpeg2encpp-2.1-0.
Preparing to unpack .../libmpeg2encpp-2.1-0_1%3a2.1.0+debian-2.1_i386.deb ...
Unpacking libmpeg2encpp-2.1-0 (1:2.1.0+debian-2.1) ...
Selecting previously unselected package libmplex2-2.1-0.
Preparing to unpack .../libmplex2-2.1-0_1%3a2.1.0+debian-2.1_i386.deb ...
Unpacking libmplex2-2.1-0 (1:2.1.0+debian-2.1) ...
Selecting previously unselected package cabextract.
Preparing to unpack .../cabextract_1.4-4_i386.deb ...
Unpacking cabextract (1.4-4) ...
Selecting previously unselected package ttf-mscorefonts-installer.
Preparing to unpack .../ttf-mscorefonts-installer_3.4+nmu1ubuntu1_all.deb ...
Unpacking ttf-mscorefonts-installer (3.4+nmu1ubuntu1) ...
Selecting previously unselected package gstreamer0.10-plugins-bad-multiverse.
Preparing to unpack .../gstreamer0.10-plugins-bad-multiverse_0.10.21-1ubuntu3_i386.deb ...
Unpacking gstreamer0.10-plugins-bad-multiverse (0.10.21-1ubuntu3) ...
Selecting previously unselected package ubuntu-restricted-extras.
Preparing to unpack .../ubuntu-restricted-extras_60_i386.deb ...
Unpacking ubuntu-restricted-extras (60) ...
Selecting previously unselected package unrar.
Preparing to unpack .../unrar_1%3a5.0.10-1_i386.deb ...
Unpacking unrar (1:5.0.10-1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for update-notifier-common (0.154.1) ...
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arial32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arialb32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/comic32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/courie32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/georgi32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/impact32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/times32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/trebuc32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/verdan32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/webdin32.exe

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Extracting cabinet: /tmp/tmprXpvc4.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: /tmp/tmppDazwA.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: /tmp/tmpXvtNHu.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: /tmp/tmpYiHaJz.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /tmp/tmpCKEOpt.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /tmp/tmpf3P1tm.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /tmp/tmpnDPjHy.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: /tmp/tmpVo92aP.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: /tmp/tmpcYJKWw.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: /tmp/tmppH7EmB.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: /tmp/tmpxLI6u5.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
Processing triggers for fontconfig (2.11.0-0ubuntu4.1) ...
Setting up libfaac0:i386 (1.28-6) ...
Setting up libmjpegutils-2.1-0 (1:2.1.0+debian-2.1) ...
Setting up libmpeg2encpp-2.1-0 (1:2.1.0+debian-2.1) ...
Setting up libmplex2-2.1-0 (1:2.1.0+debian-2.1) ...
Setting up cabextract (1.4-4) ...
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu1) ...
Setting up gstreamer0.10-plugins-bad-multiverse (0.10.21-1ubuntu3) ...
Setting up ubuntu-restricted-extras (60) ...
Setting up unrar (1:5.0.10-1) ...
update-alternatives: using /usr/bin/unrar-nonfree to provide /usr/bin/unrar (unrar) in auto mode
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
nick@nick-HP-Compaq-6910p:~$ sudo apt-get install ubuntu-restricted-addons
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-addons is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
nick@nick-HP-Compaq-6910p:~$
```

'... already the newest version.' ?!

That looks just fine. Both are just meta-packages that install many other smaller packages so I think you're good to go \\:D/

I'd still suggest running a memory test some time when it's convenient. I typically like to let it run for 3 to 4 hours, I've seen others recommend overnight. The results display towards the bottom of the screen.

Really kind of off-topic but since this is a fresh install I recommend turning the 'ufw' firewall on. I prefer just using the GUI which is named 'gufw' so it can be installed via CLI:

```
sudo apt-get install gufw
```

Then it shows up in System Settings as Firewall Configuration:

[ATTACH=CONFIG]256240[/ATTACH]

The default settings should be OK (if as shown there) but it's not turned on out-of-box ;)

And there are some fairly significant changes between Precise and Trusty so you should probably browse the Release Notes:

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes)

Sorry you had to go down such a winding path to get to this point.

---

### Post by Raggylad on 2014-09-07
@Kansasnoob,

Many thanks for all your support - together with that from Bashing-om and Westie457 (but there are others as well).  

It has been quite a journey but I have learned a great deal along the way - plus I now seem to have a working fresh install of 14.04.1 which is a true dual boot with Windows that doesn't rely on Wubi.  A result !

I've set up the firewall as you suggested and will run the memory test overnight some time this week.  Should I do a check disc as well ?  If so, how do I do it in Ubuntu ?  An initial search of the wiki and Launchpad hasn't given me anything.

---

### Post by westie457 on 2014-09-07
@ raggylad 
Very glad it is working for you.
Whenever you want to run 'fsck' you can do it using part of the routine posted earlier. 
Also you can run in a terminal 'sudo touch fsck /dev/sda -r'
I am not near my computer at the moment so cannot check the accuracy of the command. That command can also be run when using a Live DVD/USB.

---

### Post by kansasnoob on 2014-09-07
Glad to be of help. I'll stay subscribed to these two threads for a while in case you discover something I didn't think of.

---

### Post by Raggylad on 2014-09-09
Just to close off a couple of loose ends:

I ran Memory Test overnight - no errors

FSCK in recovery mode produced this report:

```
^[[C^[[D/dev/sda2: 211035/2916352 files (0.2% non-contiguous), 1264174/11655424 blocks
```

---

### Post by kansasnoob on 2014-09-09
I'm glad the memtest passed OK :D

No idea about FSCK - meaning I'm a dummy in that regard :redface:

---


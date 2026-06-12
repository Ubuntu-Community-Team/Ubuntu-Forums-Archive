---
title: "[SOLVED] How to repartition a flashdisk on Ubuntu"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by webmiester on 2007-12-08
Hi guys,

I had an old 10GB Hard disk I used to use with windows.  I recently upgraded my hard drive into a 60GB one, so I installed my old one on an external Hard drive casing, thus becoming a 10GB Flashdisk :)

While it was my primary Hard disk though, i partitioned it to work like 2 separate drives.  When I install it as a flashdisk, it is recognized as 2 separate disks by linux (and by windows for that matter).  Is it possible for me to repartition it via USB?

---

### Post by schmildo on 2007-12-09
> **webmiester said:**
> Hi guys,

I had an old 10GB Hard disk I used to use with windows.  I recently upgraded my hard drive into a 60GB one, so I installed my old one on an external Hard drive casing, thus becoming a 10GB Flashdisk :)

While it was my primary Hard disk though, i partitioned it to work like 2 separate drives.  When I install it as a flashdisk, it is recognized as 2 separate disks by linux (and by windows for that matter).  Is it possible for me to repartition it via USB?

*sorry just had to quote so I could see what you wrote*
Lemee get this right:

So you're running a linux machine with the main install on the new 60G HDD, and
you've whacked the 10G drive into an external case that plugs into the USB?

Assuming you are prepared to lose all the data on the old 10G it is easy to remove the seperate partitions and go back to just one partition. (If you want to keep you data on it you'd best wait until someone else comes along to help).

Sooo... [COLOR="Red"]don't proceed unless you're confident you really want to do this[/COLOR].

You can use the program called gparted which is probably in your applications menu, but I couldn't rely on mine because it kept crashing, so I had to use the command line. I'd urge you to try out the graphical partition editors first, but if you have problems go to the command line. (and to be honest, even when i've finished making partitions from the command line I usually jump back into the graphical interface to get a smug feeling of pride. (yeah i'm a bit of a linux noob)

1) First you'll need look around at what you have so you dont stuff up.
Asuming the old HDD (the external one) appears as a USB flash stick, run this command to get a better look at what's going on.

**tim@lister:~$** [COLOR="DarkSlateBlue"]fdisk -l[/COLOR]

[COLOR="SeaGreen"]Disk /dev/sda: 4110 MB, 4110416896 bytes
255 heads, 63 sectors/track, 499 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x002d693e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         427     3429846   83  Linux
/dev/sda2             428         499      578340   82  Linux swap / Solaris[/COLOR]

This is the output from my 4 Gig USB flask stick (which i partitioned in an attempt to get linux on it, but, well that's another story)

2) Just to be on the safe side, have a look at where you're 60Gig Drive is sitting, (so you know which one NOT to format)

**tim@lister:~$** [COLOR="DarkSlateBlue"]df -ah[/COLOR]
[COLOR="SeaGreen"]Filesystem            Size Used Avail Use% Mounted on
/dev/hda1             7.4G  3.9G  3.2G  56% /[/COLOR]

This is the output from my 8 Gig drive.
*sorry about the spacing i've not figured out that part of this forum site yet.*

3) Ok so it looks like I've got a harddrive on /dev/hda,
and my usb on /dev/sda, with 2 partitions, sda1, and sda2.

4) To delete the partitions on sda, and loose all data on them do this:
(hell i might as well format my USB stick anyway, so i'll do it and paste the output)

**tim@lister:~$**[COLOR="DarkSlateBlue"] sudo fdisk /dev/sda[/COLOR]

**Command (m for help):** [COLOR="DarkSlateBlue"]p[/COLOR] [COLOR="Magenta"]'This just P'rints the current partition table[/COLOR]

Disk /dev/sda: 4110 MB, 4110416896 bytes
255 heads, 63 sectors/track, 499 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x002d693e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         427     3429846   83  Linux
/dev/sda2             428         499      578340   82  Linux swap / Solaris

**Command (m for help)**: [COLOR="DarkSlateBlue"]d[/COLOR] [COLOR="Magenta"]Lets 'D'elete a partition[/COLOR]
**Partition number (1-4)**:[COLOR="DarkSlateBlue"] 1[/COLOR]

**Command (m for help):**[COLOR="DarkSlateBlue"] d[/COLOR] [COLOR="Magenta"]There is only one partition remaining at this point so I don't get a chance to select it.[/COLOR]
Selected partition 2

**Command (m for help**):[COLOR="DarkSlateBlue"] p[/COLOR] [COLOR="Magenta"]Lets have another look at the partition table for the USB stick[/COLOR]

Disk /dev/sda: 4110 MB, 4110416896 bytes
255 heads, 63 sectors/track, 499 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x002d693e

   Device Boot      Start         End      Blocks   Id  System

**Command (m for help**):[COLOR="DarkSlateBlue"] n[/COLOR] [COLOR="Magenta"]Lets make a new partition, one that goes from the start of the blockspace until the end.[/COLOR]
Command action
   e   extended
   p   primary partition (1-4)
[COLOR="DarkSlateBlue"]p[/COLOR]
**Partition number (1-4)**: [COLOR="DarkSlateBlue"]1[/COLOR]
**First cylinder (1-1019, default 1)**:[COLOR="DarkSlateBlue"] [Press Enter][/COLOR]
Using default value 1
**Last cylinder or +size or +sizeM or +sizeK (1-1019, default 1019)**: [COLOR="DarkSlateBlue"] [Press Enter][/COLOR]
Using default value 1019

**Command (m for help)**:[COLOR="DarkSlateBlue"] t[/COLOR] [COLOR="Magenta"]What 'T'ype of partition do you want?[/COLOR]
Selected partition 1
**Hex code (type L to list codes)**:[COLOR="DarkSlateBlue"] L[/COLOR] [COLOR="Magenta"]'L'ist me some options[/COLOR]

 0  Empty           1e  Hidden W95 FAT1 80  Old Minix       be  Solaris boot   
 1  FAT12           24  NEC DOS         81  Minix / old Lin bf  Solaris        
 2  XENIX root      39  Plan 9          82  Linux swap / So c1  DRDOS/sec (FAT-
 3  XENIX usr       3c  PartitionMagic  83  Linux           c4  DRDOS/sec (FAT-
 4  FAT16 <32M      40  Venix 80286     84  OS/2 hidden C:  c6  DRDOS/sec (FAT-
 5  Extended        41  PPC PReP Boot   85  Linux extended  c7  Syrinx         
 6  FAT16           42  SFS             86  NTFS volume set da  Non-FS data    
 7  HPFS/NTFS       4d  QNX4.x          87  NTFS volume set db  CP/M / CTOS / .
 8  AIX             4e  QNX4.x 2nd part 88  Linux plaintext de  Dell Utility   
 9  AIX bootable    4f  QNX4.x 3rd part 8e  Linux LVM       df  BootIt         
 a  OS/2 Boot Manag 50  OnTrack DM      93  Amoeba          e1  DOS access     
 b  W95 FAT32       51  OnTrack DM6 Aux 94  Amoeba BBT      e3  DOS R/O        
 c  W95 FAT32 (LBA) 52  CP/M            9f  BSD/OS          e4  SpeedStor      
 e  W95 FAT16 (LBA) 53  OnTrack DM6 Aux a0  IBM Thinkpad hi eb  BeOS fs        
 f  W95 Ext'd (LBA) 54  OnTrackDM6      a5  FreeBSD         ee  EFI GPT        
10  OPUS            55  EZ-Drive        a6  OpenBSD         ef  EFI (FAT-12/16/
11  Hidden FAT12    56  Golden Bow      a7  NeXTSTEP        f0  Linux/PA-RISC b
12  Compaq diagnost 5c  Priam Edisk     a8  Darwin UFS      f1  SpeedStor      
14  Hidden FAT16 <3 61  SpeedStor       a9  NetBSD          f4  SpeedStor      
16  Hidden FAT16    63  GNU HURD or Sys ab  Darwin boot     f2  DOS secondary  
17  Hidden HPFS/NTF 64  Novell Netware  b7  BSDI fs         fd  Linux raid auto
18  AST SmartSleep  65  Novell Netware  b8  BSDI swap       fe  LANstep        
1b  Hidden W95 FAT3 70  DiskSecure Mult bb  Boot Wizard hid ff  BBT            
1c  Hidden W95 FAT3 75  PC/IX          
**Hex code (type L to list codes)**: [COLOR="DarkSlateBlue"]83[/COLOR]


**Command (m for help):** [COLOR="DarkSlateBlue"]w[/COLOR] [COLOR="Magenta"]Lets save my changes[/COLOR]
The partition table has been altered!

Calling ioctl() to re-read partition table.

Syncing disks.


Ta Da!

I had to restart my machine for this to work, I think that's because I originally stuffed up and forgot to run fdisk as root (using sudo). The fdisk program has other functions, like the option to make a partition 'bootable' but I left that out in your case because I didn't think you were going to do that.

Lemme know how you go.

---

### Post by Herman on 2007-12-09
I always use GParted to do all my partitioning work. In Ubuntu, you just go 'System'-->'Administration'-->'Partition Editor', while the USB drive is already plugged in.
For some reason the GParted partition editor keeps closing after one operation though, I don;t know if that's supposed to be some kind of a safety feature for us or if it's a bug, but I do know it's awfully annoying.

It's a lot easier to use a [GParted -- LiveCD]("http://gparted.sourceforge.net/") because then you can do as many operations in a row as you need to without restarting GParted every time.

Usually, GParted will show the disk you are in, normally your first hard disk, but there's a spinbox over in the top right-hand corner you can click to show a list of other drives and select one to work on. GParted can do just about anything with disks, partitions and file systems.

By the way, an external USB hard disk drive is a little bit different from a flash memory drive. The external hard disk has a real hard disk in it, and the information (data) is written to the actual hard disk, where it is stored, not just volatile memory.  From a hard disk, data can be  often be recovered after a disaster of some kind.
Flash memory sticks, on the other hand, don't have an actual disk inside them, although they are treated by the operating system as if they were a real disk. If you ever need to run data recovery software on them, forget it, flash memory forgets everything without a trace. I think flash memory might be a little quicker to read and write than a real hard disk though, it seems faster to me, but I'm not certain of the facts and actual figures.
Both kinds of USB drives have their advantages and best uses. Flash memory is the best for quick, temporary storage, where an external USB drive is good enough to trust for use storing backups on.

Regards, Herman

---

### Post by webmiester on 2007-12-09
Wow!  Thanks so much Schmildo, you just brought me through step-by-step walk through!

That is so great!  Thanks so much :)

Actually I already erased everything on my 10GB Hard drive.  I had to repartition it because I started using it for mp3 storage for my car radio.  Apparently, when I plug it into my car radio, my car radio would recognize the smaller partition only, so I couldnt get to my songs (which were on the larger partition).  I removed the partitions by reinstalling it as my primary hard drive then ran the Windows installer to partition it.  However, I might repartition it again and Ill try to reverse the partitioning allocations using the technique you gave.  Thank you soooo much :)

Yes, Herman, Flash disks should be much faster than Hard drives.  They have no moving parts, and there is no data to transfer in and out of a disk.  Some of them can be as fast as the RAM on your computer (because they're made of the same components).  The data speed is mostly limited only by the USB port.

Theoretically, I also do think that there is no way to recover lost data from flash disks.  However, I came accross this shareware application (for windows) which was supposed to be able to do just that.  I forgot the name of the software, and I never got to test it either (so sorry for the vagueness).  I dont know how the software will do it though.

---

### Post by schmildo on 2007-12-09
No worries bro! I was entertaining myself with the colours, and I'd just recently spent alot of time partitioning so I figured I should share the joy. :)

I've heard so much about the GParted -- LiveCD that i'm going to have to give in and just download a copy. 

Oh yeah, if you're happy with everything, and it's working, remember to mark this thread as [solved] it's one of the options up above. (takes me forever to find it, but i swear it's on this page somewhere)

Rock on brother.

:guitar:

---

### Post by webmiester on 2007-12-10
> **schmildo said:**
> No worries bro! I was entertaining myself with the colours, and I'd just recently spent alot of time partitioning so I figured I should share the joy. :)

I've heard so much about the GParted -- LiveCD that i'm going to have to give in and just download a copy. 

Oh yeah, if you're happy with everything, and it's working, remember to mark this thread as [solved] it's one of the options up above. (takes me forever to find it, but i swear it's on this page somewhere)

Rock on brother.

:guitar:

Uhhhh, how do I mark it as solved?  Sorry for the ignorance :)

---

### Post by schmildo on 2007-12-10
I 'think' it's at the top of the page under 'thread-tools' I can't  see it on this thread because I didnt start it. LOL i'm not sure.

---

### Post by rcatman on 2007-12-10
Thanks! This helped a lot!! I was having problems formating my 2nd internal hard drive and this worked great.

---

### Post by v.alari on 2007-12-12
Does this mean if I have a HDD partition, not a USB HDD but IDE, that if I delete a primary partition, convert it to an extended primary partition and make 4 logical partitions on it the data is irrecoverable? And either way how to I edit my boot sequence to include other partitions?

---

### Post by schmildo on 2007-12-12
> **v.alari said:**
> Does this mean if I have a HDD partition, not a USB HDD but IDE, that if I delete a primary partition, convert it to an extended primary partition and make 4 logical partitions on it the data is irrecoverable? And either way how to I edit my boot sequence to include other partitions?

In a general sense yes, if you delete a partition the data is lost. (Technically I believe the data is still there untouched, but I am unaware of how to retreive the lost partition, there are programs that might do it)

There are programs out there that allow you to move partitions around, and resize them without losing data. (Before my windows harddrive died I used [COLOR="DarkRed"]partition magic[/COLOR] to do this)

I'm no guru at any of this and even less so on the boot sequence stuff... But I was under the impression that a computer will only allow you to have one bootable partition. (which often has to be the 'first' partition on the drive)

When you have a bootable partition on a drive, you can still access the other partitions that are not bootable after the OS is up and running, The bootable partition just has to be there so the pc can enter some kind of OS.

I think you might be talking about using [COLOR="DarkRed"]grub[/COLOR] (um... there is another one i can't recall it's name) so that you can pick which partition to boot from? I've used these programs before but I've honestly forgot how to use them... I imagine you'd have to put grub onto a bootable partition of it's own, and then when it starts up, you can boot into whatever OS you want...

Have I answered your question? (Sorry if i rambled, I wasn't too sure what you were asking)

---

### Post by schmildo on 2007-12-12
> **rcatman said:**
> Thanks! This helped a lot!! I was having problems formating my 2nd internal hard drive and this worked great.

No worries man!

Geeze It feels good to be helpful.

:)

---

### Post by webmiester on 2008-07-22
Im trying out the gparted thing, but it seems to take almost forever just "scanning dvices"

---

### Post by webmiester on 2008-07-22
Ok, I removed all the partitions using fdisk, then I made a new one also using fdisk.

When I remounted the volume, all the files from the first partition were still there.  Very strange...

---


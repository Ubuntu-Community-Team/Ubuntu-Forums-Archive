---
title: "partition problems and contradictions"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by dbd on 2007-01-02
**Problem solved, ignore this post and go down to errald's question**
> Hi,
I'm trying to install kubuntu edgy on my Dad's PC but I'm having some
strange problems with the partitioning.
Basically the problem is that QTParted and fdisk disagree about the
filesystem types and the names (when I say name I mean those like
/dev/hda3) of the partitions (I know which is which because of the
size) and even the installer contradicts with itself about the
partition's names! Also I just may have lost one of the windows
partitions, luckily it happened to have no important data on it, but
I'm scared now since all the partition tools seem to be behaving very
strangely.

Sorry for the very long post, hopefully all the really important stuff
is in the above paragraph so just scan read the rest :)

Using the installer I deleted a Fat32 partition and replaced it with a
10 Mb fat16 partition (so that the drive letters wouldn't all change
in windows, fat16 not fat32 because it wouldn't let me make a fat32
partition smaller than 500Mb) and out of the rest of the free space
left I made an ext2 partition. In the next stage of the installer I
selected that partition to be root but it complained there was no root
partition.

I figured this may be because it is ext2 and not ext3 so I quit the
installer and opened up QTParted. Using that I changed my new ext2
partition to ext3. Half way though the process it complained about
something being mounted, however I was pretty sure it was wrong, so I
ignored this and just pressed OK (it being the only option, there was
no Cancel button as far as I can remember).

After this QTParted then reported that partition to have no unknown
type and one of my windows partitions had changed to ext3! Worried I
rebooted to windows where one of my partitions was now apparently RAW,
and I could see it, but not see its size or data.

I went back to the live CD and decided to try fdisk. According to
fdisk everything was fine! It thought that the partition I had tried
to change to ext3 with QTParted was linux, and it also thought that my
lost fat32 partition was still fat32. However when I mounted that
partition using mount -t vfat it would not mount, but when I used
mount -t ext3 it mounted fine, containing only the directory
lost+found.

Also fdisk and QTParted seem to disagree on the partition names
QTParted has them listed hda1 to 9 in order of their position on the
disk, and fdisk seems to have them ordered by creation date. So my new
linux partition is hda9 in fdisk and hda6 in QTParted (I know it is
the same one because of sizes). Also the installer seems to disagree
about names, in the custom partition stage it has the same names as
specified in QTParted, but in the next stage where you decide where to
mount them it uses the fdisk names (again I can tell by size). Also
when mounting using mount the names agree with fdisk.

Here is fdisk's output for my primary hardrive:
[QUOTE]
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         392     3148708+   7  HPFS/NTFS
/dev/hda2             393        4865    35929372+   f  W95 Ext'd (LBA)
/dev/hda5             786        2060    10241406    b  W95 FAT32
/dev/hda6            2061        3335    10241406    b  W95 FAT32
/dev/hda7            3336        4865    12289693+   b  W95 FAT32
/dev/hda8             393         397       40099+   6  FAT16
/dev/hda9             398         785     3116578+  83  Linux

Partition table entries are not in disk order

and here is what QTParted makes of it:
 [IMG]http://img402.imageshack.us/img402/1579/snapshot1um6.png[/IMG]
fdisk's hda9 is the partition I attempted to change from ext2 to ext3
and it is QTParted's hda6. Also fdisks hda6 is QTParted's hda8 which I
think is the one that is RAW in windows (at least I can't find it in
windows now) and which linux will only mount if I call it ext3 and not
fat32.

So I'm not sure what to do next, I'm worried to continue because I'm
losing trust in the installer's partitioning, but I really want to get
kubuntu installed. Which partition table can I trust, and will it be
safe to try and install even though I'm not 100% certain if the
installer is using the right partition names!

Thanks for any help, sorry about the very long post.[/QUOTE]

---

### Post by norrux on 2007-01-02
I'm not new to linux; perhaps not an expert either.
 Recently, decided to try Ubuntu, after accepting the sales pitch.
 When I tried to partition my toshiba satellite 1415 30G hd, the utility
 'gparte' I believe, from the live CD of edition 6.10, froze as it started to
 resize my linux partition. I noticed the install tool balks if I try to set 'root'
 without touching the partion I intend for root. By touching I do not mean 
 setting one partition as root, I mean it appears I have to activate resize
 or move for tool to acknowledge my actions. Any ideas on this part of the
install problem.

---

### Post by dbd on 2007-01-02
norrux, you said: "the install tool balks if I try to set 'root' without touching the partion I intend for root". What do you mean, does it crash, do you get an error message? You really shouldn't have to resize a partition in order to install (as long as the root partition is at least 2Gb).

And by the way, if you have a new question its best to start a new thread rather than just adding to a current thread about somthing different, because otherwise answers could get confused. (Not that I'm complaining this time, my thread got a free bump! But generally it's bad practice and just makes it more difficult to get problems solved.)

---

### Post by errald on 2007-02-14
I'm a new Linux user, and I can't get Ubuntu 6.10 to recognize my XP partitions.
it will recognize my two hard drives, but when qtparted opens, it just scans forever and sees nothing.
i have tried using qtparted in the live cd mode, but it does the same thing.
i have winxp on hd0 with 3 patitions and data on hd1 with three partitions.
the third partition on hd1 is a main linux partition set up with bootit ng.

qtparted did not work before i formated that partition as linux with bootit ng.
i have a friend that has the same problem with edgy.

i have a compaq pressario with 2.1ghz, 512ram hd0=120g and hd1=80g

thanks in advance
earl

---

### Post by dbd on 2007-02-14
Hmmm, sounds like you've got some odd problem with your partitions. What does fdisk say? (To find out boot into linux, open up a console and then run the command:
>  sudo fdisk /dev/hda
and then press p followed by enter, and post the output here.
Also do the same thing using /dev/hdb instead of /dev/hda/

It may be worth seeing what the gparted live CD makes of it all. This is a CD which will boot a stripped down version of linux designed to give easy access to gparted, and also a few other useful partitions problems, you can get it from here:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

And, by the way, as I said above if you have a new question its best to start a new thread rather than just adding to a current thread about something different, because otherwise answers could get confused, and many people will waste time reading the top post when it is not relevant to your own quesion

---

### Post by errald on 2007-02-24
thank you, i'll get back as soon as i can about your suggestions.
i'll start a new thread on my next questions
been too busy with neighbors and outside work to get back here sooner.
also, couldn't remember where i posted my question.
too new at this stuff

started ubuntu 6.10 and looked at $ sudo fdisk /dev/hda
The number of cylinders for this disk is set to 15505.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Disk /dev/hda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2709    20480008+   c  W95 FAT32 (LBA)
/dev/hda2           15505       15505        7560   df  BootIt
/dev/hda3            8128       15504    55770120    c  W95 FAT32 (LBA)
/dev/hda4            2710        8127    40960080    c  W95 FAT32 (LBA)

Partition table entries are not in disk order


and hdb
The number of cylinders for this disk is set to 10337.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2709    20480008+   c  W95 FAT32 (LBA)
/dev/hdb2            2710        7585    36862560    c  W95 FAT32 (LBA)
/dev/hdb3            7586       10201    19776960   83  Linux
/dev/hdb4           10202       10337     1028160   82  Linux swap / Solaris

i gues its trying to tell me that i formated the disks wrong with BOOTIT NG
and i'm not sure how to correct the situation.

errald

---

### Post by dbd on 2007-02-25
> **errald said:**
> thank you, i'll get back as soon as i can about your suggestions.
i'll start a new thread on my next questions
been too busy with neighbors and outside work to get back here sooner.
also, couldn't remember where i posted my question.
too new at this stuff
No probs, there's no rush in sorting this out for me :)

> i gues its trying to tell me that i formated the disks wrong with BOOTIT NG
and i'm not sure how to correct the situation.
Hmm, I couldn't see any errors from the fdisk output. Although I've no idea why bootit ng would create a little partition of its own at the end of /dev/hda, but then again I'd never heard of bootit till today, so that may well be normal for that program.

Have you tried using the Alternate install CD, that can sometimes install on systems with partition tables that the live CD doesn't like?

---


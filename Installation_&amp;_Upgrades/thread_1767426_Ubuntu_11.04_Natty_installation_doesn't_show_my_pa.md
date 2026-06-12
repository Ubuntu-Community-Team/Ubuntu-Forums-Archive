---
title: "Ubuntu 11.04 Natty installation doesn't show my partition table"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by arman_prof on 2011-05-25
I'm web developer with fairly good tech knowledge.
First of all I'm  new to this community, but I've used your forums for my problem  researches very frequently and really appreciate the work all of you  does. Thanks for the best linux community.

I've used to use  Ubuntu 4 years ago, but it was immature for me at that time, so I've  abandoned Ubundu Os and came back to it a 2 weeks ago.
I have Windows  7 already installed. Want to mention that Wubi is not for me, I want to  dual boot without Wubi as I'm going to remove Windows 7 and reformat  that partition in week or so.
I'm stuck at the window of selecting  partition for installation of Ubuntu now. I had the same problem 2 week  ago, but after some research I'd fixed it and installed Ubuntu. Today  after some experimentation with source codes of software that I'm going  to contribute to, I ran low on disk (some 700mb was left from 8 GB  initial Ubuntu partition). After rebooting Ubuntu tried to update the  packages and everything crashed. So I've deleted the old partition from  live CD, added some more space partition from my Windows partition and  again stuck the same window but can't recall what I did 2 weeks  (linux/unix world is a little new for me, I've used to use simple things  and commands to administer linux web servers).

my parted output:
```
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print device                                                     
Model: ATA Maxtor 6V160E0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  106MB   105MB   primary  ntfs         boot
 2      106MB   96.7GB  96.6GB  primary  ntfs
 3      96.7GB  141GB   44.0GB  primary  ntfs

```my fdisk -lu output:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3cbf3cbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   188950527    94371840    7  HPFS/NTFS
/dev/sda3       188950528   274829311    42939392    7  HPFS/NTFS

```The first partition is Windows 7 (SYSTEM RESERVED partition). Maybe the proble is with it.
/dev/sda2 - Windows 7 partition
/dev/sda3 - my important files are here

I have also 18GB unallocated space at the end of partition for the Ubuntu and swap disk.
Here is screenshot where I'm stuck:
[IMG]http://img593.imageshack.us/img593/3277/screenshotfg.png[/IMG]

Any help would be appreciated. Thanks in advance.

---

### Post by oldfred on 2011-05-25
One thing to try is to run chkdsk on all your NTFS partitions. If you get errors you have to rerun until no errors as it does not fix everything on each pass. My gparted would not see my sda at all even though my XP booted. I ran chkdsk then everything was ok.

Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

Windows 7 has a hidden in windows 100MB boot.recovery partition. That is so you can boot if you want to encrypt the main install as the boot cannot be encrypted. And it has a copy of the recovery console for repairs. You probably still should have a windows repair CD any way.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by arman_prof on 2011-05-25
Hello and thanks for reply.

I've actually tried chkdsk previous time when I had the same problem. At that time I'd run 2 times without any errors and it takes about an hour each run. I can see my hard disk and partitions from everywhere on liver CD except installation. Gparted on LIVE CD does see my partitions. The last time I had done something in terminal and that actually fixed my error. The problem is that I can't recall where I had found the solution and commands and what I had done :(

---

### Post by coffeecat on 2011-05-25
You can get that blank allocate drive space window where there is residual RAID metadata where a drive was once used in RAID array. It confuses the installer. Have a look at post #5 in this thread:

[http://ubuntuforums.org/showthread.php?p=10435866#post10435866](http://ubuntuforums.org/showthread.php?p=10435866#post10435866)

The fix is here:

[http://ubuntuforums.org/showpost.php?p=9447593&postcount=3](http://ubuntuforums.org/showpost.php?p=9447593&postcount=3)

Which the OP of the first thread reposted as working for him.

---

### Post by arman_prof on 2011-05-25
Thank you very much. This has solved my issue. 2 weeks ago I've solved the issue the same way and I've even used the same post :)

command that solved the issue (for reference):
```
sudo dmraid -r -E /dev/sda (or whatever your hdd /dev/sd*)
```The command was originally found here:
[http://ubuntuforums.org/showpost.php?p=9447593&postcount=3](http://ubuntuforums.org/showpost.php?p=9447593&postcount=3)

---


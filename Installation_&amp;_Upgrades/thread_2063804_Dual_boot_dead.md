---
title: "Dual boot dead"
date: 2012-09-27
forum: Installation &amp; Upgrades
---

### Post by lgastmans on 2012-09-27
After a recent upgrade of my 12.04 installation, my windows does not boot up anymore. Part of the message is:

"Could not read from the selected boot disk.
Check boot path and disk hardware."

My hard disks:
sda - 300 GB: Movies
sdb - 1 TB: sdb1 - Music, sdb2 - Windows XP, sdb3 - Win Data and sdb4 - Ubuntu 12.04 root

I have tried running the Boot Repair utility that is available, and that has not solved the issue, actually now it is even worse in that before the boot menu even appears I get the following message:

Error: no device connected.

I then press enter and it boots Ubuntu directly, and the boot menu flashes by without stopping

Desperate for some help, scared to try further with Boot Repair.

And I have also tried running d:\bootcfg /repair from the console after booting up with the Windows Installation CD.

HELP!

---

### Post by daslinkard on 2012-09-27
> **lgastmans said:**
> After a recent upgrade of my 12.04 installation, my windows does not boot up anymore. Part of the message is:

"Could not read from the selected boot disk.
Check boot path and disk hardware."

My hard disks:
sda - 300 GB: Movies
sdb - 1 TB: sdb1 - Music, sdb2 - Windows XP, sdb3 - Win Data and sdb4 - Ubuntu 12.04 root

I have tried running the Boot Repair utility that is available, and that has not solved the issue, actually now it is even worse in that before the boot menu even appears I get the following message:

Error: no device connected.

I then press enter and it boots Ubuntu directly, and the boot menu flashes by without stopping

Desperate for some help, scared to try further with Boot Repair.

And I have also tried running d:\bootcfg /repair from the console after booting up with the Windows Installation CD.

HELP!
Personally I would say forget Windows and move solely over to Linux....but I know we cannot always have what we want....One option you can try is as follows:

[LIST=1]
[*]Start the computer by using your Windows XP CD-ROM. Press any key to boot from the CD.
[*]After the setup files are finished loading press R to repair using Recovery Console.
[*]When you are in the recovery console, select the installation to log on to (usually number 1), and then press ENTER.
[*]Login to the Administrator account by typing the password for this account, and then press ENTER.
[*]At the recovery console command prompt, type the following command, and then press ENTER: 

For Uni-Processor systems:  expand <cd-drive>:\i386\ntoskrnl.ex_  <hd-drive>:\Windows\system32\ntoskrnl.exe
 For Multi-Processor systems:  expand <cd-drive>:\i386\ntkrnlmp.ex_ <hd-drive>:\Windows\system32\ntoskrnl.exe 
**Note** In these two commands, the <cd-drive> placeholder represents the drive letter of your CD drive, and the <hd-drive> placeholder represents the drive letter of the hard disk on which windows is installed.
[*]If you receive a prompt to overwrite the file, press Y.
[*]Type exit, and press ENTER at the command prompt.
[/LIST]
**Have you thought about doing a clean install of both Windows & Ubuntu?

---

### Post by oldfred on 2012-09-27
Post the link to the BootInfo report so we can see what issues you have.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by lgastmans on 2012-10-02
Hi All,

Thank you both for the quick response. I had to struggle a bit with my setup here and therefore took a while to post back.
To make a long story short, I formatted the Windows partition and re-installed it - in the end the quickest way to set things right given my limited knowledge...
And, yes, I would love to work in Linux 100% of the time, but I have clients for whom I maintain Visual Foxpro and Delphi apps, believe it or not. So Linux 90% of the time...

Thanks for the support - much appreciated.

One more question, though:

I inserted a third hard disk and installed Windows on to this new hard disk. Since then, however, GParted does not display the partitions of the hard disk that has the Linux operating system on it, and that HAD the previous windows partition on it. I would like to retrieve the Windows partition...

These "invincible" partitions show up in Nautilus. And when I boot from the GParted CD that I once created, the same problem occurs.

Any suggestions?

---

### Post by oldfred on 2012-10-02
Is your gparted disk recent?

Ubuntu liveCD also has recent copies of gparted.

Does BIOS show all three drives. 

Are you sure you installed Windows to the new drive? Windows may install to one drive but put boot partitions on whatever drive BIOS says is the boot drive.

---

### Post by darkod on 2012-10-02
In terminal take a look at what parted says for the disks with:
sudo parted -l (small L)

---

### Post by rc0370 on 2012-10-02
> **daslinkard said:**
> Personally I would say forget Windows and move solely over to Linux....but I know we cannot always have what we want....One option you can try is as follows:

[LIST=1]
[*]Start the computer by using your Windows XP CD-ROM. Press any key to boot from the CD.
[*]After the setup files are finished loading press R to repair using Recovery Console.
[*]When you are in the recovery console, select the installation to log on to (usually number 1), and then press ENTER.
[*]Login to the Administrator account by typing the password for this account, and then press ENTER.
[*]At the recovery console command prompt, type the following command, and then press ENTER: 

For Uni-Processor systems:  expand <cd-drive>:\i386\ntoskrnl.ex_  <hd-drive>:\Windows\system32\ntoskrnl.exe
 For Multi-Processor systems:  expand <cd-drive>:\i386\ntkrnlmp.ex_ <hd-drive>:\Windows\system32\ntoskrnl.exe 
**Note** In these two commands, the <cd-drive> placeholder represents the drive letter of your CD drive, and the <hd-drive> placeholder represents the drive letter of the hard disk on which windows is installed.
[*]If you receive a prompt to overwrite the file, press Y.
[*]Type exit, and press ENTER at the command prompt.
[/LIST]
**Have you thought about doing a clean install of both Windows & Ubuntu?
I have the same problem after installing Ubuntu 12.04.1 from a CD along side Windows Vista. I can no longer boot up into Windows Vista even when I tell it to. It starts to go to Windows Vista and then it reboots and goes into Ubuntu. Any suggestions?

---

### Post by oldfred on 2012-10-02
@rc0370
Welcome to forums. Boot issues are almost always unique. Please start your own thread and post the link to BootInfo report as shown in post #3.

---

### Post by lgastmans on 2012-10-02
@rc0370: Try the Boot Repair CD, it has done a lot of good work for me in the past, and in case it does not do the job, then post the URL that it gives at the end to this forum...

@darkod: This is what "sudo parted -l" gives

Model: ATA ST3320620AS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  320GB  320GB  primary  ntfs         boot


Error: Can't have overlapping partitions.                                 

Model: ATA ST500DM002-1BD14 (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  52.4GB  52.4GB  primary  ntfs
 2      52.4GB  500GB   448GB   primary  fat32


I see an error in this listing "overlapping partitions"... Deleting the partition with the Windows install CD did this?

@oldfred: yes, all three drives show up in BIOS, and as you can see above, the new Windows install is on sdc

This is what "sudo fdisk -l" gives:
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb972df94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625141759   312570848+   7  HPFS/NTFS/exFAT
omitting empty partition (5)

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006c1a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   716802047   358400000   83  Linux
/dev/sdb2       819202048   952322047    66560000    7  HPFS/NTFS/exFAT
/dev/sdb3       952322048  1953523711   500600832    5  Extended
/dev/sdb4      1941555200  1953523711     5984256   82  Linux swap / Solaris
/dev/sdb5       952324096  1933211647   490443776   83  Linux
/dev/sdb6      1933213696  1941551103     4168704   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc8f1c8f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   102398309    51199123+   7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.
/dev/sdc2       102400000   976773119   437186560    b  W95 FAT32
```

---

### Post by oldfred on 2012-10-02
Your sdb4 is inside the extended partition. That cannot be. sdb4 must be a primary not  a logical. It probably should just be sdb7. Since it is a swap it might be easier just to delete it, but you may have to update fstab with the correct swap UUID.

But most partition tools do not work on invalid partition tables.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sdb > PTsdb.txt

Lets try this first:

You can reorder the partition with fdisk, anything after # is comment, do not type:
sudo fdisk /dev/sdb
x  # enter expert mode
f  # fix  partition table
r  # return
p  # to print
v  # to verify partition 
#if ok
w  #  write the changes to disk
q # quit

---

### Post by lgastmans on 2012-10-07
@oldfred: Thanks for the input - when I saw your message it was clear that I had a "partition mess".

I decided to wipe backup, wipe out all the partitions, and start anew. So right now I am back on a fresh install of Ubuntu and Windows. Feels good.

Again, many thanks for taking the time to respond!

oops, typo in previous message. Should read "I decided to backup my data, wipe out..."

:-)

---


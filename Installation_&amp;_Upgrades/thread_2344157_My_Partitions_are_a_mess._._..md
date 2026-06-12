---
title: "My Partitions are a mess. . ."
date: 2016-11-23
forum: Installation &amp; Upgrades
---

### Post by JustJazz on 2016-11-23
I thought I knew how to delete and resize partitions but I'm still a NOOB. . . I resized my Windows 7 partition with MinTool to make space for another flavor of Ubuntu but somehow screwed up ALL partitions and Windows boot loader. Although Windows 7 and Xubuntu both boot perfect from Grub 2 I cannot install any other Ubuntu flavor, I hit install but nothing happens, same result with 3 different distros. I'm almost sure this is partition related too:

harold@office:~$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
[sudo] password for harold: 
NAME   FSTYPE   SIZE MOUNTPOINT         LABEL
sda           149.1G                                      
&#9500;&#9472;sda1 ntfs     100M                                      System Reserved
&#9500;&#9472;sda2 ntfs    83.7G                                      Windows 7
&#9500;&#9472;sda3            1K                                      
&#9500;&#9472;sda5 ext4    63.4G /                                    Xubuntu
&#9492;&#9472;sda6 swap     1.9G [SWAP]                               
sdb             983M                                      
&#9492;&#9472;sdb1 vfat     983M /media/harold/E4AA-8D47              
sr0             4.4G /media/harold/Boot-Repair-Disk 64bit 
harold@office:~$



Also. . . I cannot run Gparted in Xubuntu, it gives me errors **Assertion (metadata_length>0) at ../../../libparted/labels/ dos.c:2313 in function add_logical_part_metadata() failed.** 

I also ran Boot Info. with link below. . .
[https://paste.ubuntu.com/23520241/](https://paste.ubuntu.com/23520241/) 

Please help this noob sort this out ](*,)

---

### Post by oldfred on 2016-11-23
From live installer shrink sda5 and create a new ext4 partition.
Then use Something Else to choose that partition as a new / (root) partition.

---

### Post by JustJazz on 2016-11-23
> **oldfred said:**
> From live installer shrink sda5 and create a new ext4 partition.
Then use Something Else to choose that partition as a new / (root) partition.

I tried Gparted from live installer again as I stated before but get error message:

**Assertion (metadata_length>0) at ../../../libparted/labels/ dos.c:2313 in function add_logical_part_metadata() failed.**

 and it will NOT open. . . if I open in Boot Info. Gparted shows only one BIG unallocated partition which is totally different from this in terminal:

harold@office:~$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
[sudo] password for harold: 
NAME   FSTYPE   SIZE MOUNTPOINT         LABEL
[B]sda           149.1G                                      
&#9500;&#9472;sda1 ntfs     100M  System Reserved
&#9500;&#9472;sda2 ntfs    83.7G                                      Windows 7
&#9500;&#9472;sda3            1K                                      
&#9500;&#9472;sda5 ext4    63.4G /                                    Xubuntu
&#9492;&#9472;sda6 swap     1.9G [SWAP][/B]                               
sdb             983M                                      
&#9492;&#9472;sdb1 vfat     983M /media/harold/E4AA-8D47              
sr0             4.4G /media/harold/Boot-Repair-Disk 64bit 
harold@office:~$

---

### Post by oldfred on 2016-11-23
Are you shrinking sda5 or sda2?
Post this:
sudo parted -l

Are you processing the shrink first, then process the add new logical partition.

---

### Post by JustJazz on 2016-11-23
> **oldfred said:**
> Are you shrinking sda5 or sda2?
Post this:
sudo parted -l

Are you processing the shrink first, then process the add new logical partition.

I can't do anything in Gparted, I cannot open Gparted in live CD or terminal. . .

---

### Post by oldfred on 2016-11-23
[https://lists.gnu.org/archive/html/bug-parted/2015-09/msg00020.html](https://lists.gnu.org/archive/html/bug-parted/2015-09/msg00020.html)

It says you must have one sector between logical partitions. Are you trying to force them without any separation?

---

### Post by JustJazz on 2016-11-30
> **oldfred said:**
> [https://lists.gnu.org/archive/html/bug-parted/2015-09/msg00020.html](https://lists.gnu.org/archive/html/bug-parted/2015-09/msg00020.html)

It says you must have one sector between logical partitions. Are you trying to force them without any separation?

All I know is I previously removed Linux Mint and Ubuntu 16.04 with Gnome 3 shell because I kept getting that login loop. After that Windows did not boot properly as something in the re-partitioning process affected my Windows 7 bootloader. Installing Xubuntu allowed me to boot Windows 7 via Grub 2 so. . . I tried resizing Windows 7 partition to make unallocated space to install another Ubuntu flavor. I cannot open gparted in Xubuntu or with install DVD hell. . . I cannot install anything Fred. . .

---

### Post by oldfred on 2016-11-30
How did you resize Windows?
You have to run chkdsk after any NTFS partition resize, otherwise the Linux NTFS driver cannot see the NTFS partition.
Always best to use Windows tools for Windows and Linux tools for Linux.
Or resize Windows with Windows tools & reboot immediately so it can run chkdsk.

So I suspect issue is with your NTFS partitions. Most Windows repairs cannot be done from Linux, you need to use your Windows repair/recovery disk or repair console in Windows installer to fix Windows.

---

### Post by JustJazz on 2016-11-30
> **oldfred said:**
> How did you resize Windows?
You have to run chkdsk after any NTFS partition resize, otherwise the Linux NTFS driver cannot see the NTFS partition.
Always best to use Windows tools for Windows and Linux tools for Linux.
Or resize Windows with Windows tools & reboot immediately so it can run chkdsk.

So I suspect issue is with your NTFS partitions. Most Windows repairs cannot be done from Linux, you need to use your Windows repair/recovery disk or repair console in Windows installer to fix Windows.

I used Mintool to delete the other two OS. I resized, hit apply, rebooted to repair console in Windows where Windows supposedly fixed my issue. Windows 7 came installed on this system so I don't have a repair/recovery disk. . .

---

### Post by oldfred on 2016-11-30
So does Windows boot ok?
If so I might still create a Windows repair disk. But you mintool should do many Windows repairs.

 Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm) 
   [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive](http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive)
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Also post this:
sudo parted -l
sudo fdisk -lu
just to see if they report errors also.

---

### Post by JustJazz on 2016-11-30
> **oldfred said:**
> So does Windows boot ok?
If so I might still create a Windows repair disk. But you mintool should do many Windows repairs.

 Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm) 
   [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive](http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive)
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Also post this:
sudo parted -l
sudo fdisk -lu
just to see if they report errors also.

Windows boots ok. If I remember correctly [COLOR=#000000]chkdsk[/COLOR] was ran before boot which didn't report and partition problems. Report below:

```
harold@office:~$ sudo fdisk -lu[sudo] password for harold: 
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6f06ecd2


Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048    206847    204800  100M  7 HPFS/NTFS/exFAT
/dev/sda2          206848 175722495 175515648 83.7G  7 HPFS/NTFS/exFAT
/dev/sda3       175724543 312580095 136855553 65.3G  f W95 Ext'd (LBA)
/dev/sda5       175724544 308656127 132931584 63.4G 83 Linux
/dev/sda6       308656128 312580095   3923968  1.9G 82 Linux swap / Solaris



```

---

### Post by oldfred on 2016-11-30
Fdisk shows no errors.
Does parted show errors as it is the same as gparted without gui?

---

### Post by JustJazz on 2016-11-30
> **oldfred said:**
> Fdisk shows no errors.
Does parted show errors as it is the same as gparted without gui?
This is what parted shows:

```
harold@office:~$ sudo parted -lBacktrace has 14 calls on stack:
  14: /lib/x86_64-linux-gnu/libparted.so.2(ped_assert+0x44) [0x7f5b057f1ea4]
  13: /lib/x86_64-linux-gnu/libparted.so.2(+0x1e45f) [0x7f5b0580545f]
  12: /lib/x86_64-linux-gnu/libparted.so.2(+0xf8ba) [0x7f5b057f68ba]
  11: /lib/x86_64-linux-gnu/libparted.so.2(ped_disk_add_partition+0x25f) [0x7f5b057f71af]
  10: /lib/x86_64-linux-gnu/libparted.so.2(+0x1dd4f) [0x7f5b05804d4f]
  9: /lib/x86_64-linux-gnu/libparted.so.2(+0x1dde0) [0x7f5b05804de0]
  8: /lib/x86_64-linux-gnu/libparted.so.2(+0x1dd89) [0x7f5b05804d89]
  7: /lib/x86_64-linux-gnu/libparted.so.2(+0x1ed75) [0x7f5b05805d75]
  6: /lib/x86_64-linux-gnu/libparted.so.2(ped_disk_new+0x48) [0x7f5b057f6dd8]
  5: parted(+0x7343) [0x55d498620343]
  4: parted(+0x6c3b) [0x55d49861fc3b]
  3: parted(main+0x13a4) [0x55d49861f194]
  2: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0) [0x7f5b04fcf830]
  1: parted(_start+0x29) [0x55d49861f1d9]




You found a bug in GNU Parted! Here's what you have to do:


Don't panic! The bug has most likely not affected any of your data.
Help us to fix this bug by doing the following:


Check whether the bug has already been fixed by checking
the last version of GNU Parted that you can find at:


	http://ftp.gnu.org/gnu/parted/


Please check this version prior to bug reporting.


If this has not been fixed yet or if you don't know how to check,
please visit the GNU Parted website:


	http://www.gnu.org/software/parted


for further information.


Your report should contain the version of this release (3.2)
along with the error message below, the output of


	parted DEVICE unit co print unit s print


and the following history of commands you entered.
Also include any additional information about your setup you
consider important.


Assertion (metadata_length > 0) at ../../../libparted/labels/dos.c:2313 in
function add_logical_part_metadata() failed.


Aborted (core dumped)
```

---

### Post by oldfred on 2016-11-30
Parted obviously has major errors.
Not sure if bug or not.

Does this show same errors?
parted DEVICE unit co print unit s print
Should be this which gives two listing of parted unit & sectors:
sudo parted /dev/sda unit co print unit s print

What versions like this?
fred@Asusz97:~$ dpkg -s parted | grep Version
Version: 3.2-15
fred@Asusz97:~$ dpkg -s gparted | grep Version
Version: 0.25.0-1

---

### Post by JustJazz on 2016-11-30
> **oldfred said:**
> Parted obviously has major errors.
Not sure if bug or not.

Does this show same errors?
parted DEVICE unit co print unit s print
Should be this which gives two listing of parted unit & sectors:
sudo parted /dev/sda unit co print unit s print

What versions like this?
fred@Asusz97:~$ dpkg -s parted | grep Version
Version: 3.2-15
fred@Asusz97:~$ dpkg -s gparted | grep Version
Version: 0.25.0-1

```
sudo parted /dev/sda unit co print unit s print
```

Gives same error in previous post.

```
dpkg -s parted | grep Version
```

Version: 3.2-15

I really don't have any data on the Xubuntu partition so would uninstalling/reinstall Xubuntu solve my problem. If so I'll still be tasked with creating extra partitions to try other OS which I still don't fully understand partitioning?

---

### Post by oldfred on 2016-11-30
You have the same versions of parted & gparted I have or the defaults in 16.04.

If partitioner does not work, you will not be able to install, even auto install will want to in background see partitions.
And another install only needs another / (root) partition but again you have to be able to use partition tools.

[SIZE=1]error on libparted/labels[/SIZE]
Parted uses labels for both just a description of a partition, and for whether it is gpt or MBR(msdos).
Did you ever have gpt data on drive?
This error may be cause drive has gpt data, even though drive is MBR. That then creates conflicts which it does not know how to handle.

Post this, but do not write any data with w command. This is the gpt partitioning tool and will show some info also. It can convert to gpt, but then you break Windows BIOS boot as Windows only boot in BIOS mode from MBR.
sudo gdisk -l /dev/sda

---

### Post by JustJazz on 2016-12-01
> **oldfred said:**
> You have the same versions of parted & gparted I have or the defaults in 16.04.

If partitioner does not work, you will not be able to install, even auto install will want to in background see partitions.
And another install only needs another / (root) partition but again you have to be able to use partition tools.

[SIZE=1]error on libparted/labels[/SIZE]
Parted uses labels for both just a description of a partition, and for whether it is gpt or MBR(msdos).
Did you ever have gpt data on drive?
This error may be cause drive has gpt data, even though drive is MBR. That then creates conflicts which it does not know how to handle.

I'm not sure I follow you about gpt data on drive?

> [COLOR=#000000]*You have the same versions of parted & gparted I have or the defaults in 16.04.*[/COLOR]

Yes I have the same versions you have. . .

> [COLOR=#000000]*Post this, but do not write any data with w command. This is the gpt partitioning tool and will show some info also. It can convert to gpt, but then you break Windows BIOS boot as Windows only boot in BIOS mode from MBR.*[/COLOR]
[COLOR=#000000]*sudo gdisk -l /dev/sda*[/COLOR]

I don't want to break Windows. . .

```
harold@office:~$ sudo gdisk -l /dev/sda[sudo] password for harold: 
GPT fdisk (gdisk) version 1.0.1


Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present




***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************


Disk /dev/sda: 312581808 sectors, 149.0 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 7A90003D-733C-49E2-B681-2BB52C1D2DD8
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 312581774
Partitions will be aligned on 2048-sector boundaries
Total free space is 5741 sectors (2.8 MiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   0700  Microsoft basic data
   2          206848       175722495   83.7 GiB    0700  Microsoft basic data
   5       175724544       308656127   63.4 GiB    8300  Linux filesystem
   6       308656128       312580095   1.9 GiB     8200  Linux swap
harold@office:~$
```

---

### Post by oldfred on 2016-12-01
Found invalid GPT

If that is the case, run this.
FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda 

We want to remove any invalid gpt data so it is correctly MBR.

---

### Post by JustJazz on 2016-12-01
> **oldfred said:**
> Found invalid GPT

If that is the case, run this.
FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda 

We want to remove any invalid gpt data so it is correctly MBR.

I'm sorry Fred, I'm an idiot as this is ALL so confusing. . . I don't know what to do inside of Fixparts as I'm scared I will break things beyond repair:confused:

---

### Post by oldfred on 2016-12-01
Fixparts has good instructions. You just need to follow them.

But backup of current MBR partition table is vital. Or back up is always important if you are using a computer. In your case the example with sdc should be changed to sda. 
Not sure if you need sudo or not with Ubuntu for these commands.

 [FONT=arial]sfdisk -d /dev/sda > parts.txt[/FONT][FONT=arial]

Then you need to run fixparts using sda.
fixparts /dev/sda
[/FONT]

---

### Post by JustJazz on 2016-12-06
Sorry Fred but I don't know where I'm going here, I don't know which partition(s) to change etc. but hey. . . I did manage to save [COLOR=#000000][FONT=arial]sfdisk -d /dev/sda > parts.txt[/FONT][/COLOR]:confused:

```
FixParts 1.0.1

Loading MBR data from /dev/sda


MBR command (? for help): p


** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!


** Extended partitions are not displayed, but will be generated as required.


Disk size is 312581808 sectors (149.0 GiB)
MBR disk identifier: 0x6F06ECD2
MBR partitions:


                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048       206847   primary              Y      0x07
   2                206848    175722495   primary              Y      0x07
   5             175724544    308656127   logical     Y        Y      0x83
   6             308656128    312580095   primary              Y      0x82


MBR command (? for help): ?
a    toggle the active/boot flag
c    recompute all CHS values
l    set partition as logical
o    omit partition
p    print the MBR partition table
q    quit without saving changes
r    set partition as primary
s    sort MBR partitions
t    change partition type code
w    write the MBR partition table to disk and exit



```

---

### Post by oldfred on 2016-12-06
With MBR only 1 thru 4 can be primary and all from 5 & up must be logical. 
Change 6 to logical and write the changes.

---

### Post by JustJazz on 2016-12-06
> **oldfred said:**
> With MBR only 1 thru 4 can be primary and all from 5 & up must be logical. 
Change 6 to logical and write the changes.

I'm not allowed to make any changes to 6, I get this message:
```
** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 312581808 sectors (149.0 GiB)
MBR disk identifier: 0x6F06ECD2
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048       206847   primary              Y      0x07
   2                206848    175722495   primary              Y      0x07
   5             175724544    308656127   logical     Y        Y      0x83
   6             308656128    312580095   primary              Y      0x82

MBR command (? for help): l
Partition to set as logical: 6
Specified change is not legal! Aborting change!


```

---

### Post by oldfred on 2016-12-06
Is sda6 swap?
If you write it as primary it may convert things. 
If you have to write it, then do it. But I might then delete & recreate swap.
Then swap will have a new UUID and we have to update fstab with new UUID.

---

### Post by JustJazz on 2016-12-06
I rolled the dice again, this time after 6 "partition set as logical" I immediately selected "w". . . got confirmation of changes then reboot. Checked partitions:
```
MBR disk identifier: 0x6F06ECD2MBR partitions:


                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048       206847   primary              Y      0x07
   2                206848    175722495   primary              Y      0x07
   3             308656128    312580095   primary              Y      0x82
   5             175724544    308656127   logical     Y        Y      0x83
```

> **oldfred said:**
> Is sda6 swap?

sda3 is now swap:

```
harold@office:~$ lsblk -lNAME MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda    8:0    0 149.1G  0 disk 
sda1   8:1    0   100M  0 part 
sda2   8:2    0  83.7G  0 part 
sda3   8:3    0   1.9G  0 part [SWAP]
sda5   8:5    0  63.4G  0 part /
```


> **oldfred said:**
> But I might then delete & recreate swap.
Then swap will have a new UUID and we have to update fstab with new UUID.
And just how do I update fstab with new UUID?

---

### Post by oldfred on 2016-12-07
If system boots, it should boot but give errors on swap:

#Find new UUID:
 sudo blkid -o list 

#copy & paste into fstab replacing old UUID
sudo nano /etc/fstab 

#If from live installer, you have to mount your install and edit from that mount.
 sudo mount /dev/sda5 /mnt
sudo nano /mnt/etc/fstab

#My fstab entry for swap, note # makes line comment:.

# swap was on /dev/sda4 during installation
UUID=[COLOR=#ff0000]7f429d54-b2e9-417a-ab13-b93af50f5159[/COLOR] none            swap    sw              0       0

---

### Post by JustJazz on 2016-12-08
> **oldfred said:**
> If system boots, it should boot but give errors on swap:
#Find new UUID:
 sudo blkid -o list

sudo blkid -o list

```
 harold@office:~$ sudo blkid -o list[sudo] password for harold: 
device                fs_type   label      mount point               UUID
---------------------------------------------------------------------------------------------------------
/dev/sda1             ntfs      System Reserved (not mounted)        5EC8245BC8243425
/dev/sda2             ntfs      Windows 7  (not mounted)             01D242E028CEE180
/dev/sda3             swap                 [SWAP]                    2eb67e22-6ac4-4b2c-9dda-af7ca9f8c5e4
/dev/sda5             ext4      Xubuntu    /                         b6fa1184-e9dc-499a-a986-74703ccf1b3a
harold@office:~$ sudo mount /dev/sda5 /mnt
```

> **oldfred said:**
> #copy & paste into fstab replacing old UUID
sudo nano /etc/fstab

sudo nano /etcfstab

When I open fstab this is what I got. . . 

```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=b6fa1184-e9dc-499a-a986-74703ccf1b3a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2eb67e22-6ac4-4b2c-9dda-af7ca9f8c5e4 none            swap    sw              0       0

```

Not sure what to edit here since the UUID for swap is the same as blkid -o list?

Since /dev/sda5 is no longer swap partition should I change to /dev/sda3?

---

### Post by oldfred on 2016-12-08
That looks ok then. I thought when it changed from sda5 to sda3 the UUID might change.
It looks like it did not, so everything is ok. Description/comment is just a note on where it was. UUID is what is critical.

Now can you shrink sda5 and make a new sda6?

Normally / & swap are both logical partitions inside the extended, but do not have to be.

---

### Post by JustJazz on 2016-12-09
> **oldfred said:**
> That looks ok then. I thought when it changed from sda5 to sda3 the UUID might change.
It looks like it did not, so everything is ok. Description/comment is just a note on where it was. UUID is what is critical.

Now can you shrink sda5 and make a new sda6?

Normally / & swap are both logical partitions inside the extended, but do not have to be.

Thank you so much Fred, my partitions are sorted out finally. I really hope this thread helps other users. . .

I shrank sda5 and made a new sda6 partition, successfully installed Ubuntu Gnome. After navigating to Additional Settings and selecting the Nvidia Driver 304.132 option, I didn't get the chance to install Nvidia Server Settings before having to reboot to a black screen again ](*,)](*,)](*,) Xubuntu boots and runs perfect because I was able to install Nvidia Server Settings before the black screen of course. . .

Edit: I'm getting the login screen loop(guest too) when attempting Gnome, I can access terminal. I updated Nvidia to same driver as Xubuntu 304.132, tried nomodeset, still login screen loop?

---

### Post by oldfred on 2016-12-09
I missed what nVidia card/chip you have.
       lspci | grep VGA 
      
 ubuntu-drivers devices 

You can confirm what nVidia driver is correct.

 Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers) 

If you install one nVidia driver, but change to a different one, you must totally purge all old nVidia drivers. New install will conflict with old, it does not automatically replace.

---

### Post by JustJazz on 2016-12-09
> **oldfred said:**
> I missed what nVidia card/chip you have.
       lspci | grep VGA 
      
 ubuntu-drivers devices 

You can confirm what nVidia driver is correct.

 Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers) 

If you install one nVidia driver, but change to a different one, you must totally purge all old nVidia drivers. New install will conflict with old, it does not automatically replace.

```
Nvidia GeForce 6150SE nForce 430

nvidia-304, 304.132, 4.4.0-21-generic, i686: installed
nvidia-304, 304.132, 4.4.0-50-generic, i686: installed
```
Totally purged all old Nvidia drivers followed with a reboot but still get login screen loop. . . it's weird, I never encounter this problem when I triple booted Windows 7, Linux and Ubuntu(gnome shell) in the past. . .

---

### Post by oldfred on 2016-12-09
That should be correct driver.
       Legacy drivers by GPU model 
[URL="http://www.nvidia.com/object/IO_32667.html"]http://www.nvidia.com/object/IO_32667.html

      [/URL]
 #What is installed
dpkg -l | grep -i nvidia
dkms status 
    [URL="http://www.nvidia.com/object/IO_32667.html"]
[/URL]

---

### Post by JustJazz on 2016-12-09
> **oldfred said:**
> That should be correct driver.
       Legacy drivers by GPU model 
[URL="http://www.nvidia.com/object/IO_32667.html"]http://www.nvidia.com/object/IO_32667.html

      [/URL]
 #What is installed
dpkg -l | grep -i nvidia
dkms status 
    [URL="http://www.nvidia.com/object/IO_32667.html"]
[/URL]
So I do have the correct driver installed?

dkms status is same as previous post:

```
nvidia-304, 304.132, 4.4.0-21-generic, i686: installed
nvidia-304, 304.132, 4.4.0-50-generic, i686: installed
```

dpkg -l | grep -i nvidia:

Attached below, don't know how to copy from terminal tty1. . .

---

### Post by oldfred on 2016-12-09
From what I know that looks ok.
Do not know about cuda & other drivers.

---

### Post by JustJazz on 2016-12-10
> **oldfred said:**
> From what I know that looks ok.
Do not know about cuda & other drivers.
Great. . . so how do I solve this Ubuntu(gnome) login loop?

---

### Post by oldfred on 2016-12-10
I am out of ideas, but those that know nVidia issues and perhaps log in issues will not be looking a thread titled Partitions are a mess.

Best to start new thread with your issue in title.
[https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by JustJazz on 2016-12-10
> **oldfred said:**
> I am out of ideas, but those that know nVidia issues and perhaps log in issues will not be looking a thread titled Partitions are a mess.

Best to start new thread with your issue in title.
[https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

Thanks for your time and patience Fred, you really helped me out a lot=d>

---

### Post by superkid333 on 2017-04-07
Hi oldFred and JustJazz,

Just wanted to thank you both for going through this exercise and share my experience. Your information was helpful to say the least. 

I arrived at this page because I wanted to extend the size of my /home partition. I dual boot Windows 10 along side Ubuntu 16.10, grub2 loader works fine. I had to resize my Windows partition, which I did using "Minipartition" a tool for windows. I thought I was done! In Ubuntu, when I ran "disks" I could see the unallocated space (a solid 250 GB), but I got an error loading GParted in Ubuntu. 

"[COLOR=#333333][FONT=monospace]Assertion (metadata_length > 0) at ../../.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]./libparted/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]labels/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]dos.c:2313 in function add_logical_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]part_metadata([/FONT][/COLOR][COLOR=#333333][FONT=monospace]) failed."

[/FONT][/COLOR]JustJazz, I'm sure you remember this error. I went through all the same steps OldFred described, gdisk -l /dev/sda and found I had invalid GPT and valid MBR. I installed Fixparts to clean that up. I'm not sure if it did anything, because there was no output from Fixparts saying "Hey cleaned up that GPT buddy, go get some coffee!". I simply ran it, reviewed the partitions, they looked good, and then I saved it by "w" to write the partition table. 

I rebooted and then Gparted loaded. Now I will attempt to resize my /home partition. I'll let you know how it goes. Keep this information alive. Excellent work team!

---

### Post by superkid333 on 2017-04-07
As part of my update, apparently I lost my /swap partition.
[U][B]
my old partition table:[/B][/U]

```
label: dos
label-id: 0xfc98230b
device: /dev/sda
unit: sectors


/dev/sda1 : start=        2048, size=     1024000, type=7, bootable
/dev/sda2 : start=     1026048, size=    12582912, type=27
/dev/sda3 : start=    13608960, size=   629962752, type=7
/dev/sda4 : start=  1111177215, size=   842346497, type=f
/dev/sda5 : start=  1111177216, size=    39999488, type=83
/dev/sda6 : start=  1151176704, size=    31997952, type=82
/dev/sda7 : start=  1183176704, size=   770347008, type=83

_**New partition table:**_
label: dos
label-id: 0xfc98230b
device: /dev/sda
unit: sectors


/dev/sda1 : start=        2048, size=     1024000, type=7, bootable
/dev/sda2 : start=     1026048, size=    12582912, type=27
/dev/sda3 : start=    13608960, size=   629962752, type=7
/dev/sda4 : start=  1111177215, size=   842346497, type=f
/dev/sda5 : start=  1111177216, size=    39999488, type=83
/dev/sda6 : start=  1183176704, size=   770347008, type=83


```
I'm trying to figure out how to get it back at this point. I think Fixparts may have turned it off. I had a 16GB swap, which Gparted now shows as unallocated space.

---

### Post by wildmanne39 on 2017-04-07
You never need a swap partition that large and you can just create a swap file, in fact from 17.04 and on there will be no more swap partitions just swap files.
[https://help.ubuntu.com/community/SwapFaq#How_do_I_add_a_swap_file.3F](https://help.ubuntu.com/community/SwapFaq#How_do_I_add_a_swap_file.3F)

---

### Post by wildmanne39 on 2017-04-07
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by superkid333 on 2017-04-08
Ok, I can't figure out how to get my swap back. Gparted sees the 16GB as "unallocated" space but won't let me modify it. I understand that /dev/sda6 was previously my swap and it looks as if when I used Fixparts, the swap was "omitted" which I should have changed that. I am trying to restore (yes I backed it up) and then do it again.

---

### Post by superkid333 on 2017-04-08
Thank you for the advice, I will change to a swap file once 17.04 hits. 

For now, what do I do with this 16GB partition that is in the middle of my logical extended partition? :(

And thanks for the info about code block, didn't know that.

---


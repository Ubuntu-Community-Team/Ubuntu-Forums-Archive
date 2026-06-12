---
title: "Unable to create ext4 partition in un-allocated space during Ubuntu 16.04.1 installa"
date: 2016-07-30
forum: Installation &amp; Upgrades
---

### Post by americast on 2016-07-30
Hello everyone,
  I was trying to install Ubuntu 16.04.1 LTS on a Lenovo ThinkPad laptop  (2GB RAM, 2.3 GHz processor). I already have Windows installed with an  un-allocated space of 258 GB after the Windows C: drive. During  installation, I just used a part of the free space (around 120 GB) and  partitioned it into three halves:
- 2 GB for swap
- 100 GB for /home and
- 18 GB for /

During installation, I got notified that the swap partition could not be  created and the installation aborted. I restored all the free space  using gparted and tried installing Ubuntu again, this time without  creating a partition for swap. Again during installation, I got an error  that ext4 partition could not be created. The installer aborted  again...

sudo parted /dev/sda "print free"gives:

```
ubuntu@ubuntu:~$ sudo parted /dev/sda "print free"
Model: ATA ST320LT020-9YG14 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1049kB  1016kB  primary
 2      1049kB  106MB   105MB   primary  ntfs         boot
 3      106MB   43.0GB  42.8GB  primary  ntfs
        43.0GB  320GB   277GB            Free Space
```

I had allocated all the free space into an extended partition and then  created those three logical partitions. Gparted had failed to create the  partitions. In the Ubuntu installer, there is no option to create an  extended partition. It is done automatically. The presence of an  extended partition was clearly visible in gparted when the installation  via the Ubuntu installer had failed...

When starting gparted, I am getting this message: "The driver descriptor  says the physical block size is 2048 bytes, but Linux says it is 512  bytes." I had chosen to "Ignore" it.

Gparted looks like this after an installation failure. Note that I had  created these partitions by choosing "Something Else" in the Ubuntu  installer:

[https://www.dropbox.com/s/idqo8ac5gz...46-46.png?dl=0]("https://www.dropbox.com/s/idqo8ac5gzqqope/Screenshot%20from%202016-07-30%2014-46-46.png?dl=0")

I am not able to create ext4 partitions even using gparted. Any help would be appreciated...
Gramercy...

---

### Post by blackbird34 on 2016-07-30
_Edit: this post is irrelevant, sorry_

Hi! Could you boot from the Live USB system ("Try Ubuntu") and open Gparted again, and go to View > Device information and tell us what's there? (See screenshot - My Ubuntu is in Spanish but it should give you an idea. "tabla de particiones" means "partition table"). 

[ATTACH=CONFIG]270450[/ATTACH]

If it is "gpt" rather than "msdos" (which is likely - its currently the most used form of partition table = most recent technique for organizing partitions) then you do not need to create extended and logical partitions. You may have followed a guide containing outdated information (?). 

[Source]("http://unix.stackexchange.com/a/53293") 

I hope this helps

---

### Post by nikefalcon on 2016-07-30
> **blackbird34 said:**
> 
If it is "gpt" rather than "msdos" (which is likely - its currently the  most used form of partition table = most recent technique for organizing  partitions) then you do not need to create extended and logical  partitions. You may have followed a guide containing outdated  information (?). 

The parted output shows the partition table to be "msdos" so we already know it is MBR.

> **americast said:**
> Hello everyone,
  I was trying to install Ubuntu 16.04.1 LTS on a Lenovo ThinkPad laptop   (2GB RAM, 2.3 GHz processor). I already have Windows installed with an   un-allocated space of 258 GB after the Windows C: drive. During   installation, I just used a part of the free space (around 120 GB) and   partitioned it into three halves:
- 2 GB for swap
- 100 GB for /home and
- 18 GB for /

During installation, I got notified that the swap partition could not be   created and the installation aborted. I restored all the free space   using gparted and tried installing Ubuntu again, this time without   creating a partition for swap. Again during installation, I got an error   that ext4 partition could not be created. The installer aborted   again...

sudo parted /dev/sda "print free"gives:

```
ubuntu@ubuntu:~$ sudo parted /dev/sda "print free"
Model: ATA ST320LT020-9YG14 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1049kB  1016kB  primary
 2      1049kB  106MB   105MB   primary  ntfs         boot
 3      106MB   43.0GB  42.8GB  primary  ntfs
        43.0GB  320GB   277GB            Free Space
```

I had allocated all the free space into an extended partition and then   created those three logical partitions. Gparted had failed to create the   partitions. In the Ubuntu installer, there is no option to create an   extended partition. It is done automatically. The presence of an   extended partition was clearly visible in gparted when the installation   via the Ubuntu installer had failed...

When starting gparted, I am getting this message: "The driver descriptor   says the physical block size is 2048 bytes, but Linux says it is 512   bytes." I had chosen to "Ignore" it.

Gparted looks like this after an installation failure. Note that I had   created these partitions by choosing "Something Else" in the Ubuntu   installer:

[https://www.dropbox.com/s/idqo8ac5gz...46-46.png?dl=0]("https://www.dropbox.com/s/idqo8ac5gzqqope/Screenshot%20from%202016-07-30%2014-46-46.png?dl=0")

I am not able to create ext4 partitions even using gparted. Any help would be appreciated...
Gramercy...

1) Since you are using MBR, the fourth partition(**sda4**) has to span the entire unused region after your windows partition(**sda3,** isn't it?). That's the only way you are going to be able to use the full capacity of the HDD as MBR only allows for up to 4 partitions(sda1 through sda4). You can make all your new logical partitions inside this extended one, that is **sda4**. These partitions shall be numbered upwards from sda5.

2) I do not know what exactly went wrong when you tried through the installer, so I'd suggest booting a live cd/usb and using **gparted**, **fdisk** or some similar tool to get your partitions set up properly first. Then you can start the installer and manually specify the mount points and swap without having to format via the ubuntu OS installer wizard.

EDIT: **fdisk** cannot format, it will only create the partitions. You will have to use mkfs,gprated or something else to format.
Let us know how it goes.

---

### Post by oldfred on 2016-07-30
Gparted is showing Red error icons on all the NTFS partitions.
That is typical if Windows is hibernated.
And if Windows 8 or later, the fast start up is always on hibernation.
       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

While in Windows make sure you create a repair/recovery drive. Windows will keep turning on fast start or need chkdsk and grub only boots working Windows. So you need an easy way to repair Windows.
       Repair/backup/restore
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
            [http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)

---

### Post by americast on 2016-07-31
> **nikefalcon said:**
> The parted output shows the partition table to be "msdos" so we already know it is MBR.



1) Since you are using MBR, the fourth partition(**sda4**) has to span the entire unused region after your windows partition(**sda3,** isn't it?). That's the only way you are going to be able to use the full capacity of the HDD as MBR only allows for up to 4 partitions(sda1 through sda4). You can make all your new logical partitions inside this extended one, that is **sda4**. These partitions shall be numbered upwards from sda5.

2) I do not know what exactly went wrong when you tried through the installer, so I'd suggest booting a live cd/usb and using **gparted**, **fdisk** or some similar tool to get your partitions set up properly first. Then you can start the installer and manually specify the mount points and swap without having to format via the ubuntu OS installer wizard.

EDIT: **fdisk** cannot format, it will only create the partitions. You will have to use mkfs,gprated or something else to format.
Let us know how it goes.

Creation of an extended partition on the free space using gparted was successful but creation of logical partitions inside the extended partition is failing. I tried creating a 2GB logical partition and what happened was this:

[https://www.dropbox.com/s/jat2030tr2jrgnj/Screenshot%20from%202016-07-31%2009-45-52.png?dl=0](https://www.dropbox.com/s/jat2030tr2jrgnj/Screenshot%20from%202016-07-31%2009-45-52.png?dl=0)

Here is the error report:

```
GParted 0.25.0 --enable-libparted-dmraid --enable-online-resize

Libparted 3.2
Create Logical Partition #1 (ext4, 2.00 GiB) on /dev/sda  00:00:03    ( ERROR )
     	
create empty partition  00:00:02    ( SUCCESS )
     	
path: /dev/sda5 (partition)
start: 83890176
end: 88084479
size: 4194304 (2.00 GiB)
clear old file system signatures in /dev/sda5  00:00:00    ( SUCCESS )
     	
write 512.00 KiB of zeros at byte offset 0  00:00:00    ( SUCCESS )
write 4.00 KiB of zeros at byte offset 67108864  00:00:00    ( SUCCESS )
write 512.00 KiB of zeros at byte offset 2146959360  00:00:00    ( SUCCESS )
write 4.00 KiB of zeros at byte offset 2147418112  00:00:00    ( SUCCESS )
write 8.00 KiB of zeros at byte offset 2147475456  00:00:00    ( SUCCESS )
flush operating system cache of /dev/sda  00:00:00    ( SUCCESS )
set partition type on /dev/sda5  00:00:01    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:00    ( ERROR )
     	
mkfs.ext4 -F -L "" /dev/sda5  00:00:00    ( ERROR )
     	
mke2fs 1.42.13 (17-May-2015)
The file /dev/sda5 does not exist and no size was specified.

========================================
```

Gramercy...

---

### Post by nikefalcon on 2016-07-31
That's weird...
Just wondering..have you tried doing it by hand?

After creating partition, run as root:
```

partprobe
mkfs -t ext4 -L whatevernameyouwant /dev/sda5

```

You might be affected by this bug:
[https://bugzilla.gnome.org/show_bug.cgi?id=762941](https://bugzilla.gnome.org/show_bug.cgi?id=762941)
[https://git.gnome.org/browse/gparted/commit/?id=fd9013d5f6971e9282f019903d6e148e367718bf](https://git.gnome.org/browse/gparted/commit/?id=fd9013d5f6971e9282f019903d6e148e367718bf)

---

### Post by oldfred on 2016-07-31
You mention an error on block size of 2048.
But drive is this:
 Sector size (logical/physical): 512B/4096B 

So something does not seem correct on drive configuration.
Post these, just to see if anything more is shown:
      
 sudo parted /dev/sda unit s print 

 First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX >parts_ parts.txt
sudo sfdisk -d /dev/sda > parts_sda.txt 


And some have fixed issues:
You can possibly repair a MBR partition with fdisk:
sudo fdisk /dev/sda
x  # enter expert mode
f  # fix  partition table
r  # return
p  # to print
v  # to verify partition 
if ok
w  #  write the changes to disk
q  # quit

---

### Post by americast on 2016-07-31
Thanx a lot for your reply...

> **oldfred said:**
> 
Post these, just to see if anything more is shown:
      
 sudo parted /dev/sda unit s print 


Well, it gives:
```
sudo parted /dev/sda unit s print
Model: ATA ST320LT020-9YG14 (scsi)
Disk /dev/sda: 625142448s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start      End         Size        Type      File system  Flags
 1      63s        2047s       1985s       primary
 2      2048s      206847s     204800s     primary   ntfs         boot
 3      206848s    83888127s   83681280s   primary   ntfs
 4      83888128s  625141759s  541253632s  extended
 5      83890176s  88084479s   4194304s    logical

```

And,
> **oldfred said:**
> 
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX >parts_ parts.txt
sudo sfdisk -d /dev/sda > parts_sda.txt 


gives:
```
label: dos
label-id: 0xbef01032
device: /dev/sda
unit: sectors

/dev/sda1 : start=          63, size=        1985, type=42
/dev/sda2 : start=        2048, size=      204800, type=42, bootable
/dev/sda3 : start=      206848, size=    83681280, type=42
/dev/sda4 : start=    83888128, size=   541253632, type=5
/dev/sda5 : start=    83890176, size=     4194304, type=83
```

Gramercy...

---

### Post by oldfred on 2016-07-31
Do not know if entire issue or not.
But you must have copied/cloned partitions to drive.
You have sda1 starting at sector 63 and that has not been used since XP and after Windows 7 changed to 2048, then Linux soon after also changed.
Did you install new drive in older system?

All 4K drives need to start at sector 2048 and have sector boundaries divisible by 8. Otherwise you will have performance issues.
       Sector size (logical/physical): 512B/[COLOR=#ff0000]4096B [/COLOR]
/dev/sda1 : [COLOR=#ff0000]start=          63[/COLOR], size=        1985, type=42 

      Partition does not start on physical sector boundary.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

But to fix this you just about have to fully backup everything & restore data.

---

### Post by americast on 2016-07-31
> **oldfred said:**
> Do not know if entire issue or not.
But you must have copied/cloned partitions to drive.
You have sda1 starting at sector 63 and that has not been used since XP and after Windows 7 changed to 2048, then Linux soon after also changed.
Did you install new drive in older system?

All 4K drives need to start at sector 2048 and have sector boundaries divisible by 8. Otherwise you will have performance issues.
       Sector size (logical/physical): 512B/[COLOR=#ff0000]4096B [/COLOR]
/dev/sda1 : [COLOR=#ff0000]start=          63[/COLOR], size=        1985, type=42 

      Partition does not start on physical sector boundary.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

But to fix this you just about have to fully backup everything & restore data.

Thanx again for your reply. I think I should have mentioned it before. I am running Windows 10 which I had upgraded from Windows 7. Windows 7 had come pre-installed with this PC.

May be I need to convert the dynamic volume into a basic volume...

Gramercy again...

---

### Post by oldfred on 2016-07-31
Fdisk used to show dynamic partitions, but I guess parted does not.
Generally Linux does not work with Windows proprietary dynamic partitions.

       [http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

You also need this off.

 Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

---


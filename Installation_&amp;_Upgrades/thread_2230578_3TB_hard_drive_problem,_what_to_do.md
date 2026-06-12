---
title: "3TB hard drive problem, what to do?"
date: 2014-06-20
forum: Installation &amp; Upgrades
---

### Post by zzaoka on 2014-06-20
I installed Xubuntu 14.04 64bit system, after installation and restart it does not boot. (it was working with old hard drive that is smaller)

This is the error:
```
[FONT=Ubuntu Mono]error: attempt to read or write outside of disk 'hd0'. [/FONT]Entering rescue mode...  [FONT=Ubuntu Mono]grub rescue>[/FONT]
```

How do I fix this?

---

### Post by oldfred on 2014-06-20
How did you partition drive?
Is system BIOS or UEFI?
Do you have BIOS set to AHCI for drive.

Post this from terminal.

sudo parted -l

---

### Post by zzaoka on 2014-06-20
[LIST]
[*]I used "erase all disk and install xubuntu" option during installation
[*]Its BIOS, not UEFI
[*]No AHCI option in BIOS
[*]Could not run that command, its GRUB command line
[/LIST]

As I said it was working fine with smaller disk, I purchased new 3TB and this must be related to bigger space for sure...

This is motherboard model (latest BIOS installed)
[http://www.asus.com/Motherboards/M2NBPVM_CSM/](http://www.asus.com/Motherboards/M2NBPVM_CSM/)

---

### Post by oldfred on 2014-06-20
What settings do you have on motherboard for drive. Use LBA or large but not IDE nor RAID.

Post this from live installer.
sudo parted -l

Since it looks like a much older drive, you probably need to use Something Else or manual install and make sure to have all of / (root) inside the first 100GB of drive. Rest of drive can be /home or data partition(s).

I normally suggest a 25GB / partition. If booting in BIOS mode on gpt partitioned drive you must also have a bios_grub partition. The installer should have created that, but if manually partitioning make sure you have it.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4(or ext3) 
[*]all but 2 GB Mountpoint /home logical beginning ext4(or ext3) 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

It looks like you have an older nVidia card. You still will need to use nomodeset to boot from grub menu.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
      
 nVidia versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers.
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

---

### Post by tgalati4 on 2014-06-20
It's possible that your BIOS does not handle the layout of this particular 3 TB drive.  The reason you could install it is because Ubuntu overrides the BIOS for disk detection, but during boot, the BIOS must recognize the disk in order to boot from it.  Boot into BIOS and look through the disk options.  Try SATA-only instead of IDE/SATA.  Remove any IDE devices in case there is a chipset limitation.

---

### Post by zzaoka on 2014-06-20
Here is the result for that command:

```
xubuntu@xubuntu:~$ sudo parted -l
Model: ATA TOSHIBA MG03ACA3 (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  2996GB  2996GB  ext4
 3      2996GB  3001GB  4158MB


Model: Verbatim STORE N GO (scsi)
Disk /dev/sdb: 8005MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  8005MB  8005MB  fat32


xubuntu@xubuntu:~$ 


```

btw I have 4GB of ram

---

### Post by oldfred on 2014-06-20
I would use gparted to shrink sda2 to 25GB or reinstall manually with Something else and use a 25GB root partition. 
That may work as some BIOS do not boot from beyond 137GB. But your BIOS is old enough it may not correctly see a 3TB drive?

---

### Post by zzaoka on 2014-06-20
BIOS can see 3tb drive correctly.

So I just have to shring sda2 to 25gb and use the rest for home?

Will Xubuntu automatically know that I made changes and created separate home partition or I have to reinstall?

---

### Post by oldfred on 2014-06-20
You can reasonably easily test that it will work by shrinking partition as there is not a lot of data yet.
But it will not create a new partition for /home. You can manually do that and edit fstab to add it, but it may be easier to just reinstall. But you have to use Something Else to be able to create more than the default / & swap.
I like to create partitions with gparted as it seems a bit easier. 
But you still have to use Something else and change button, to tell it which partition is / and its format and which is /home and its format. If swap exists it finds it automatically.

---

### Post by zzaoka on 2014-06-21
SOLVED!
This article helped me: [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

Basically if we used hard disks greated than 2TB, with old motherboards that uses BIOS and does not have AHCI mode, we must use GPT partitioning scheme and by using the following (manual) partition scheme we help old BIOS&MBR scheme to start loading our Ubuntu installation in order to avoid boot error after sucesfull installation.

**Make it in this order:**



[LIST=1]
[*]biosgrub (this partition must be first, 1MB size) 
[*]/boot (it uses ext2 filesystem, size 1gb) 
[*]swap (double size of the ram, no filesystem needed) 
[*]/ (root, should be 15gb, I made it 30gb, uses ext4 filesystem)) 
[*]/home (rest of the space, ext4 filesystem, I used btrfs filesystem to experiment) 
[/LIST]


Thanks guys for help, I spent some time to research and learned a bit...

---

### Post by sudodus on 2014-06-21
Congratulations and thanks for sharing your solution :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---


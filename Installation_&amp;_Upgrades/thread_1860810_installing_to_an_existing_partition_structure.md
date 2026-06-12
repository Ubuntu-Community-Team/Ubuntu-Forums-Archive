---
title: "installing to an existing partition structure"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by skela on 2011-10-15
I've got ubuntu 11.04 installed, with a windows dual boot.
My / is most of the disk, and I've got my home folders in a separate partition.

But when I try to install 11.10, the list of partitions is empty in the installer.
I feed uncomfortable unless I can see which partition is going to get wiped.

Basically, all I'm trying to do is to install a fresh version of Ubuntu 11.10, only on my root partition,
(so not touching my windows partition, or my home partition).

What do I need to do to get the partitions to show up in the list?

---

### Post by hal8000 on 2011-10-15
From existing Ubuntu post the output of:

sudo fdisk -l

df -hT

I just installed Ubuntu 11.10 from the installer at the disk partioner
choose "Something Else" this then allows you to use existing partitions.

For me I was using btrfs filesystems for both / and /home and the first attempt to install the installation crashed.  I then decided to make / ext4 and /home btrfs. This time installation completed.

Post output of those commands first and we'll see what you have setup.

---

### Post by skela on 2011-10-15
```

skela@davinci3:~$ sudo fdisk -l
[sudo] password for skela: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb78bf718

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/sda2            2433        4864    19535040   83  Linux
/dev/sda3            4865        5350     3903795   82  Linux swap / Solaris
/dev/sda4            5351       57614   419810580   83  Linux


skela@davinci3:~$ df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda2     ext4     19G  4.6G   13G  27% /
none      devtmpfs    2.0G  680K  2.0G   1% /dev
none         tmpfs    2.0G  596K  2.0G   1% /dev/shm
none         tmpfs    2.0G  220K  2.0G   1% /var/run
none         tmpfs    2.0G     0  2.0G   0% /var/lock
/dev/sda4     ext3    398G  298G   88G  78% /home


```


"I just installed Ubuntu 11.10 from the installer at the disk partioner
choose "Something Else" this then allows you to use existing partitions."

The weird bit is, I never see the something else button,
it basically skips that step.
It goes from the screen where you see the ticks to install proprietary software and to update packages during installation, to the partition editor screen, with the partitions blank.
I've had the same problem with beta 1, beta2, and now also the live release.

---

### Post by hal8000 on 2011-10-15
> **skela said:**
> ```

skela@davinci3:~$ sudo fdisk -l
[sudo] password for skela: 


skela@davinci3:~$ df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda2     ext4     19G  4.6G   13G  27% /
none      devtmpfs    2.0G  680K  2.0G   1% /dev
none         tmpfs    2.0G  596K  2.0G   1% /dev/shm
none         tmpfs    2.0G  220K  2.0G   1% /var/run
none         tmpfs    2.0G     0  2.0G   0% /var/lock
/dev/sda4     ext3    398G  298G   88G  78% /home


```


"I just installed Ubuntu 11.10 from the installer at the disk partioner
choose "Something Else" this then allows you to use existing partitions."

The weird bit is, I never see the something else button,
it basically skips that step.
It goes from the screen where you see the ticks to install proprietary software and to update packages during installation, to the partition editor screen, with the partitions blank.
I've had the same problem with beta 1, beta2, and now also the live release.

It is just before the partition editor screen that the screen appears (or not in your case). This could be an install bug. The first time I installed, the installer crashed, the second time I chnaged filesystems from btrfs to ext4 and install went smoothly.
Unless someone has a better idea, I would back up your data, then manually
wipe the partitions and try installing again, to see if this helps.

---

### Post by varunendra on 2011-10-17
> **skela said:**
> The weird bit is, I never see the something else button,
it basically skips that step.
It goes from the screen where you see the ticks to install proprietary software and to update packages during installation, to the partition editor screen, with the partitions blank.
I've had the same problem with beta 1, beta2, and now also the live release.
If this happens everytime with every distro, I doubt a bad partition table in the MBR. If this happened only with 11.10 releases, it maybe a bug as *hal8000 *pointed out, but I still doubt a non-standard partition table since the same releases work for others.

Whatever be the cause, I'd go with what *hal8000 *suggested (wipe the entire disk > recreate partitions using gparted, retry installation).


**PS:**
Was your hard drive ever a part of some RAID array? If it was, the command for you to remove possible remnants of the metadata:
```
sudo dmraid -E -r /dev/sda
```
Make sure no such option is enabled in the BIOS as well.
This may be a useful read for you: [http://ubuntuforums.org/showthread.php?p=9274738#post9274738](http://ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by Quackers on 2011-10-17
skela, your system is already using 4 primary partitions. On an MBR partitioned drive that is the maximum. This is the reason the installer is not giving you the install alongside option.
If you want more partitions (or to install another operating system) you will need to delete one primary partition then in its space create an extended partition. This new extended partition can hold as many new LOGICAL partitions as you want.
Most Linux systems will boot from a logical partition, but Windows won't (unless its boot files are in a separate primary partition).

---

### Post by varunendra on 2011-10-17
> **Quackers said:**
> skela, your system is already using 4 primary partitions. On an MBR partitioned drive that is the maximum. This is the reason the installer is not giving you the install alongside option.Damn it!! That's why experience counts.. I missed that simple fact. Thank you quackers, you hit the nail on the head.

---


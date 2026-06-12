---
title: "Installing Ubuntu 13.10 alongside Windows 7"
date: 2013-10-25
forum: Installation &amp; Upgrades
---

### Post by NoFriends on 2013-10-25
Alright guys,

I've now given up trying to boot via USB Stick and went out and got some dvd's, installation is running fine.

Only issue i'm facing is the choosing installation section, There's no options to install ubuntu alongside windows,
only inside windows or remove windows, there was another option that says select something else.

I click select something else and it comes up with all the partitions, as i've never done this before i have no idea,
what to do next, the last time i run an install was 9.04 and it was a case of using the slider to select how much
GB you wanted you're ubuntu partition, 13.10 doesn't have that.

If someone can advise that would be appreciated.

I have a 1TB HDD with Windows 7 (913GB) , HP Recovery Tools (15GB) , HP Tools ( 5GB) All installed when purchased the laptop.

---

### Post by sudodus on 2013-10-25
Boot into a live session from the Ubuntu Boot CD 'Try Ubuntu'!

Run gparted. If you boot from a terminal window, use the command

```
sudo gparted
```

You can also run the following commands and post the output of the following commands in a reply

```
sudo fdisk -lu
```
```
sudo parted -l
```

I think that you have a fourth (hidden) partition, that is shown by these commands (also gparted). If you have an MSDOS partition table it means that no more partition can be created.

You need to remove one partition to get 'logical space' to create an extended partition where to install Ubuntu.

Then you would probably also shrink a big partition, the one with Windows, to create unallocated space to be used by the extended partition.

Create the extended partition
Create one ext4 partition for Ubuntu's root file system (as a logical partition)
Create one swap partition (as a logical partition)

Install Ubuntu into the ext4 partition (it will find the swap partition automatically).

-o-

But if my guess about the partition table is wrong, we have to start from the beginning using the information from the output of the commands above (that you post in a reply)

---

### Post by sudodus on 2013-10-25
1. Please boot from the Ubuntu 13.10 CD and run the programs I suggested (and post the result). Ubuntu is much better to show hidden partitions if there are such partitions!

2. Please make a backup of all your personal files or the whole drive where you intend to install Ubuntu.

3. Do not edit the partitions or install anything before you have a backup on another drive, because things can go wrong and all data can be erased or at least made very hard to recover.

-o-

I don't think those few unallocated MB are the problem.

---

### Post by NoFriends on 2013-10-25
> **sudodus said:**
> In your first post you wrote


Did you wipe  HP Recovery Tools (15GB) , HP Tools ( 5GB) ? Because I don't see any such partitions.

As it is now, there is only one partition in each drive, and it should work well to install Ubuntu. Do you want a dual boot in drive /dev/sda?

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SAMSUNG HD103UJ (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs         boot

```

In that case, use ***gparted*** to shrink the partition /dev/sda1 (and create unallocated space). Remember ***backup*** before editing partitions.

Are the other drives internal or external (USB or eSATA)? Would it be an option to install Ubuntu into one of those?

Sorry another member hijacked the thread, please find my post below with my partitions and the output of running you're commands.

---

### Post by NoFriends on 2013-10-25
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1e24d905

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600  1915770879   957680640    7  HPFS/NTFS/exFAT
/dev/sda3      1915770880  1945202687    14715904    7  HPFS/NTFS/exFAT
/dev/sda4      1945202688  1953523119     4160216    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  210MB   209MB   primary  ntfs         boot
 2      210MB   981GB   981GB   primary  ntfs
 3      981GB   996GB   15.1GB  primary  ntfs
 4      996GB   1000GB  4260MB  primary  fat32        lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$

---

### Post by sudodus on 2013-10-25
Yes you have four primary partitions and need to wipe one of them. I would suggest that you copy the content of HP_TOOLS to another drive and after that remove that partition, /dev/sda4.

> **NoFriends said:**
> [IMG]http://s17.postimg.org/xkbwi21wv/Screenshot_from_2013_10_25_10_23_04.png[/IMG]

---

### Post by sudodus on 2013-10-25
> **davorin104 said:**
> i already shrinked the 1TB drive 30 gb 1 gb for swap and 29 gb ext4 for ubuntu and when ubuntu install i restart my computer trying to boot but cant i get the error: no such partition. entering rescue mode. grub rescue>_
You need to explain more about your system to make it possible to help in an efficient way:

- computer specs: brand name, model, cpu, ram (size), graphics card/chip, wifi card/chip

- operating system version and flavour of Ubuntu (for example Ubuntu 12.04 LTS 64-bits or Lubuntu 13.10 32-bits

and how you installed it.

---

### Post by NoFriends on 2013-10-25
> **sudodus said:**
> ...

Seems an aweful lot of hassle to get ubuntu onto the laptop alongside windows 7, damm you HP.

---

### Post by sudodus on 2013-10-25
Yes, we wonder why HP delivers computers with four primary partitions in an MSDOS partition table. But UEFI is much worse. Maybe that helps you feel better :-P

---

### Post by NoFriends on 2013-10-25
> **sudodus said:**
> Yes, we wonder why HP delivers computers with four primary partitions in an MSDOS partition table. But UEFI is much worse. Maybe that helps you feel better :-P

Makes me feel a little bit better, just a shame though i really wanted to have it running alongside.

---

### Post by sudodus on 2013-10-25
And it is possible. There are several threads here at the Ubuntu Forums where people have move the HP_TOOLS directories and files and removed that partition to make logical space for an extended partition and Ubuntu (or Lubuntu, Xubuntu, Kubuntu depending on hardware and preferences).

---

### Post by oldfred on 2013-10-25
Almost all Windows 7 systems are configured to use all 4 primary partitions. And often the vendor partition does not have a lot of useful info that could not just be in the Windows main partition.

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---


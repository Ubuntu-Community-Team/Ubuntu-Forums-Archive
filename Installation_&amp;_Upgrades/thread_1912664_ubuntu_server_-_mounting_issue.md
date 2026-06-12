---
title: "ubuntu server - mounting issue"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by wotan0 on 2012-01-21
Hi,

i just finished installing ubuntu server on my new nas system.
i've installed the Ubuntu on a new hdd. additionally i put 2 other hdds into the nas, which came from an earlier nas system with just data on them. they're formatted in ext3, but my "fdisk -util" says they are "Id: fd ; System: Linux raid autodetect".

Now what i easily want is to access my data in the ubuntu system, so i want to mount it in /media ...
I edited the etc/fstab as this:

/dev/sdb3 /media ext3 defaults 1 2
/dev/sdc3 /media ext3 defaults 1 2

if i type "mount /dev/sdb3" i get : " /dev/xy is already mounted or /media is currently in use"

I hope i told you enough details and its quite easy to solve (I'm beginner).

- Ubuntu Server 11.10 amd64 

regards

edit:
if i want to umount one of these devices, i get the expected feedback...: "/dev/xy is not mounted"

---

### Post by darkod on 2012-01-21
You left out the most important part:
Were the disks used as raid in the old system, and do you expect to mount them as raid again?
The fd Linux Raid Autodetect type is configured on disks used in linux software raid. I'm not sure if the same type is used for fakeraid, I think not.

During the install didn't it detected you had raid disks, or you connected them later?

---

### Post by wotan0 on 2012-01-21
Thats the most confusing point, it was'nt a RAID system. The previous NAS was a synology ds210j and I chose a "basic" formatting (a non-raid solution).

They were former mounted as volume1/ and volume2/ .
So they have been accepted couriosly as RAID1?

[IMG]http://dl.dropbox.com/u/6478002/Photo/Screenshots/Bildschirmfoto%202012-01-21%20um%2010.15.04.png[/IMG]

Maybe there is a possibility of not-loosing all my data and recovering the corrupt device information?

The devices were connected all the time during the installation and were not touched in partitioning-process.


> 
> sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
***************************************************************

Disk /dev/sdb: 2930277168 sectors, 1.4 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 0BF1D9AE-ED01-4739-B6B3-46702384C07F
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 2930277134
Partitions will be aligned on 256-sector boundaries
Total free space is 267436 sectors (130.6 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1             256         4980735   2.4 GiB     FD00  Linux RAID
   2         4980736         9175039   2.0 GiB     FD00  Linux RAID
   3         9437184      2930272064   1.4 TiB     FD00  Linux RAID



---

### Post by darkod on 2012-01-21
I don't know about the synology, but it can be raid even if you are not aware of it. When I bought my WD My Book World Edition 1TB, even though it comes with a single 1TB disk, I was very surprised to see that it is configured as a raid1 array which always works in degraded state with one disk, and one missing (because it was never there).

It seems your setup is similar, because for every /dev/mdX device only one member partition is stated.

/dev/mdX is a software raid device. To assemble an existing device(s) you can use:
sudo mdadm --assemble --scan

The --scan option detects them automatically for you.

When using mdadm and existing raid devices be careful with the following:
--create is used only when creating it the first time. if you use --create on exisiting one after you moved it to another computer, it will destroy the old array (data) and create new
--assemble is used to assemble existing raid array that was alreay created earlier, doesn't matter if it was on another computer

At least that's how I understand it.

If the assemble scan above works, you will need to mount them. For more permanent mounts, you could do something like:
```
sudo --assemble --scan
(this should assemble your /dev/md2 and /dev/md3 devices)
sudo mkdir /media/md2
sudo mkdir /media/md3
sudo mount /dev/md2 /media/md2
sudo mount /dev/md3 /media/md3
```

Then see if you can list the data in /media/md2 and /media/md3. If it works fine you can make manual entries in /etc/fstab to mount them on boot.

EDIT: It seems there will also be a /dev/md1 device because from the gdisk output you posted there are three FD partitions. Lets see what the assemble scan finds and configures.

---


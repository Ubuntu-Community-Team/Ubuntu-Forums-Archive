---
title: "HD clone with ddrescue"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by drumanart on 2012-07-05
Hell everybody.
I bought a 500Gb USB hard-drive to make a clone of my laptops HD.
For some reason after cloning the system I'm not able to boot from the drive:

I tried two different ways:
First: **sudo dd if=/dev/sda1 of=/dev/sdb**
where sdb is the new drive.

Second: **cfdisk -z /dev/sdb**
**sudo ddrescue -v /dev/sda /dev/sdb**

If I open the drive with the "disk utility" everything looks Ok, but when booting up with USB priority after a while the boot-prozess jumps to the internal drive.
I'd like to use the USB HD to boot another computer.

Thanks Martin

---

### Post by msammels on 2012-07-05
What errors do you get?

---

### Post by drumanart on 2012-07-05
The lshw command list the following:

drumanart@drumanart:~$ sudo lshw -C disk
[sudo] password for drumanart: 
  *-disk                  
       description: ATA Disk
       product: Hitachi HTS54502
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: PB2O
       serial: 100403PBG2063SHPKZUV
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000e6f67
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdb
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: signature=000e6f67

---

### Post by Grenage on 2012-07-05
> **drumanart said:**
> I tried two different ways:
First: **sudo dd if=/dev/sda1 of=/dev/sdb**
where sdb is the new drive.

Ignoring ddrescue for now, that command copies a partition, not the drive.  Try:

```
sudo dd if=/dev/sda of=/dev/sdb bs=4096 conv=noerror,notrunc
```

---

### Post by drumanart on 2012-07-05
This will take some time, I'll let you kow.
Thanks for the help
Martin

---

### Post by drumanart on 2012-07-05
After view hours the dd command has finished copying. Now, if I try to boot from the new HD the computer starts resetting over and over again.
If I boot from the internal HD and try to mount the USB drive with the disk utility I get this error:

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed

drumanart@drumanart:~$ sudo lshw -C disk
[sudo] password for drumanart: 
  *-disk                  
       description: ATA Disk
       product: Hitachi HTS54502
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: PB2O
       serial: 100403PBG2063SHPKZUV
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000e6f67
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: signature=000e6f67

---

### Post by Grenage on 2012-07-06
Greetings,

A couple of questions:

1) I've never used dd to clone a drive that was mounted and in use, are you booting from a LiveCD before cloning the laptop drive?  Others may have further input here.

3) I assume that your laptop has been able to boot from other USB media?

4) You get a mount error message referring to sda, which I assume is your internal drive:

```
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed
```

a) I'd expect the USB drive to appear in Nautilus, and auto-mount or be selectable from there.
b) Are you definitely mounting the right drive?

---

### Post by drumanart on 2012-07-07
No, I did the dd command directly from the mounted internal HD:

**sudo dd if=/dev/sda of=/dev/sdb bs=4096 conv=noerror,notrunc**

Then the command: **sudo fdisk -l** shows the cloned drive (it seems to be correct)


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e6f67

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   480536575   240267264   83  Linux
/dev/sda2       480538622   488396799     3929089    5  Extended
/dev/sda5       480538624   488396799     3929088   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e6f67

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   480536575   240267264   83  Linux
/dev/sdb2       480538622   488396799     3929089    5  Extended
/dev/sdb5       480538624   488396799     3929088   82  Linux swap / Solaris

Is your succession to start the dd commend from a live USB stick? (I don't have a CD drive on my Lap Top).
Kind regards Martin

---

### Post by mywai on 2012-07-07
I have booted either from Live CD or USB flash drive and followed procedure in

[www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk](www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk)

to image hard drives.

With flash drive, ddrescue will stay with it.

John

---

### Post by drumanart on 2012-07-07
Ok, I'll give it a try, thanks

---

### Post by drumanart on 2012-07-11
I made an boot able USB memory stick with **UBUNTU Rescue Remix** and I  initiated the command to clone my external drive.
**sudo ddrescue -v /dev/sda /dev/sdb &#8211;force** (--force I did because the drive was not empty)

The program finished without any error and **fdisk -l** shows a perfect cloned system (see underneath).
Still I cant boot from the drive. My intention is to use the cloned drive to boot up another computer.
Is this possible, let's say like with Puredyne? Or may I'm totally wrong and this never works.
ddrescue offers a lot of switches, is there an option for my use?

**sudo fdisk -l**

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e6f67

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   480536575   240267264   83  Linux
/dev/sda2       480538622   488396799     3929089    5  Extended
/dev/sda5       480538624   488396799     3929088   82  Linux swap / Solaris

Disk /dev/sdb: 16.0 GB, 15998099456 bytes
64 heads, 32 sectors/track, 15256 cylinders, total 31246288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00060b78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    31244287    15622128    c  W95 FAT32 (LBA)

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e6f67

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   480536575   240267264   83  Linux
/dev/sdc2       480538622   488396799     3929089    5  Extended
/dev/sdc5       480538624   488396799     3929088   82  Linux swap / Solaris

---

### Post by oldfred on 2012-07-11
If you totally cloned drive you have duplicate UUIDs.

sudo blkid -c /dev/null -o list

System will not work with duplicate UUIDs. If just using for backup or on another computer it should be ok, but will not work on the one you copied from because of the duplicates. 

You could change UUID, edit fstab & reinstall grub, then then it is not a image.

---

### Post by drumanart on 2012-07-11
I made an boot able USB memory stick with UBUNTU Rescue Remix and I  initiated the command to clone my external drive.
sudo ddrescue -v /dev/sda /dev/sdb –force (--force I did because the drive was not empty)

The program finished without any error and fdisk -l shows a perfect cloned system (see underneath).
Still I cant boot from the drive. My intention is to use the cloned drive to boot up another computer.
Is this possible, let's say like with Puredyne? Or may I'm totally wrong and this never works.
Ddrescue offers a lot of switches, is there an option for my use?

sudo fdisk -l 

Disk /dev/sda: 250.1 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x000e6f67 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *        2048   480536575   240267264   83  Linux 
/dev/sda2       480538622   488396799     3929089    5  Extended 
/dev/sda5       480538624   488396799     3929088   82  Linux swap / Solaris 

Disk /dev/sdb: 16.0 GB, 15998099456 bytes 
64 heads, 32 sectors/track, 15256 cylinders, total 31246288 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x00060b78 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *          32    31244287    15622128    c  W95 FAT32 (LBA) 

Disk /dev/sdc: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x000e6f67 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1   *        2048   480536575   240267264   83  Linux 
/dev/sdc2       480538622   488396799     3929089    5  Extended 
/dev/sdc5       480538624   488396799     3929088   82  Linux swap / Solaris

---

### Post by drumanart on 2012-07-11
Sorry I duplicated the last text:

So I changed the UUID on my external drive with:
**sudo tune2fs -U random /dev/sdb1**
Still I can't boot from it. My intention is to use the drive to boot an other computer. 
At least since I made the changes the external drive mounts automatically.
Is this a GRUB problem? 

The **sudo blkid -c /dev/null -o list** gives:

device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              0e1c0f26-b026-40d5-911a-b21e173e0455
/dev/sda5  swap             <swap>         94f51246-196f-4c4a-87e8-ff635eb06f91
/dev/sdb1  ext4             /media/7bb9f1ad-25ee-4a3b-b8ef-4b5f61568fa8 7bb9f1ad-25ee-4a3b-b8ef-4b5f61568fa8
/dev/sdb5  swap             (not mounted)  94f51246-196f-4c4a-87e8-ff635eb06f91


Thanks Martin

---

### Post by oldfred on 2012-07-11
Swaps are still the same UUID.

When you change UUID you have to update fstab with new UUIDs and reinstall grub2's boot loader.

Then you'll have to edit fstab:

This is for your working fstab, you will have to adjust for mount of the non-working version:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

Something like this?:
sudo mkdir /mnt/sdc1
sudo mount /dev/sda1 /mnt/sdc1
gksu gedit /mnt/sdc1/etc/fstab


You can use this to reinstall grub2's boot loader:

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

Or:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
(was this thread) [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by drumanart on 2012-07-12
I made a boot USB stick with **Ubuntu-Secure-Remix** because I thought that **Boot-Repair** is already installed on the new version. But I can't start the program.

So I tried to change the UUID from the booted USB doing the following:
**sudo mkdir /media/sdc1**
** sudo mount /dev/sdc1 /media/sdc1**
**sudo tune2fs -U random /dev/sdc1**

then I re-installed the grub with:

**sudo grub-install --root-directory=/media/sdc1 /dev/sdc**

Now the command: 
**sudo blkid -c /dev/null -o list**
outputs:
/dev/sda1  ext4             /              0e1c0f26-b026-40d5-911a-b21e173e0455
/dev/sda5  swap             <swap>         94f51246-196f-4c4a-87e8-ff635eb06f91
/dev/sdb1  ext4             /media/ea376fcb-cd44-449b-819d-1a1f176926d5 ea376fcb-cd44-449b-819d-1a1f176926d5
/dev/sdb5  swap             (not mounted)  94f51246-196f-4c4a-87e8-ff635eb06f91

The UUID is the same on both drives.

If run **Boot-Repair** on my mounted filesystem:
[http://paste.ubuntu.com/1088532](http://paste.ubuntu.com/1088532)

Thanks Martin

---

### Post by oldfred on 2012-07-12
Your fstabs are also calling out the same UUIDs. So if you boot sdb it will mount the partitions on sda.

---


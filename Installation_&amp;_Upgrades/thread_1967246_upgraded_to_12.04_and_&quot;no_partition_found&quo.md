---
title: "upgraded to 12.04 and &quot;no partition found&quot;"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by Dasien on 2012-04-27
I am a basic user but have been using Ubuntu for around 5 years. I just upgraded my asus eepc 1005ha net book and when the boot screen comes up it looks like a old one (black and white) then any boot option I try including my windows partition I get a error of "no partition found". I can open grub but I am unfamiliar with what to even look for. 
Thank you 
Nick

---

### Post by garvinrick4 on 2012-04-27
Using a Live CD (Ubuntu CD using Try Ubuntu) open a terminal and:
```
sudo fdisk -l 
```(lower case L)
```
sudo parted -l
``` (lowr case L)
What is output?

---

### Post by Dasien on 2012-04-27
I am all over this but I will need to get a live cd and put it on a usb because my current live usb seems to be corrupted so I wil give some read outs tomorrow thanks for the help and getting me started.

---

### Post by Dasien on 2012-04-28
Here is the read outs... I can totaly reload ubuntu but I do have some files of my wifes I would love to get off of the windows partition if at all possible.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8da2c67c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   209717247   104857600    7  HPFS/NTFS/exFAT
/dev/sda2       209717248   468828576   129555664+  83  Linux
/dev/sda3       468830206   488359935     9764865    5  Extended
/dev/sda5       468830208   488359935     9764864   82  Linux swap / Solaris

Disk /dev/sdb: 2004 MB, 2004877312 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00072841

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     3913191     1956565    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST9250315AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  107GB  107GB   primary   ntfs            boot
 2      107GB   240GB  133GB   primary   ext4
 3      240GB   250GB  9999MB  extended
 5      240GB   250GB  9999MB  logical   linux-swap(v1)


Model:  USB DISK 2.0 (scsi)
Disk /dev/sdb: 2005MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  2004MB  2004MB  primary  fat32        boot, lba


ubuntu@ubuntu:~$ 
```
 
Thanks

---

### Post by darkod on 2012-04-28
The partitions are there but we need more details. Run the boot info script from the link in my signature and post the results as explained there. It can be done from live mode. That will show us more details.

---

### Post by oldfred on 2012-04-28
If you have important files that you have not backed up, I would do that right away if you can. You should be able to mount the NTFS partition with the liveCD or USB and copy the files.

But if the NTFS partition need chkdsk which can only be run from Windows, Ubuntu will not mount it to prevent further damage that then chkdsk may not be able to fix.

Your partition table looks ok to me, but others may see something.

I would download and run this, post the link to the Bootinfo it creates so we can suggest what repairs may be best:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

---

### Post by Dasien on 2012-04-28
I ran boot repair and here is the url
[HTML]http://paste.ubuntu.com/953565/[/HTML]
I have backed up what I needed so I am prepared for the worse case senario
Thank you everyone for the help

---

### Post by darkod on 2012-04-28
I can't see anything wrong. But since you already had ubuntu, maybe the grub2 on the MBR is not correct although it seems like it is. Just in case, boot with a 12.04 cd (it's always best to repair grub with the same version cd) into live mode and try in terminal:
```
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Restart and see if that helps.

I see that in windows you still have some remains of a wubi install, so if you try to boot windows you might see one more boot menu, but that can be easily sorted out later. Right now it's more important that it starts booting.

---

### Post by Dasien on 2012-04-28
This seemed to work both partitions are back up and going and it seems as if every thing is they way it should be. 
Thank you and I will mark it as SOLVED

---

### Post by zender on 2012-05-02
I had the same "no partition found" error.
Followed the last two steps above, i.e., re-installed grub on disk 2,
and everything worked fine.
Thanks for blazing the trail ahead of me!
cz

---


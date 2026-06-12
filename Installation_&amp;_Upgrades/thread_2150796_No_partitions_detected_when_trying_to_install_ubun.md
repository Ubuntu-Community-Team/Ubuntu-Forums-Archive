---
title: "No partitions detected when trying to install ubuntu 13.04"
date: 2013-06-02
forum: Installation &amp; Upgrades
---

### Post by ahmed11ber on 2013-06-02
Hello,

I've recently bought a laptop Hp pavilion g6 with windows 7 64bits pre-installed, when I was trying to install ubuntu 13.04, no partions has been detecetd by the wizard ( In fact, I have four partitions: boot partition, windows partition 20GB occupied over 195 GB, e: partition  empty, e: partition empty) so I've enogh space to install Ubuntu. I don't know where is the problem and why I can't install ubuntu alongside with windows 7. In addition when I execute the Gparted program it gave this message:

/dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? 

I will be most grateful to whom gives me an assistance to solve this problem, so I can install Ubuntu.

Thanks a lot.

---

### Post by fantab on 2013-06-02
Can you boot with the Ubuntu LiveDVD/USB ie, 'Try Ubuntu without Installing'?
If yes then boot with it, let the desktop load, then open TERMINAL [Ctrl+Alt+T] and run the following:

```
sudo parted -l
```

and post its output here.

---

### Post by ahmed11ber on 2013-06-02
when I run sudo parted -l   
the message was the folowing:

ubuntu@ubuntu:~$ sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?

---

### Post by fantab on 2013-06-02
Can you post the screen-shot of your partitions from Windows disk Mangement? We need to have a look at those partitions. 
Did you try to create any new partitions before you tried to install Ubuntu?

---

### Post by ahmed11ber on 2013-06-02
Normaly my disc has a capacity of 500GB, but when I go to disk manager, I see that the total size is almost 465 GB. I think that I've done something with liveunbutuDVD, sure I've changed  the partition table but I don't remerber. I attach a snapshot of my disc storage. thanks a lot for your collaboration.

---

### Post by fantab on 2013-06-02
> **ahmed11ber said:**
> Normaly my disc has a capacity of 500GB, but when I go to disk manager, I see that the total size is almost 465 GB. I think that I've done something with liveunbutuDVD, sure I've changed  the partition table but I don't remerber. I attach a snapshot of my disc storage. thanks a lot for your collaboration.

Yes 500**GB**=465.66128730773926**GIB**, this is normal. The disk is showing in GiB not GB.

We have to fix this corrupt partition table. We can fix this with '[**FIXPARTS**]("http://www.rodsbooks.com/fixparts/")'... 
After using fixparts boot Ubuntu install DVD/USB and check with Gparted if it shows all your partitions.
If it does than goahead and install ubuntu.

---

### Post by ahmed11ber on 2013-06-02
I don't know how to use Fixpart? Sould I downloaded it from ubuntu liveDVD or from windows?
In addition and since I've booted from ubuntu liveDVD, I ran the command: sudo fdisk -l to check the partitions and it gives this message

ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd5f2444c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      131071       64512    7  HPFS/NTFS/exFAT
/dev/sda2          131072   294088703   146978816    7  HPFS/NTFS/exFAT
/dev/sda3       294088704   703698943   204805120    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$

---

### Post by ahmed11ber on 2013-06-02
I have downloaded fixparts from unbutu liveDVD and install it, then i have run the command the terminal : sudo fixparted /dev/sda
then i removed the gpt table, then i run another time the command: sudo parted -l
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA HGST HTS545050A7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  67,1MB  66,1MB  primary  ntfs         boot
 2      67,1MB  151GB   151GB   primary  ntfs
 3      151GB   360GB   210GB   primary  ntfs


Model: Generic Flash Disk (scsi)
Disk /dev/sdb: 4090MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      393kB  4090MB  4090MB  primary  fat32


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!       

I think the problem is resolved, I'll try to install unbutu in laptop
I have one question, which version of unbutu should I install 13.04 32bits or 64 bits, my laptop is 64 architecture HP pavillion g6 ek2220
I will attach  pictures of my  first steps of installation

How much memory do I fix to unbutu ?  for the system , for home directory and for the swap( I will choise to do manually  the partition of ubuntu)
Thank you a lot for your assistance

---

### Post by fantab on 2013-06-02
If you have 64bit machine then 64bit Ubuntu it is. 
You can use Gparted from Ubuntu DVD/USB Install Disc and create:

'Unallocated Space' EXTENDED PARTITION
30GB LOGICAL Ext4 /
4GB SWAP
'all the remaining GB LOGICAL Ext4 /home

Then from Desktop 'Install Ubuntu'.
Choose 'SOMETHING ELSE' to manually select your partitions.
30GB partition: MOUNTPOINT=/
'all the remaining GB': MOUNTPOINT=/home

Thats it.

---

### Post by ahmed11ber on 2013-06-03
When I have tried Ubuntu 13.04 32 bits version, it has detected my wireless connection, but when  I've tried the 13.04 amd 64 bits it has not detected my wireless connection. Should I install the 64 bits version even, it has not detected my wireless card ?

---


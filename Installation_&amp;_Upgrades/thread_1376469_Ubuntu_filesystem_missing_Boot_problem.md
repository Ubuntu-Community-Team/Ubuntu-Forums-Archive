---
title: "Ubuntu filesystem missing? Boot problem"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by SolomonWilde on 2010-01-09
Help! My Ubuntu 9.10 installation suddenly doesn't boot today. Possibly I closed the lid a bit soon yesterday when I shut down but this doesn't seem a likely cause. I have a dual boot with XP and had loaded a pae kernel so my grub menu has a good few listed.

All has been fine for a couple of months - suddenly today choosing the usual top item in Grub boot list the Ubuntu logo appears (white) but just stays for a while and then disappears. There is no hard disk activity. Worst of all there is no error message!

Running the install disk the partitioner is calling my second (main ubuntu) partition sda5 which doesn't seem right (XP is on sda1).

Using the Recovery Grub menu option I get: "Gave up waiting for root device". Unfortunately I don't know enough commands to do anything useful from the command prompt but I can see that my normal file system is not available. 

This is not hard disk failure as XP still boots fine.

Any help greatly appreciated.

---

### Post by SolomonWilde on 2010-01-09
OK, well I thought the best thing to do before anything else since I have much data to lose would be to back up with Ghost. But Ghost tells me there is something wrong with a Linux partition and recommends running fsck. 

I booted from the Ubuntu install disk and ran **fsck /dev/sda2** and got the message: Attempt to read block from filesystem resulted in short read. Looking around the net this seems indicative of hardware failure - yet XP still boots fine.

---

### Post by SolomonWilde on 2010-01-09
I ran the following commands from booted Ubuntu install cd terminal and got these responses:

**sudo fdisk -l**

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcd111e92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6665    53536581    7  HPFS/NTFS
/dev/sda2            6666       38913   259032060    5  Extended
/dev/sda5            6666       37844   250445286   83  Linux
/dev/sda6           37845       38913     8586711   82  Linux swap / Solaris

**sudo mke2fs -n /dev/sda2**
mke2fs 1.41.9 (22-Aug-2009)
mke2fs: inode_size (128) * inodes_count (0) too big for a
	filesystem with 0 blocks, specify higher inode_ratio (-i)
	or lower inode count (-N).

**sudo mount -t ext2 /dev/sda2 /mnt/sda2**

mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

**sudo mount -t ext2 /dev/sda5 /mnt/sda5**
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Can anybody help please? At this point I'd settle for saving my data - faith in Linux heavily shaken.

---

### Post by monsoon on 2010-01-09
Try following the instructions here:

[http://ubuntuforums.org/showthread.php?t=1355385](http://ubuntuforums.org/showthread.php?t=1355385)

I had the same problem, and this worked for me.

---

### Post by SolomonWilde on 2010-01-09
Thank you for the response Monsoon but I am sure it is not the UUID issue. Following those instructions I still get the "gave up waiting for filesystem" message. The problem is more to do with the two entries with the same address in my partition table and the partition that's zero blocks. Fsck doesn't seem able to fix this and so, because I need this sooner rather than later I'll be reinstalling and mourning the lost data. In particular it took me a while to get to be able to play DVDs - now I have to climb that mountain again.

After this I shall have to take M$ more seriously - Windows 7 here I come.

---

### Post by SolomonWilde on 2010-01-09
Apologies Monsoon that DID work. I kept trying with sda2 but when I tried sda5 suddenly everything is ok again - thank you.

I very much regret my sulky comments now, but you know what it's like :)

---

### Post by phillw on 2010-01-09
Hi, glad you got up and running. just a bit of background info on your system, should you have future problems
> Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6665    53536581    7  HPFS/NTFS
/dev/sda2            6666       38913   259032060    5  Extended
/dev/sda5            6666       37844   250445286   83  Linux
/dev/sda6           37845       38913     8586711   82  Linux swap / Solaris
sda1 = Your Win installation
sda2 = Extended Partition Marker (You can only have 4 primary partitions, this is a way round it, but costs you a primary partition)
sda5 = Your Ubuntu installation (You'll note that it is #5, as it 'lives' on the extended partition of sda2)
sda6 = Your Swap area (it is #6, for the same reason as sda5)

Rule #1: **never** and I mean **never** run fsck on a mounted partition - The safest way is to do it from a LiveCD - Trust me on that one (I've got the scars to prove it !!)

Unless you *really* know what you're doing with fsck (And I happily confess that I just trust it !!)
```
 sudo fsck -My /dev/.... 
```

The -**M** tells fsck not to touch a mounted file system.  Read Rule #1 !!
the **y** tells fsck that you mean **yes** to every time it asks if you want it to fix it - saves a lot of pressing the return button ;-)

Hard to remember ? not really .... repair **My** File System, is how I remember it !!

Regards,

Phill.

---

### Post by SolomonWilde on 2010-01-12
Thanks phillw - I realized about the extended partition in the end. There was nothing so odd about the output from fdisk at all - the message from fsck about sda2 was scary though.

---


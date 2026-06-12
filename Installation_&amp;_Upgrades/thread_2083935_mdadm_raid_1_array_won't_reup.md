---
title: "mdadm raid 1 array won't reup"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by kruppe on 2012-11-14
I have two drives configured as Raid 1 on mdadm.

Last week the power borked, the drives won't remount. Said that the array was degraded, and took about 2-3 days to resync.

The problem is now that on trying to mount the array:
```
mount: you must specify the filesystem type
```It says I have to specify a filesystem type.

dmesg | tail says:
```
[ 1050.818782] EXT3-fs (md127): error: can't find ext3 filesystem on dev md127.
[ 1050.849214] EXT4-fs (md127): VFS: Can't find ext4 filesystem
[ 1050.944781] FAT-fs (md127): invalid media value (0x00)
[ 1050.944782] FAT-fs (md127): Can't find a valid FAT filesystem
[ 1058.272787] EXT2-fs (md127): error: can't find an ext2 filesystem on dev md127.

```Attached see the drive setup.

Any help appreciated, as quite a bit of my data is on here, and I haven't gone through a resyncing process before.

---

### Post by darkod on 2012-11-14
What does
cat /proc/mdstat

say?

Did you try running fsck on the mdX device while it is unmounted? Something like:
sudo fsck /dev/mdX

depending which one is your mdX device. Don't forget it needs to be unmounted, so if it's mounted then unmount it.

---

### Post by kruppe on 2012-11-14
/proc/mdstat says:
```
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md127 : active (auto-read-only) raid1 sdj[2] sdi[0]
      2930135360 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

```
and 

```
sudo fsck /dev/md127
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/md127

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```


> **darkod said:**
> What does
cat /proc/mdstat

say?

Did you try running fsck on the mdX device while it is unmounted? Something like:
sudo fsck /dev/mdX

depending which one is your mdX device. Don't forget it needs to be unmounted, so if it's mounted then unmount it.
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md127 : active (auto-read-only) raid1 sdj[2] sdi[0]
      2930135360 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

---

### Post by darkod on 2012-11-14
Did you have ext2/ext3/ext4 filesystem on the md127 device or another filesystem?

Can you also post the output of:
cat /etc/fstab

If it was extX filesystem it looks corrupted and fsck didn't manage to sort it out in the first try. I'm not sure how safe it is to run the commend suggested, e2fsck -b 8193, especially since you have no backup of the data.

Lets see the fstab content first with the command above, and if you remember confirm the filesystem you had on md127.

---

### Post by kruppe on 2012-11-14
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=151dac44-62f4-40e8-8893-4f6b26389484 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=dcfdc4d1-93cd-424d-b8d0-8a5b8006cd0a /home           ext4    defaults        0       2
# /media/winC was on /dev/sdc2 during installation
UUID=3AB04D11B04CD553 /media/winC     ntfs    defaults,umask=007,gid=46 0       0
# /media/winD was on /dev/sdf1 during installation
UUID=30467A7C467A4320 /media/winD     ntfs    defaults,umask=007,gid=46 0       0
# /opt was on /dev/sda2 during installation
UUID=58c8c2be-b57d-47c8-9b3c-8a1b71a665d3 /opt            ext4    defaults        0       2
# /var was on /dev/sda3 during installation
UUID=4545e926-a5a8-4e0a-aa41-ed620ea9b3b6 /var            ext4    defaults        0       2
# swap was on /dev/sda1 during installation
#UUID=e3d998d8-cbd9-456e-988f-e7485581678f none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
UUID=3AB04D11B04CD553   /boot   ext4    defaults        0       2
**/dev/md0        /media/terrapool ext4 defaults  0       0**

Seems to have been ext4.

Any ideas?

---

### Post by kruppe on 2012-11-14
Darko, thanks for all the replies, you see, my logic was that raid 1 is my mirrored backup. I had no idea the full array could fail :(

---

### Post by darkod on 2012-11-14
That it seems it was ext4 is OK, but you can also see that it was md0. After the failure it has been "renamed" to md127 and together with the fsck giving an error, I don't like that.

Let me try contact someone who is bigger expert on saving raids with valuable data, but depending on time zone you might need to be patient. I understand you want to see it running ASAP but doing things in a hurry can rarely help.

Meanwhile, you can also check if the array is named md0 or md127 by posting the content of:
cat /etc/mdadm/mdadm.conf

---

### Post by darkod on 2012-11-14
> **kruppe said:**
> Darko, thanks for all the replies, you see, my logic was that raid 1 is my mirrored backup. I had no idea the full array could fail :(

I think it's only a slight mix up due to the power failure. Usually fiaxable. Lets see if someone better with the commands can help.

---

### Post by kruppe on 2012-11-14
Darko, I'm not in that much of a hurry.

Linux seems to have renamed the raid collection automatically.

What keeps me 'less scared' is the fact that it took days to resync. Which means the data is probably still there. How would it know what to resync if it couldn't find a file system, otherwise?

Any help much appreciated.

---

### Post by rubylaser on 2012-11-14
Hello, sorry you're in such a bad spot.  Let's try to do this the easy way first and just verify if any of the data on either disk is good.  Since this is a a RAID1 array, each disk should be readable by itself (without needing to assemble with mdadm). 

I would startup your computer with the Live Ubuntu CD, and try to mount each disk without trying to assemble the array.  Hopefully, one of the two disks will be mountable, and have valid data on it.  Can you try to mount each disk and report back?

```
mkdir -p /media/sd[ij]
mount /dev/sdi /media/sdi
mount /dev/sdj /media/sdj
```

Also, just for my own info, what does each disk show in it's metadata?
```
mdadm -E /dev/sd[ij]
```

---

### Post by kruppe on 2012-11-20
Thanks for getting back to me.

I have booted from a live disc (took me a while to download one with my SA bandwidth).

Here are the results. Neither of the drives want to mount. Both say 
unknown filesystem type 'linux_raid_member'

But here are the full results:
```
boot@boot ~ $ sudo mkdir /media/sdj /media/sdi
boot@boot ~ $ sudo mount /dev/sdj /media/sdj
mount: unknown filesystem type 'linux_raid_member'
boot@boot ~ $ sudo mount /dev/sdi /media/sdi
mount: unknown filesystem type 'linux_raid_member'

boot@boot ~ $ sudo mdadm -E /dev/sdi
/dev/sdi:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 37ac1824:eb8a21f6:bd5afd6d:96da6394
           Name : sojourn:33
  Creation Time : Sat Nov 10 10:43:52 2012
     Raid Level : raid1
   Raid Devices : 2

Avail Dev Size : 5860271016 (2794.40 GiB 3000.46 GB)
     Array Size : 2930135360 (2794.39 GiB 3000.46 GB)
  Used Dev Size : 5860270720 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 3e6e9a4f:6c07ab3d:22d47fce:13cecfd0

    Update Time : Tue Nov 13 20:34:18 2012
       Checksum : f7d10db9 - correct
         Events : 27

   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing)
boot@boot ~ $ sudo mdadm -E /dev/sdj
/dev/sdj:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 37ac1824:eb8a21f6:bd5afd6d:96da6394
           Name : sojourn:33
  Creation Time : Sat Nov 10 10:43:52 2012
     Raid Level : raid1
   Raid Devices : 2

Avail Dev Size : 5860271016 (2794.40 GiB 3000.46 GB)
     Array Size : 2930135360 (2794.39 GiB 3000.46 GB)
  Used Dev Size : 5860270720 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 7fb84af4:e9295f7b:ede61f27:bec0cb57

    Update Time : Tue Nov 13 20:34:18 2012
       Checksum : b9d17fef - correct
         Events : 27

   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing)

boot@boot ~ dmesg | tail
[   61.785866] init: alsa-restore main process (2736) terminated with status 99
[   68.433548] eth0: no IPv6 routers present
[  534.142511] EXT4-fs (sdi): ext4_check_descriptors: Block bitmap for group 0 not in group (block 2838187772)!
[  534.142518] EXT4-fs (sdi): group descriptors corrupted!
[  546.418780] EXT2-fs (sdi): error: couldn't mount because of unsupported optional features (240)
[  549.654127] EXT3-fs (sdi): error: couldn't mount because of unsupported optional features (240)
```

I hope this helps you somehow. Would also help if you can describe what you think went wrong. AS I see it, if either drive went offline, and a resynced happen, both should still be in a usable state.

---

### Post by kruppe on 2012-11-24
Ok, so this morning e2fsck would finally run on the one drive. It took forever to complete and ended with these messages:

```
llegal double indirect block (2298566437) in inode 39717736.  CLEARED.
Illegal block #4231180 (2611866932) in inode 39717736.  CLEARED.
Error storing directory block information (inode=39717736, block=0, num=1092368): Memory allocation failed
Recreate journal? yes

Creating journal (32768 blocks):  Done.

*** journal has been re-created - filesystem is now ext3 again ***

```
I then tried mounting it and got this. Suggestions?

```

dmesg | tail
[  170.674659] md: export_rdev(sdc)
[  170.675152] md: export_rdev(sdc)
[  195.275288] md: export_rdev(sdc)
[  195.275876] md: export_rdev(sdc)
[ 1338.540092] CE: hpet increased min_delta_ns to 30169 nsec
[26125.734105] EXT4-fs (sdc): ext4_check_descriptors: Checksum for group 0 failed (43502!=37987)
[26125.734115] EXT4-fs (sdc): group descriptors corrupted!
[26182.325371] EXT3-fs (sdc): error: couldn't mount because of unsupported optional features (240)
[27083.316519] EXT4-fs (sdc): ext4_check_descriptors: Checksum for group 0 failed (43502!=37987)
[27083.316530] EXT4-fs (sdc): group descriptors corrupted!

```

---


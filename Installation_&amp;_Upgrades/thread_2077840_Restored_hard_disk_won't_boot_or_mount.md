---
title: "Restored hard disk won't boot or mount"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by qianian on 2012-10-29
Hi, avid learner here, please reply with each step. I apologize for the long-windedness. How can I get my new SSD to boot?

I used partimage from a live boot CD to copy / and /home partitions from my old HDD to a new SSD. I also made a swap and extended partition but simply formatted those using gparted without cloning any data. 

The newly restored SSD wouldn't boot immediately so I used the live disk to boot using a detected Linux system. I ran Grub Rescue in that session and rebooted. Here's the URL from Grub Rescue: [http://paste.ubuntu.com/1314100](http://paste.ubuntu.com/1314100)

I got a black screen on every reboot, so I booted from live disk again, but when I selected to use a detected Linux system I just got a black screen. From the live CD environment I saw the SSD's / partition had an unrecognized fs. fsck came up with endless errors. I wiped and restored / from partimage again. Then I booted and Ubuntu startup screen indicated it couldn't mount /home. I tried to mount manually but it didn't like the filesystem. It hung on shutdown.

Finally I ran boot-repair from live disk. The / and /home partitions can't be mounted so the program doesn't detect the Linux OS. EDIT: Here's the boot-repair output: [http://paste2.org/p/2398880](http://paste2.org/p/2398880)

# fdisk -l

Disk /dev/sda: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00055639

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           2       10240   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2   *           2        1277    10240000   83  Linux
/dev/sda3            1277        1404     1024000   82  Linux swap / Solaris
/dev/sda4            1404       29186   223155200   83  Linux

Disk /dev/sdb: 499.4 GB, 499405291520 bytes
255 heads, 63 sectors/track, 60715 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b0789

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60716   487699456   83  Linux

# blkid
/dev/sda1: UUID="e6294b13-8db5-49b1-a4ca-28c6159b6d25" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: LABEL="swap" UUID="438412f6-d739-45cd-9f42-030d2614112c" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: LABEL="Smalrus" UUID="7f0114cb-faea-41e7-b3c9-6cc772e53fc8" TYPE="ext3" 

# file -sL /dev/sda1
/dev/sda1: Linux rev 1.0 ext3 filesystem data, UUID=e6294b13-8db5-49b1-a4ca-28c6159b6d25
# file -sL /dev/sda2
/dev/sda2: data
# file -sL /dev/sda3
/dev/sda3: Linux/i386 swap file (new style), version 1 (4K pages), size 255999 pages, LABEL=swap, UUID=438412f6-d739-45cd-9f42-030d2614112c
# file -sL /dev/sda4
/dev/sda4: data

#dmesg:

root@debian:/home/user# dmesg | tail
[  934.387580] qnx4: wrong fsid in superblock.
[  971.785973] EXT4-fs (sda2): VFS: Can't find ext4 filesystem
[  981.309947] VFS: Can't find ext3 filesystem on dev sda2.
[ 1384.143283] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 1384.143457] FAT: bogus number of reserved sectors
[ 1384.143461] VFS: Can't find a valid FAT filesystem on dev sda4.
[ 1384.143650] qnx4: wrong fsid in superblock.
[ 1411.153962] VFS: Can't find ext3 filesystem on dev sda4.
[ 1480.605957] EXT4-fs (sda4): VFS: Can't find ext4 filesystem
[ 1485.505981] VFS: Can't find an ext2 filesystem on dev sda4.

Thank you all so much for your help to get me this far.

---

### Post by dino99 on 2012-10-29
well the first thing to know is the actual uuids on that system:

```
sudo blkid
```

then to update (if needed) fstab with the correct uuid

```
sudo  gedit /etc/fstab
```

and be sure of grub installation

```
sudo grub-install /dev/sda
```

note: use the livecd

---

### Post by qianian on 2012-10-29
Thanks, dino, but I can't do that because blkid doesn't see the / or home partitions, sda2 and sda4. file doesn't even see they should be ext3 filetypes.
> 
# blkid
/dev/sda1: UUID="e6294b13-8db5-49b1-a4ca-28c6159b6d25" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda3: LABEL="swap" UUID="438412f6-d739-45cd-9f42-030d2614112c" TYPE="swap"
/dev/loop0: TYPE="squashfs"
/dev/sdb1: LABEL="Smalrus" UUID="7f0114cb-faea-41e7-b3c9-6cc772e53fc8" TYPE="ext3" 

# file -sL /dev/sda1
/dev/sda1: Linux rev 1.0 ext3 filesystem data, UUID=e6294b13-8db5-49b1-a4ca-28c6159b6d25
# file -sL /dev/sda2
/dev/sda2: data
# file -sL /dev/sda3
/dev/sda3: Linux/i386 swap file (new style), version 1 (4K pages), size 255999 pages, LABEL=swap, UUID=438412f6-d739-45cd-9f42-030d2614112c
# file -sL /dev/sda4
/dev/sda4: data


---

### Post by Androzani1 on 2012-10-29
Which version of ubuntu are you using?

Is there a chance that the SSD isn't compatible yet with the distro?

---

### Post by qianian on 2012-10-29
12.04 

The restored partition booted from Live CD and ran fine that first time, then with Grub Rescue. Could it be incompatible with grub itself?

---

### Post by Androzani1 on 2012-10-29
You'll have to ask someone else, I'm on XP and don't know much about Grub.

---

### Post by qianian on 2012-10-29
I went ahead and re-restored / and home to the SSD. It seemed like they responded differently after the first time they ran. Then I got

% grub-install /dev/sda
/dev/sda does not have any corresponding BIOS drive.

Do I need to copy an MBR or install Grub a different way?

---

### Post by darkod on 2012-10-29
If you are doing that from live mode you can't simply use grub-install /dev/sda without any parameters since live mode doesn't know which one is your root partition.

You have to first mount it at any temporary mount point and then pass that as parameter to grub-install. For example, lets say /dev/sda2 is your root partition, it would be:
```
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Also, you have to find the UUIDs with blkid and compare them with the UUIDs in /etc/fstab. If they don't match, it won't mount the partitions properly.

It's often better to copy the files instead of cloning a partition. For example fsarchiver is a backup program that can copy and restore the whole root partition. You can copy /home with a simple cp but with added options like -ax so that ownership and permissions are kept.

In any case, if the new partitions have different UUIDs you have to adjust /etc/fstab.

---

### Post by qianian on 2012-10-29
I believe grub-install was successful because I booted directly from the hard drive.

It stopped again on the startup screen unable to mount /home. I checked fstab from the prompt and the UUIDs still matched. 

When I try to use the live CD to boot into the hard drive it hangs on a black screen. Why would I be unable to boot into it after the first time? How can I mount /home manually from the startup screen prompt?

Thanks also for the lead on FSArchiver, it looks tricky for my level but I'll play with it now that I'm trying this all over again.

---

### Post by darkod on 2012-10-30
Did you try running fsck on the cloned home partition, just in case?

Boot ubuntu and since it can't mount home anyway, it means the partition will be unmounted. If it's not, unmount it yourself. Then try something like:
sudo fsck /dev/sdaX

for the correct partition.

I am not sure if you can mount /home manually once the OS is running, since usually it needs to find your user and its home folder while login. Other data partitions you can mount later, but I have never tried that with home.
When checking /etc/fstab don't check only the UUID, also see if the other parameters look correct like filesystem (ext4, ext3,etc).

---

### Post by qianian on 2012-11-02
Thanks for the suggestion. fsck turns up an endless list of errors to clear or fix.

I went ahead and did a clean install with manual partitions from Live CD 12.04.1. It didn't boot at first so I ran boot rescue with this output: [http://paste2.org/p/2410667](http://paste2.org/p/2410667) Booting up gets me to a purple ubuntu page that still can't mount /home. fstab looks right, except with the reinstall the /home was a volume in the /boot partition. It appears to be the same problem I experienced with the cloned /boot partition.

Then I did a clean install with default partitions. It booted once, then on restart I got the same grub error on black screen.

The new SSD came unformatted and I used gparted to make my original partitions at first.

Since it seems to be the hard disk rather than restore problem I'll start a new post and link it here.

---

### Post by qianian on 2012-11-02
Here's the new thread: [http://ubuntuforums.org/showthread.php?p=12333773#post12333773](http://ubuntuforums.org/showthread.php?p=12333773#post12333773)

---


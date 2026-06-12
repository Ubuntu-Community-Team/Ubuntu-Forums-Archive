---
title: "Ubuntu 12.04 halts in boot"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by smartgenes on 2014-04-30
Hi, my Ubuntu 12.04 crashed. I was able a couple of times to load the desktop in read-only mode,
then it halted on load. I can 'Escape' if I'm quick and get a Grub menu up.

When I e (edit) on the most recent update I get the following:

```
insmod part_msdos
insmod ntfs
set root='(hd0,msdos2)'
search--no-floppy --ffs-uuid --set=root=A8E48F75E48F492
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
echo 'Loading Linux...'
linux /boot/vmlinuz-3.11.0.19-generic root=UUID=A8E48F75E48F492
loop=/ubuntu/disks/root.disk no recovery
nomode set [COLOR=#545454][FONT=arial]\
[/FONT][/COLOR]echo 'Loading initial ramdisk...'
initrd /boot/initrd.img-3.11.0-19-generic
```

Am I correct in thinking that Windows has confused Ubuntu as to where the partitions are?
(I have a dual boot - I've been using Ubuntu for some time alongside a non-working Windows Vista - Vista was installed first)
- as I was expecting to read something like (hd0,1).

I tried to use the root command, though it didn't work for me.

When I type ls I get the following:

(msdisk) (loop0) (hd0) (hd0, msdos1) (hd0, msdos2) (hd0, msdos3) (hd0, msdos4) (hd1) (hd1, msdos1)

I also attempted to make a live Linux usb on a Windows machine -- that showed up as (hd2) (hd2, msdod1) --
but I wasn't able to boot into it.

Thanks for any help, I'm a little bit new to all this, but as you can see I'm prepared to give things a good go.

---

### Post by oldfred on 2014-04-30
Is this wubi? root.disk is wubi inside a NTFS partition.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

---

### Post by smartgenes on 2014-05-02
Infinite thanks, that advice has me back on Ubuntu at least via live-CD.
The ntfs appears to be on sda2. But...

```
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /win
ubuntu@ubuntu:~$ sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

fsck:

```
/win/ubuntu/disks/root.disk contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix<y>? yes

Inode 311395 was part of the orphaned inode list.  FIXED.
Inode 311457 was part of the orphaned inode list.  FIXED.
Inode 311507 was part of the orphaned inode list.  FIXED.
Inode 311530 was part of the orphaned inode list.  FIXED.
Inode 311544 was part of the orphaned inode list.  FIXED.
Inode 311565 was part of the orphaned inode list.  FIXED.
Inode 311635 was part of the orphaned inode list.  FIXED.
Inode 311658 was part of the orphaned inode list.  FIXED.
Deleted inode 312507 has zero dtime.  Fix<y>? yes

Inode 312509 was part of the orphaned inode list.  FIXED.
Inode 312612 was part of the orphaned inode list.  FIXED.
Error reading block 2503761 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 312599.  Ignore error<y>? yes

Force rewrite<y>? yes

Inode 312599, i_blocks is 66, should be 26.  Fix<y>? yes

Error writing block 2503761 (Attempt to write block to filesystem resulted in short write) while reading indirect blocks of inode 312416.  Ignore error<y>? yes

y
Inode 500749 was part of the orphaned inode list.  FIXED.
Inode 500752 was part of the orphaned inode list.  FIXED.
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -2494470 -2496032 -2497537 -(2499395--2499396) -(2499398--2499400) -(2499508--2499512) -2499612 -2499640 -2499778 -(2499783--2499784) -(2499798--2499799) -(2499803--2499804) -2499809 -2499812 -2499831 -(2499833--2499834) -2499837 -2499842 -2499844 -2499848 -2499850 -(2499853--2499854) -(2499861--2499868) -2499896 -(2499898--2499899) -2500624 -(2500655--2500662) -2501476 -(2501823--2501832) -(2501834--2501842) -(2503762--2503766) -2504668 -2505250 -2505255 -(2505264--2505266) -(2505271--2505277) -2505312 -(2505314--2505315) -2505317 -(2505361--2505365) -(2505367--2505369) -(2505379--2505382) -2505385 -(2505388--2505392) -(2505404--2505410) -2505425 -2505429 -(2505434--2505452) -(2514419--2514420) -(2514422--2514438) -2514472 -2514493 -(2514495--2514496) -(2514498--2514504) -2514528 -(2514549--2514551) -(2514553--2514568) -(2514578--2514587) -(2514589--2514590) -(2514616--2514620) -(2514640--2514643) -(2514683--2514684) -2514688 -2514690 -(2514754--2514757) -2514769 -2514771 -(2514817--2514824) -2514853 -(2515203--2515206) -(2515248--2515251) -(2515324--2515327) -(2515434--2515437) -(2515522--2515526) -2517166 -2518696 -(2519367--2519374) -(2521975--2521979) -(2669438--2669441) -(2669473--2669482) -2669507 -(4008398--4008429) -(4010580--4010581)
Fix<y>? yes

Free blocks count wrong for group #304 (0, counted=3).
Fix<y>? yes

Free blocks count wrong for group #305 (31, counted=170).
Fix<y>? yes

Free blocks count wrong for group #306 (13, counted=103).
Fix<y>? yes

Free blocks count wrong for group #307 (65, counted=101).
Fix<y>? yes

Free blocks count wrong for group #325 (0, counted=15).
Fix<y>? yes

Free blocks count wrong for group #489 (1815, counted=1849).
Fix<y>? yes

Free blocks count wrong (3798202, counted=3811623).
Fix<y>? yes

Inode bitmap differences:  -311395 -311457 -311507 -311530 -311544 -311565 -311635 -311658 -312507 -312509 -312612 -500749 -500752
Fix<y>? yes

Free inodes count wrong for group #304 (660, counted=668).
Fix<y>? yes

Free inodes count wrong for group #305 (666, counted=669).
Fix<y>? yes

Free inodes count wrong for group #489 (1015, counted=1017).
Fix<y>? yes

Free inodes count wrong (2344571, counted=2344525).
Fix<y>? yes


/win/ubuntu/disks/root.disk: ***** FILE SYSTEM WAS MODIFIED *****
/win/ubuntu/disks/root.disk: 310707/2655232 files (3.0% non-contiguous), 17430233/21241856 blocks
```



And here is my boot-repair, which will undoubtedly shed light on the matter:

[http://paste.ubuntu.com/7381774/](http://paste.ubuntu.com/7381774/)

The shell script you supplied to attempt to mount wubi tells me the volume is aready exclusively opened:

```
Mounting NTFS Partition
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
Mounting Wubi Disk
/media/Windows/ubuntu/disks/root.disk: No such file or directory
Done :)
Initializing nautilus-gdu extension
```

---

### Post by oldfred on 2014-05-02
Boot-Repair is not able to fix wubi. But is useful to see what is where.

You can only mount a partition once. You you would have to unmount with umount the previous mount if running more than one task that mounts differently.

But you seem to be getting all sorts of corruption. 
Is hard drive ok?
In Disks you can click on drive and see Smart Status. It can run lots of tests, but all I really know is passed is good and anything else is plan on a new drive.

---

### Post by smartgenes on 2014-05-03
Back on the old desktop after the repair, so it did something, though the drive is read-only again.

The hard drives don't mount, though this happened before the stall on boot, and on some boots they would mount. Internet access*ok, but Firefox won't start (again it managed to before) -- I was thinking of emailing some files from the drive.

Edit: once back in the live environment I did

```
sudo mount -o loop /media/acer/ubuntu/disks/root.disk /vdisk
```

 and was able to get inside the home folder and copy the files to the hard disk.

Now what.. Should I purge the wubi somehow & begin again,
and how do I get Windows booting correctly again?

---


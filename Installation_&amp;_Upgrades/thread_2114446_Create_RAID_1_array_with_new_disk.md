---
title: "Create RAID 1 array with new disk"
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by cthugha on 2013-02-10
Hello,

So I recently installed a new disk on my Ubuntu 12.04.2 LTS system, and I was wondering if it's possible to set up software RAID 1 with the new disk (sdb) without losing any data on the old disk (sda)?

Here is the output from fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001d526

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1886507007   943252480   83  Linux
/dev/sda2      1886509054  1953523711    33507329    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1886509056  1953523711    33507328   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/mapper/cryptswap1: 34.3 GB, 34311503872 bytes
255 heads, 63 sectors/track, 4171 cylinders, total 67014656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1cece66b

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

---

### Post by darkod on 2013-02-10
Yes, you can.

First you will need to make partitions of the same size on sdb. You can easily do that with parted:
```
sudo parted /dev/sdb
unit s
mklabel msdos
mkpart primary 2048 1886507007
mkpart primary 1886507008 1953523711
set 1 raid on
set 2 raid on
quit
```

Note: Before running the above commands think about your swap partition. It's very big, about 16GB. That is a lot of space to waste on swap. When you have lots or ram, you only need big swap if you plan to hibernate. In that case it should be 1.5 x RAM. If not planning to hibernate, swap can be 2GB or 4GB, that's enough. If you want to have smaller swap this is the chance to make the partition smaller when installing the raid.

In that case change the sector numbers above when creating the partitions. If you need help with that ask before running the commands.

After the above is done, you have two primary partitions which will serve to create two raid devices, for / and swap.

Now you need to create the raid devices with one member missing (you will add sda later there):
```
sudo apt-get install mdadm
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 missing /dev/sdb1
sudo mdadm --create /dev/md1 --level=1 --raid-devices=2 missing /dev/sdb2
```

If the above --create commands don't work, you might need to reboot after installing mdadm. If all worked, you should be able to see the arrays by:
```
cat /proc/mdstat
```

Post the output of that command and wait for further instructions. Don't reboot at this point, there is more to do.

---

### Post by cthugha on 2013-02-10
I'm confused. I kind of understand what's going on here:

> **darkod said:**
> 
First you will need to make partitions of the same size on sdb. You can easily do that with parted:
```
sudo parted /dev/sdb
unit s
mklabel msdos
mkpart primary 2048 1886507007
mkpart primary 1886507008 1953523711
set 1 raid on
set 2 raid on
quit
```


but shouldn't the partition boundaries match up?
wouldn't I need to do something more like:

```
sudo parted /dev/sdb
unit s
mklabel msdos
mkpart primary 2048 1886507007
mkpart primary 1886509054 1953523711
mkpart primary 1886509056 1953523711
set 1 raid on
set 2 raid on
quit
```

How do I shrink the swap space? I just checked, and I'm not using any of it. Would it be possible to turn the swap space into a RAID 0 array shared across both disks?

---

### Post by darkod on 2013-02-10
For your current install you used the automatic method which creates primary root partition and logical swap partition. That's why you have extended partition (sda2) holding one logical (sda5).

With only two partitions, there is not much sense using logical (extended) partition. It is used when you have 3 primary already because the limit is 4 primary partitions, so after the third you start creating logicals.

That's why I used mkpart for creating two primary partitions. Even if you wanted swap to be logical again, you won't use three mkpart commands. You will make one primary and one logical, the extended container is created automatically around the logical partition(s).

When creating swap on sdb, simply create it smaller. That's why I mentioned it, this is a good chance to make it smaller. In that case root can be little bigger and doesn't need to be matched to the current sda1 in size.

In that case, it's better to use MiB as unit in parted, not sectors. Try this:
```
sudo parted /dev/sdb
unit MiB
print
```

That will show the total size of the disk in MiB towards the top of the output. Lets say we will reserve 2GiB of swap on each disk (4GiB in total), that's 2048MiB. So, when you know the total size of the disk in MiB which should be like 942080MiB (the number will be slightly different), just subtract 2048 and you have the end point of the first partition. Then you can create it while still in the parted prompt with:
```
mkpart primary 1 XXXXXX
mkpart primary XXXXXX YYYYYY #(create swap from XXXXXX to the end YYYYYY)
set 1 raid on
quit
```

You are right, you don't need to raid swap, I don't have it raided in my raid1 server. That why we set the raid flag only on partition #1.

If you need help with the numbers about the partitions, just post the output of parted print command and we can help. I hope I explained my idea good. :)

And of course, if not raiding swap, you will not create the md1 device I mentioned earlier.

---

### Post by cthugha on 2013-02-10
Here are the outputs of parted print.

```

/$ sudo parted /dev/sdb
GNU Parted 2.3
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Error: /dev/sdb: unrecognised disk label
(parted) unit MiB
(parted) print
Error: /dev/sdb: unrecognised disk label
(parted) mklabel msdos
(parted) print
Model: ATA ST1000DM003-9YN1 (scsi)
Disk /dev/sdb: 953870MiB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags

(parted) quit
Information: You may need to update /etc/fstab.

/$ sudo parted /dev/sda
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Model: ATA ST1000DM003-9YN1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  966GB   966GB   primary   ext4         boot
 2      966GB   1000GB  34.3GB  extended
 5      966GB   1000GB  34.3GB  logical

(parted) unit MiB
(parted) print
Model: ATA ST1000DM003-9YN1 (scsi)
Disk /dev/sda: 953870MiB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start      End        Size       Type      File system  Flags
 1      1.00MiB    921146MiB  921145MiB  primary   ext4         boot
 2      921147MiB  953869MiB  32722MiB   extended
 5      921147MiB  953869MiB  32722MiB   logical

(parted)
```

To confirm, I want to do the following:

```

sudo parted /dev/sdb
unit MiB
mkpart primary 1 951822
mkpart primary 951823 953869
set 1 raid on
quit

```

---

### Post by darkod on 2013-02-10
Correct.

After that use the newly created big sdb1 partition to create md device with one missing member:
```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 missing /dev/sdb1
```

You might need to install mdadm and reboot before being able to use the --create option.

After creating it make a filesystem on the array and check if it's automatically in mdadm.conf or not:
sudo mkfs.ext4 /dev/md0
cat /etc/mdadm/mdadm.conf

If you don't see an ARRAY definition there for md0, make a copy of the file and generate the definition with:
sudo cp /etc/mdadm/mdadm.conf /etc/mdadm/mdadm.conf.orig
sudo mdadm --examine --scan >> /etc/mdadm/mdadm.conf

If you check mdadm.conf again you should see the ARRAY definition at the bottom.

---

### Post by cthugha on 2013-02-10
Here are the outputs:
```

user:/$ sudo parted /dev/sdb
GNU Parted 2.3
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit MiB
(parted) mkpart primary 1 951822
(parted) mkpart primary 951823 953869
(parted) set 1 raid on
(parted) print
Model: ATA ST1000DM003-9YN1 (scsi)
Disk /dev/sdb: 953870MiB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start      End        Size       Type     File system  Flags
 1      1.00MiB    951822MiB  951821MiB  primary               raid
 2      951823MiB  953869MiB  2046MiB    primary

(parted) quit
Information: You may need to update /etc/fstab.

uesr:/$ sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 missing /dev/sdb1
mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.
user:/$ sudo mkfs.ext4 /dev/md0
mke2fs 1.42 (29-Nov-2011)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
60915712 inodes, 243633360 blocks
12181668 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
7436 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000, 214990848

Allocating group tables: done
Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

user:/$ cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Sun, 30 Sep 2012 22:38:06 -0500
# by mkconf $Id$
user:/$ cat /etc/mdadm/mdadm.conf |grep ARRAY
user:/$ sudo cp /etc/mdadm/mdadm.conf /etc/mdadm/mdadm.conf.orig
user:/$ sudo mdadm --examine --scan >> /etc/mdadm/mdadm.conf
-bash: /etc/mdadm/mdadm.conf: Permission denied
user:/$ sudo mdadm --examine --scan >> /etc/mdadm/mdadm.conf
-bash: /etc/mdadm/mdadm.conf: Permission denied
user:/$ sudo su
root:/# mdadm --examine --scan >> /etc/mdadm/mdadm.conf
root:/# exit
exit
user:/$ cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Sun, 30 Sep 2012 22:38:06 -0500
# by mkconf $Id$
ARRAY /dev/md/0 metadata=1.2 UUID=6a592df0:3183e7f1:c183aae0:673586f1 name=MACHINE_NAME:0

```
What should I do next?

---

### Post by darkod on 2013-02-11
OK, as you can see the ARRAY definition exists now at the bottom of mdadm.conf. This should assemble the array on every boot.

Now comes the fun part. You need to copy your system over to the array. I think it's best to be done from live mode because then your root is not mounted. It would be something like:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan #(to assemble the array in live mode)
sudo mkdir /mnt/oldroot
sudo mkdir /mnt/md0
sudo mount /dev/sda1 /mnt/oldroot
sudo mount /dev/md0 /mnt/md0
cd /mnt/oldroot
sudo cp -dpRx * /mnt/md0/ #(this should copy all keeping permissions)
```

Hopefully that will be done successfully. I'm trying to do it this way to keep your original system on sda untouched until we confirm the raid works. :) That is best in my opinion.

So, after the copy ends (it might take long depending how much data you have), you need to edit few files in the newly copied root (on md0):
```
gksu gedit /mnt/md0/etc/fstab
```

In fstab for the root line replace the UUID=<string> with the string for the md0 (this UUID is in mdadm.conf if I'm not mistaken). You can also put /dev/md0 instead of UUID=<string> for a start.
Also change the UUID of swap with the UUID of the swap partition you created sdb2. You can check the UUID with:
sudo blkid

I forgot to mention, it's time we format swap too, it will not have UUID until it's formatted. So format it first:
sudo mkswap /dev/sdb2

So, after you have adjusted fstab save and close the file. I'm not 100% sure we need to update the intiramfs with chroot but it doesn't hurt doing it:
```
sudo mount --bind /proc /mnt/md0/proc
sudo mount --bind /dev /mnt/md0/dev
sudo mount --bind /sys /mnt/md0/sys
sudo chroot /mnt/md0
update-initramfs -u
exit
sudo umount /mnt/md0/sys
sudo umount /mnt/md0/dev
sudo umount /mnt/md0/proc
sudo umount /mnt/md0
sudo umount /mnt/oldroot
```

That should unmount all, reboot and see how it goes. At this point your old install will still load automatically. Lets see if it works.

---

### Post by cthugha on 2013-02-13
If my server automatically restarted before doing this, would it make it so the server was unable to boot?

---

### Post by darkod on 2013-02-13
No, you still hasn't changed completely over to the raid. I don't know if there could be other issues depending when exactly it restarted. For example if it restarted during copying, it will stop and later you don't know where it stopped exactly so you might need to copy everything again.

But booting should continue as normal since you are still doing it from the single disk, not the raid.

---

### Post by cthugha on 2013-02-13
Well, I'm not physically near the server right now, so I don't really know what's going on. Hopefully, its a network issue. No chance of data corruption or loss there.

I'm planning on doing the copy tomorrow night 7 CST, so, it shouldn't be anything related to that.

---

### Post by cthugha on 2013-02-13
So I didn't stay on the error screen long enough to really soak in the error, but, what I did see was similar to:

> Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash) 
Enter 'help' for a list of built-in commands

(initramfs)

After I typed "exit" at the prompt it mounted sda1 properly. Would this be at all related?

---

### Post by darkod on 2013-02-14
I don't know. There is a possibility something got slightly corrupted due to the power off. You can try fsck from live mode (root needs to be unmounted):
sudo fsck /dev/sda1

to check the filesystem.

The important thing is did you do the copy before the power off? Did it finish?

---

### Post by cthugha on 2013-02-14
I just finished the copy. It looks like the hangup during reboot is that mdadm sees an unfinished RAID array and gets understandably upset. It's actually a feature.

I wasn't able to grab the output of the terminal, but everything went off without a hitch. What should I do next?

---

### Post by darkod on 2013-02-15
I would try to add the raid root to grub2 boot menu with:
sudo update-grub

You should run that from the sda1 installation, just boot it as normal and run it. See if it says it finds Ubuntu on /dev/md0, etc.

If it does find it, it should add an entry in grub boot menu. Reboot and try to boot the Ubuntu on /dev/md0. Lets see if it boots.

---

### Post by cthugha on 2013-02-15
So I rebooted, but I think it booted from sda1.

How do I force it to boot from md0? Also, here are the results from fdisk -l

```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001d526

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1886507007   943252480   83  Linux
/dev/sda2      1886509054  1953523711    33507329    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1886509056  1953523711    33507328   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00062f84

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1949331455   974664704   fd  Linux raid autodetect
/dev/sdb2      1949333504  1953523711     2095104   83  Linux

Disk /dev/md127: 997.9 GB, 997922242560 bytes
2 heads, 4 sectors/track, 243633360 cylinders, total 1949066880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md127 doesn't contain a valid partition table

Disk /dev/mapper/cryptswap1: 34.3 GB, 34311503872 bytes
255 heads, 63 sectors/track, 4171 cylinders, total 67014656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x18b6f6fe

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table


```

---

### Post by darkod on 2013-02-16
1. At boot do you have the grub2 menu giving you option to boot ubuntu on the raid? Did you run update-grub?

2. Is your array named md127 or md0? fdisk says md127.

---

### Post by cthugha on 2013-02-17
When I reboot, I'm met with the ash shell thing
Here is the output from update-grub:

```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

I named it md0 but it appears to have changed names somehow.

---

### Post by darkod on 2013-02-17
Can you post the output of:
```
sudo parted -l (small L)
```

---

### Post by cthugha on 2013-02-17
Here is the output:
```

Model: ATA ST1000DM003-9YN1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  966GB   966GB   primary   ext4         boot
 2      966GB   1000GB  34.3GB  extended
 5      966GB   1000GB  34.3GB  logical


Model: ATA ST1000DM003-9YN1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  998GB   998GB   primary                  raid
 2      998GB   1000GB  2145MB  primary  linux-swap(v1)


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 34.3GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  34.3GB  34.3GB  linux-swap(v1)


Model: Linux Software RAID Array (md)
Disk /dev/md127: 998GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  998GB  998GB  ext4

```

---

### Post by darkod on 2013-02-17
If you temporary mount md127 and look into the /boot folder, what does it say?

```
sudo mount /dev/md127 /mnt
ls /mnt/boot
ls /mnt/boot/grub
cat /mnt/etc/fstab
sudo blkid
```

---

### Post by cthugha on 2013-02-17
```
:/$ ls /mnt/boot
abi-3.2.0-23-generic         memtest86+.bin
abi-3.2.0-31-generic         memtest86+_multiboot.bin
config-3.2.0-23-generic      System.map-3.2.0-23-generic
config-3.2.0-31-generic      System.map-3.2.0-31-generic
grub                         vmlinuz-3.2.0-23-generic
initrd.img-3.2.0-23-generic  vmlinuz-3.2.0-31-generic
initrd.img-3.2.0-31-generic
:/$ ls /mnt/boot/grub
915resolution.mod            gcry_tiger.mod      parttool.mod
acpi.mod                     gcry_twofish.mod    password.mod
adler32.mod                  gcry_whirlpool.mod  password_pbkdf2.mod
affs.mod                     gettext.mod         pbkdf2.mod
afs_be.mod                   gfxblacklist.txt    pci.mod
afs.mod                      gfxmenu.mod         play.mod
aout.mod                     gfxterm.mod         png.mod
ata.mod                      gptsync.mod         probe.mod
ata_pthru.mod                grldr.img           pxeboot.img
at_keyboard.mod              grub.cfg            pxecmd.mod
befs_be.mod                  grubenv             pxe.mod
befs.mod                     gzio.mod            raid5rec.mod
biosdisk.mod                 halt.mod            raid6rec.mod
bitmap.mod                   hashsum.mod         raid.mod
bitmap_scale.mod             hdparm.mod          read.mod
blocklist.mod                hello.mod           reboot.mod
boot.img                     help.mod            regexp.mod
boot.mod                     hexdump.mod         reiserfs.mod
bsd.mod                      hfs.mod             relocator.mod
btrfs.mod                    hfsplus.mod         scsi.mod
bufio.mod                    hwmatch.mod         search_fs_file.mod
cat.mod                      iorw.mod            search_fs_uuid.mod
cdboot.img                   iso9660.mod         search_label.mod
chain.mod                    jfs.mod             search.mod
cmostest.mod                 jpeg.mod            sendkey.mod
cmp.mod                      kernel.img          serial.mod
command.lst                  keylayouts.mod      setjmp.mod
configfile.mod               keystatus.mod       setpci.mod
core.img                     legacycfg.mod       sfs.mod
cpio.mod                     linux16.mod         sleep.mod
cpuid.mod                    linux.mod           squash4.mod
crypto.lst                   lnxboot.img         tar.mod
crypto.mod                   loadenv.mod         terminal.lst
cs5536.mod                   locale              terminal.mod
datehook.mod                 loopback.mod        terminfo.mod
date.mod                     lsacpi.mod          test_blockarg.mod
datetime.mod                 lsapm.mod           testload.mod
diskboot.img                 lsmmap.mod          test.mod
dm_nv.mod                    ls.mod              tga.mod
drivemap.mod                 lspci.mod           trig.mod
echo.mod                     lvm.mod             true.mod
efiemu32.o                   lzopio.mod          udf.mod
efiemu64.o                   mdraid09.mod        ufs1.mod
efiemu.mod                   mdraid1x.mod        ufs2.mod
elf.mod                      memdisk.mod         uhci.mod
example_functional_test.mod  memrw.mod           unicode.pf2
ext2.mod                     minicmd.mod         usb_keyboard.mod
extcmd.mod                   minix2.mod          usb.mod
fat.mod                      minix.mod           usbms.mod
font.mod                     mmap.mod            usbserial_common.mod
fshelp.mod                   moddep.lst          usbserial_ftdi.mod
fs.lst                       msdospart.mod       usbserial_pl2303.mod
functional_test.mod          multiboot2.mod      usbtest.mod
g2hdr.img                    multiboot.mod       vbe.mod
gcry_arcfour.mod             nilfs2.mod          vga.mod
gcry_blowfish.mod            normal.mod          vga_text.mod
gcry_camellia.mod            ntfscomp.mod        video_bochs.mod
gcry_cast5.mod               ntfs.mod            video_cirrus.mod
gcry_crc.mod                 ntldr.mod           video_fb.mod
gcry_des.mod                 ohci.mod            videoinfo.mod
gcry_md4.mod                 part_acorn.mod      video.lst
gcry_md5.mod                 part_amiga.mod      video.mod
gcry_rfc2268.mod             part_apple.mod      videotest.mod
gcry_rijndael.mod            part_bsd.mod        xfs.mod
gcry_rmd160.mod              part_gpt.mod        xnu.mod
gcry_seed.mod                partmap.lst         xnu_uuid.mod
gcry_serpent.mod             part_msdos.mod      xzio.mod
gcry_sha1.mod                part_sun.mod        zfsinfo.mod
gcry_sha256.mod              part_sunpc.mod      zfs.mod
gcry_sha512.mod              parttool.lst
:/$ cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4d89f5ad-17e9-4178-ad7c-f191eed788d3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9989bff1-3b47-4326-b14c-cc0ff1dc513f none            swap    sw              0       0
:/$ sudo blkid
/dev/sdb1: UUID="6a592df0-3183-e7f1-c183-aae0673586f1" UUID_SUB="bde5edb0-9347-f455-3dab-76aa661ef456" LABEL="Server:0" TYPE="linux_raid_member"
/dev/sdb2: UUID="9989bff1-3b47-4326-b14c-cc0ff1dc513f" TYPE="swap"
/dev/sda1: UUID="cb06beb8-e3d6-4258-a871-869dec6f5715" TYPE="ext4"
/dev/md127: UUID="4d89f5ad-17e9-4178-ad7c-f191eed788d3" TYPE="ext4"
/dev/mapper/cryptswap1: UUID="85c05a85-e7de-487e-a964-2b049cba25e3" TYPE="swap"
:/$

```

---

### Post by darkod on 2013-02-17
Most of it looks good. But I think the issue is that somehow the md0 was renamed to md127, including the UUID is wrong.

Can you now post:
cat /etc/mdadm/mdadm.conf

---

### Post by cthugha on 2013-02-17
```
:/$ cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Sun, 30 Sep 2012 22:38:06 -0500
# by mkconf $Id$
ARRAY /dev/md/0 metadata=1.2 UUID=6a592df0:3183e7f1:c183aae0:673586f1 name=Server:0

```

---

### Post by darkod on 2013-02-18
The raid definition looks correct for md0. It still assembles md127 on boot?

Try stopping it and assembling md0 with something like:
```
sudo mdadm --stop /dev/md127
sudo mdadm --assemble /dev/md0 missing /dev/sdb1
```

See if that assembles md0 and if it does run update-grub and see if the OS on it is recognized.

Also, once it's recognized you might need to enter it with chroot and update the initramfs. That would be like:
```
sudo mount /dev/md0 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
update-initramfs
update-grub
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

See if that changes anything.

---

### Post by cthugha on 2013-02-18
I keep getting this error:

```
:/# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.2.0-31-generic
mdadm: cannot open /dev/md/0: No such file or directory

```

---

### Post by darkod on 2013-02-18
Open mdadm.conf and delete the ARRAY definition. Then have it make a new definition automatically with:
sudo mdadm --examine --scan >> /etc/mdadm/mdadm.conf

Regardless whether it creates the new definition as md0 or md127, see if update-grub will detect it.

If it doesn't, do the chroot again and try update-initramfs again.

The array somehow got messed up, not sure how. Maybe with the power off /stopping of the first copy, or what ever happened exactly.

It should have been much more straightforward than this. But I remember you said something happened when it copying first time.

---

### Post by cthugha on 2013-02-18
that didn't work, I'm going to format the drive and start over

---

### Post by cthugha on 2013-02-19
Would the following code work (even if it is a bit wasteful)
```

sudo sfdisk -d /dev/sda | sfdisk /dev/sdb
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 missing /dev/sda
sudo mdadm --add /dev/md0 /dev/sdb

```

---

### Post by darkod on 2013-02-19
The first command, personally I would create the partitions manually like you did last time with parted. Also, you wanted to make swap lower at the same time, remember? If you copy the table the partitions will be identical. I don't like using sfdisk and copying partition tables. It takes 2mins to make partitions manually with parted, and you have perfect control.

The second command, no. Regardless whether you make the partitions manually or by copying the table with sfdisk, you add partition(s) to create the md devices, not with disks. /dev/sda is the whole disk. You would use /dev/sda1 or /dev/sdb1 for md0, depending which partition is the new one, and use 'missing' for the other one.

The same applies for the --add command later, you don't add the whole disk unless the array is made of disks instead of partitions. This is very important. If you created md device using partitions, you DO NOT add disks to that device in the future, never. Only partitions. It's one or the other, not mixing them.

In your case if you use disks you can't make swap. Remember that one md deice can have only one mount point. If the whole /dev/sda and /dev/sdb make md0 which will be root, what will be swap???

---

### Post by cthugha on 2013-02-19
Well, I want to do as much while the server is hot as possible, because downtime is just painful for everyone. So if moving the partitions around is going to cause as much downtime as it has, I'd like to avoid it and waste some space. I'd also rather copy the partitions auto-magically so everything matches up perfectly.

If I can re-size the partitions on sda in one live session or while running hot, I would do that.

```

sudo sfdisk -d /dev/sda | sfdisk /dev/sdb
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 missing /dev/sda1
sudo mdadm --add /dev/md0 /dev/sdb1

```

---

### Post by darkod on 2013-02-19
I'm confused. The first step was to partition the newly added disk and create md array on it. Why would that involve any downtime?

You are running from sda, business as usual, and you are partitioning sdb. Later creating the md device which doesn't involve downtime either.

The only part where it might be better to run in live mode, is the copying, so that you are sure that files are not changing while copying. But you can do the copying while hot with rsync too. Not sure if that copies 100% while running from sda though.

---

### Post by cthugha on 2013-02-20
what if, instead I:
removed the cryptswap (sda5)
shrunk sda2
set sda2 to be the swap
increased the size of sda1 using gparted in a live session
copied the partition tables from sda to sdb
create a RAID array missing sdb
add sdb to the RAID array

Then I don't have to muck around with boot configuration or copy anything from sda to sdb.

---

### Post by darkod on 2013-02-21
You can't create the raid on the same disk where the data is right now. It will format it during creation of the md device.

The only way to move from single disk to mdadm raid1, is to partition the new disk (this doesn't involve downtime since you are not using it), create md device with this new disk and missing the first one, copy data, try to boot from the array and run from it to confirm it works, and then add the old (first) disk to the array and let it sync.

I think your procedure was correct only that during the first copy it powered off or what ever, and this is what created issues.

---


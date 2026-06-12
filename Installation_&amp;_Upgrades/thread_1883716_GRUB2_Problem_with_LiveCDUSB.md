---
title: "GRUB2 Problem with LiveCD/USB"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by nicklemarr on 2011-11-19
[SIZE=2]Alright, first off, forgive my ignorance, I'm very new to *nix. Before yesterday I'd only used #!, Knoppix, Backtrack; and that was a long time ago.

I'm trying to install Ubuntu, and in the installation when it "installs GRUB2" I get an error because of the following:[/SIZE] [SIZE=2]

 The problem is that plugininstall.py runs grubinstaller.py which in turn  runs /usr/share/grub-installer/grub-installer and that program crashes  when /var/cache/debconf/config.dat is in use (locked). That crash causes  grubinstaller.py to return error code 1 and abort. The reason that  /var/cache/debconf/config.dat is locked is that the installer is written  in python and runs a program called "debconf-communicate" which stays  open for as long as the installer is open, and that is the process which  is locking the file.[/SIZE] [B][SIZE=2]
[/SIZE]


[/B][SIZE=2]So as a messy workaround I did the following:[/SIZE]
 
[SIZE=1]**cd /usr/lib/ubiquity/ubiquity/components/**
**sudo rm grubinstaller.pyc**[/SIZE] [SIZE=1]
**sudo gedit grubinstaller.py**[/SIZE] 

[SIZE=2]Replaced "/usr/share/grub-installer/grub-installer" with "ls".

 Thus grubinstaller.py doesn't install Grub. Instead, it will simply  execute a meaningless "ls" (directory index) command. That means that  you never run into the problem of grub-installer crashing since it's never executed.[/SIZE] [SIZE=2]

The installer finishes now, but now I need to instal GRUB2 manually. So this is what I want to do:[/SIZE] 

[SIZE=1][B]sudo passwd root
su
mount /dev/sda1 /target[/B]
[B]mount -o bind /dev /target/dev
mount -o bind /dev/pts /target/dev/pts
mount -o bind /sys /target/sys
mount -o bind /proc /target/proc
chroot /target
grub-install /dev/sda[/B][/SIZE] [SIZE=1]
**reboot**[/SIZE] 

[SIZE=2] But this is what I get:[/SIZE]
[B]
[SIZE=1]sudo passwd root
[/SIZE][/B][SIZE=1][I]Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully[/I][B]
su
[/B]*Password: *[B]
# mount /dev/sda1 /target
# mount -o bind /dev /target/dev
[/B]*mount: mount point /target/dev does not exist*[B]
# mount -o bind /dev /target/dev
[/B]*mount: mount point /target/dev does not exist*[B]
# mount -o bind /dev /target/dev
[/B]*mount: mount point /target/dev does not exist*[B]
# mount /dev/sda1 /target
[/B]*mount: /dev/sda1 already mounted or /target busy**mount: according to mtab, /dev/sda1 is already mounted on /target*[B]
# mount -o bind /dev/pts /target/dev/pts
[/B]*mount: mount point /target/dev/pts does not exist*[B]
# mount -o bind /sda1/dev /target/dev
[/B]*mount: mount point /target/dev does not exist*[B]
# chroot /target
[/B]*chroot: failed to run command `/bin/bash': No such file or directory*[B]
# sudo /target
[/B]*sudo: /target: command not found*[B]
# grub-install /dev/sda
[/B]*grub-probe: error: cannot stat `aufs'.**/usr/sbin/grub-probe: error: cannot stat `aufs'.*[B]
# sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
[/B]*mount: mount point /mnt/dev does not exist*[B]
# sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
[/B]*mount: /dev/sda1 already mounted or /mnt busy**mount: according to mtab, /dev/sda1 is already mounted on /mnt*[B]
# sudo chroot /mnt
[/B]*chroot: failed to run command `/bin/bash': No such file or directory*[B]
# chroot /mnt apt-get install grub-pc
[/B]*chroot: failed to run command `apt-get': No such file or directory*[B]
# chroot /mnt
[/B]*chroot: failed to run command `/bin/bash': No such file or directory*[/SIZE]


[SIZE=2]As you can see, I have mo clue at what I'm doing. I just want this to work. Can anyone shed some light on where I'm messing up. It's probably something obvious, but I'm sleep deprived right now.
[/SIZE]

---

### Post by darkod on 2011-11-19
I would rather do the mount commands one by one so you know where it fails. If /dev/sda1 is your root partition the group of commands to chroot into an existing installation is (DO NOT have anything mounted in advance, you start from a fresh live mode):

```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
```

After that you can run commands as root inside the installation, namely:

```
grub-mkconfig (just in case the config files were never created when the grub2 install failed)
grub-install /dev/sda
```

---

### Post by nicklemarr on 2011-11-19
[QUOTE=darkod;11472252]
```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
```Okay, well went to a fresh live session. Installed. This is what happens on the first two. Every time.

```
**sudo mount /dev/sda1 /mnt**[I]
mount: /dev/sda1 already mounted or /mnt busy[/I][I]
mount: according to mtab, /dev/sda1 is already mounted on /mnt[/I][B]
sudo mount --bind /dev /mnt/dev[/B][I]
mount: mount point /mnt/dev does not exist[/I]
**sudo mount --bind /sys /mnt/sys**[I]
mount: mount point /mnt/sys does not exist[/I][B]
sudo mount --bind /proc /mnt/proc[/B][I]
mount: mount point /mnt/proc does not exist[/I]
**sudo chroot /mnt**
*chroot: failed to run command `/bin/bash': No such file or directory*
```

---

### Post by darkod on 2011-11-19
I'm confused. Why does it say that /dev/sda1 is already mounted in a fresh live session? The live session doesn't mount the root partition from the hdd.

Can you post the results of:
sudo fdisk -l (small L)

Do you know which partition is what on your hdd?

---

### Post by nicklemarr on 2011-11-19
> **darkod said:**
> I'm confused. Why does it say that /dev/sda1 is already mounted in a fresh live session?

Because I have to install the OS first, otherwise the GRUB2 would be erased? Is that not correct?

> Can you post the results of:
sudo fdisk -l (small L)```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 16.0 GB, 16013942784 bytes
255 heads, 63 sectors/track, 1946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe51f32d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1947    15638615+  ee  GPT

Disk /dev/sdc: 4.0 GB, 3942784 bytes
255 heads, 63 sectors/track, 413 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         488     3913600    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(486, 254, 63) logical=(487, 58, 19)
```> Do you know which partition is what on your hdd?I'm using the entire drive, and let the installer decide what's what. Is that a problem?

---

### Post by darkod on 2011-11-19
It's not a problem to install ubuntu on the whole disk letting the installer decide how to split it.

But in your case you don't seem to have ubuntu installed at all. In the first post you said only grub2 doesn't get installed. But the fdisk results don't show linux partitions.

That's why the mount commands fail.

Also, I would replace the GPT partition table on the 16GB disk with MSDOS. Much easier to use.

First make the install, and if grub2 fails you can try to add it later, but you need to have the ubuntu installed first. You don't seem to have it on /dev/sda (16GB).

---

### Post by nicklemarr on 2011-11-20
I finally made some progress by using Gparted to change is from GPT to MSBIOS before installing the OS.

Then when I install it, it automatically deletes the partion table back to GPT. (I'm assuming).
This is the error I get when I get to the last list. If I can just get passed this step then everything will be fine.


```
**grub-install /dev/sda**
[I]/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.[/I]
```

---

### Post by darkod on 2011-11-20
Did you actually create a msdos table or just deleted the existing partitions? Because deleting the partitions doesn't change the table type.

Another option is to simply install on gpt table. In this case grub needs a small partition at the beginning of the disk which will have the bios_grub flag. You can do it like this:

1. Boot with the cd in live mode. Open Gparted.
2. Delete all partitions on the disk.
3. Create one small 32MB partition at the start of the disk, fat32 type. Hit the green tick mark button in Gparted to apply the change.
4. After the partition is created right click on it and select Manage Flags. From the list of flags activate bios_grub.
5. Click again the green button to apply, if needed.

Then just reboot with the cd again and install.

---

### Post by oldfred on 2011-11-20
Actually it is UEFI that has to have a FAT32 partition as the first partition.

With gpt and BIOS you need a bios_grub partition and it can be anywhere on the drive. Since I may move drives to a newer computer, I now create both the FAT32 efi and a bios_grub partition at the beginning of every new drive, but only one or the other will be used.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
BIOS Boot Partition of 1 MiB for partition alignment.

sudo parted /dev/sda set <partition_number> bios_grub on

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using EFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
To be safe, create both of these partitions, in addition to your regular Linux partitions. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

```
fred@fred-MavericDT:~$ sudo parted /dev/sdd unit s print
[sudo] password for fred: 
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sdd: 117231408s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size       File system  Name  Flags
 1      2048s      616447s     614400s    fat32              boot
 2      616448s    618495s     2048s                         bios_grub
 3      618496s    58925055s   58306560s  ext4         04
 4      58925056s  117229567s  58304512s  ext4         10

```

---


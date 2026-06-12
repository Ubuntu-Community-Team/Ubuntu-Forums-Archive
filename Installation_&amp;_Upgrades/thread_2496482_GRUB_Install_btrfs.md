---
title: "GRUB Install btrfs"
date: 2024-03-30
forum: Installation &amp; Upgrades
---

### Post by yuralamov on 2024-03-30
Hello. I ran into a problem. Installer error during bootloader installation.
sda1 -512M - efi
sda2 - 1536M - boot
sdb1 - 2G - swap
sda3 + sdb2 =
```

mkfs.btrfs -L bt_root -d raid0 -m raid0 -f /dev/sda3 /dev/sdb2

```
install =
use efi, swap
use boot - format ext4
use sda3 / - not format
When it comes to grub install - error

---

### Post by yancek on 2024-03-30
> When it comes to grub install - error 		 

 If you actually want help, you will need to post the complete/exact error you receive.  I've seen a number of threads here from people who are having problems with btrfs plus you have RAID which complicates things also.  Are you also using LVM, encryption?

---

### Post by yuralamov on 2024-03-30
There is no encryption. if you just btrfs on lvm(raid 0), then everything is ok(where I stopped). but if raid 0 in btrfs - err. If you do this manually in arch-linux, then there is no error

---

### Post by MAFoElffen on 2024-03-30
You are trying to do btrfs... Right?

So where, in which step did you create your brfs RAID1 member and format the filesystem on it for the installer to use mounted to it as "/"?

Note: the older installer in 22.04 will see that, and you cn point to that in the installer to use. The newer installers after that don't recognise those kinds of things yet (I have  bug report filed on the newer partitioner because of that).

Show me the manual commands you used for creating the LVM RAID1 Volume Group... Then for creating the LV's on that VG. Then formating that LV to BTRFS... before you switched over to the installer to point it to it to use as btrfs, not format, and mount as "/"...

This is not my first rodeo. I've done it and know it works as expected. I know LVM RAID is outside of the norm. I too think outside the box. I have tested that, and it does work. 

Inside of the norm a bit, would be doing btrfs raid member types. Why did you opt not to go that way?

---

### Post by yuralamov on 2024-03-31
You did not understand me. I'm trying to make software RAID0 on 2 HDDs  identical drives WD 2T (/dev/sda & /dev/sdb).
1 I loading from live usb-key ubuntu-desktop (20.06 or 22.04.3 or 22.04.4)
2 launch the terminal.
```

sudo su -
fdisk /dev/sda

```
g, n +512M, n +1536M, n remnant, w
```

fdisk /dev/sdb

```
g, n +2G, n remnant, w
2 options for creating a raid0
2.a the first one works (BTRFS on LVM)
```

pvcreate /dev/sda3 /dev/sdb2
vgcreate vg01 /dev/sda3 /dev/sdb2
lvcreate -i2 -I64 -l 70%FREE -n lv_root vg01

```
2.b the second one should work, but doesn't
```

mkfs.btrfs -L bt_root -d raid0 -m raid0 -f /dev/sda3 /dev/sdb2

```
3 sudo & terminal exit and launch ubuntu install
/dev/sda1 - use as efi
/dev/sda2 - use as ext4, format, /boot
/dev/sdb1 - use as swap
and vg01-lv_root (2.a) or /dev/sda3 (2.b), not format, mount /
result:
2.a - Ok. The installation was successful, everything works
2.b - error at stage grub-install
Without leaving the living system: 
the file system is creat and mounted in the directory /target
sections (/dev/sda3 and /dev/sdb2) are synchronized
====
my notes for myself github.com/yuralamov/ubuntu-tuning/blob/main/raid

---

### Post by MAFoElffen on 2024-03-31
Have you tried to create a separate partition for your /boot that is not in the RAID (, formatted as most anything)? 

LVM2 used to require that, went away for a time from that... then went back to it. That way when Grub2 writes everything and has to read it again on boot, it "is simpler" for it.

---

### Post by #&amp;thj^% on 2024-03-31
> **MAFoElffen said:**
> Have you tried to create a separate partition for your /boot that is not in the RAID (, formatted as most anything)? 

LVM2 used to require that, went away for a time from that... then went back to it. That way when Grub2 writes everything and has to read it again on boot, it "is simpler" for it.

+1

The OP should include this if possible:
```
 sudo btrfs check /dev/sda
```

If the drive is already mounted then a "--force" flag will be needed.
Mine for example:
```
Opening filesystem to check...
WARNING: filesystem mounted, continuing because of --force
Checking filesystem on /dev/sda2
UUID: b332af46-6ad2-4652-baf9-4468ef7a7a75
[1/7] checking root items
[2/7] checking extents
[3/7] checking free space tree
[4/7] checking fs roots
[5/7] checking only csums items (without verifying data)
[6/7] checking root refs
[7/7] checking quota groups skipped (not enabled on this FS)
found 29022367744 bytes used, no error found
total csum bytes: 23133820
total tree bytes: 723058688
total fs tree bytes: 665075712
total extent tree bytes: 31064064
btree space waste bytes: 110854534
file data blocks allocated: 31732498432
 referenced 39947325440

```

Not to sound like I'm vetting you, but is all this really necessary?
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a device; this may
# be used with UUID= as a more robust way to name devices that works even if
# disks are added and removed. See fstab(5).
#
# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
UUID=EFE0-B154                            /boot/efi      vfat    defaults,noatime 0 2
UUID=b332af46-6ad2-4652-baf9-4468ef7a7a75 /              btrfs   subvol=/@,defaults,noatime,compress=zstd,space_cache=v2,commit=120 0 0
UUID=b332af46-6ad2-4652-baf9-4468ef7a7a75 /home          btrfs   subvol=/@home,defaults,noatime,compress=zstd,space_cache=v2,commit=120 0 0
UUID=b332af46-6ad2-4652-baf9-4468ef7a7a75 /root          btrfs   subvol=/@root,defaults,noatime,compress=zstd,space_cache=v2,commit=120 0 0
UUID=b332af46-6ad2-4652-baf9-4468ef7a7a75 /srv           btrfs   subvol=/@srv,defaults,noatime,compress=zstd,space_cache=v2,commit=120 0 0
UUID=b332af46-6ad2-4652-baf9-4468ef7a7a75 /var/cache     btrfs   subvol=/@cache,defaults,noatime,compress=zstd,space_cache=v2,commit=120 0 0
UUID=b332af46-6ad2-4652-baf9-4468ef7a7a75 /var/tmp       btrfs   subvol=/@tmp,defaults,noatime,compress=zstd,space_cache=v2,commit=120 0 0
UUID=b332af46-6ad2-4652-baf9-4468ef7a7a75 /var/log       btrfs   subvol=/@log,defaults,noatime,compress=zstd,space_cache=v2,commit=120 0 0
tmpfs                                     /tmp           tmpfs   defaults,noatime,mode=1777 0 0

```

BTW Here is a pretty nice guide for you read over: [https://www.baeldung.com/linux/btrfs-lvm](https://www.baeldung.com/linux/btrfs-lvm)

---

### Post by yuralamov on 2024-04-01
I do performance experiments. LVM+BTRFS works well with the installer ubuntu-desktop. There are no questions for it.
But with a clean BTRFS RAID0 I get the error. On Arch-linux, manual installation works well.
My fstab SSD(/)+SSD(/home)
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=bed103a4-cf83-452e-982d-bc722d18cca9 /               btrfs   defaults,subvol=@ 0       1
# /boot was on /dev/sda1 during installation
UUID=b6711e7f-6d56-40b0-b39c-35afe0de780f /boot           ext4    defaults        0       2
# /boot/efi was on /dev/sda2 during installation
UUID=7A62-0B17  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sdb1 during installation
UUID=9591af5d-765c-416b-afe7-016a510110a9 /home           btrfs   defaults,subvol=@home 0       2
#/swapfile                                 none            swap    sw              0       0
//192.168.0.7/Shared  /home/yura/Public  cifs  guest,rw,auto,iocharset=utf8,file_mode=0666,dir_mode=0777  0  0

```
swap commented because I forgot the section

---

### Post by MAFoElffen on 2024-04-02
Please start using CODE Tags for any command and/or output. I'm surprised a Moderator stepped in and warned you about that yet... Just trying to keep you out of troubles.

<<EDITED for format>>
> **yuralamov said:**
> You did not understand me. I'm trying to make software RAID0 on 2 HDDs identical drives WD 2T (/dev/sda & /dev/sdb).
1 I loading from live usb-key ubuntu-desktop (20.06 or 22.04.3 or 22.04.4)

2 launch the terminal.
```

sudo su -
fdisk /dev/sda
# g, n +512M, n +1536M, n remnant, w
fdisk /dev/sdb
# g, n +2G, n remnant, w

```

2 options for creating a raid0

2.a the first one works (BTRFS on LVM)
```

pvcreate /dev/sda3 /dev/sdb2
vgcreate vg01 /dev/sda3 /dev/sdb2
lvcreate -i2 -I64 -l 70%FREE -n lv_root vg01

```

2.b the second one should work, but doesn't
```

mkfs.btrfs -L bt_root -d raid0 -m raid0 -f /dev/sda3 /dev/sdb2

```
3 sudo & terminal exit and launch ubuntu install

/dev/sda1 - use as efi
/dev/sda2 - use as ext4, format, /boot
/dev/sdb1 - use as swap
and vg01-lv_root (2.a) or /dev/sda3 (2.b), not format, mount /
result:

2.a - Ok. The installation was successful, everything works

2.b - error at stage grub-install

Without leaving the living system:
the file system is creat and mounted in the directory /target
sections (/dev/sda3 and /dev/sdb2) are synchronized
====
my notes for myself github.com/yuralamov/ubuntu-tuning/blob/main/raid
Let me comment on 2-a and how these command differ from what you said you are using...
```

pvcreate /dev/sda3 /dev/sdb2
vgcreate vg01 /dev/sda3 /dev/sdb2
# This is the command format for creating LVM2 RAID
lvcreate --type raid0 -i 2 -l 70%FREE -n my_lv my_vg

```

Let's talk LVM volume types first: Linear, striped & mirrored...

The command you did was not formally LVM RAID0 (striped). It was a Linear, which means it aggregates space from one or more physical volumes into one logical volume. Yours just happened to be muliple PV extents into one Logical Volume. 

It expands the storage volume as if it were RAID0, tu the write scheduling is different. Just like LVM has Mirrored volumes, similar to RAID1, that are called Mirrored Volumes, that are also not RAIDS


So the Command I posted above is LVM RAID... Specifically RAID0. You did not do "RAID", but rather just an LVM Linear LV with multiple PV's...

"RAID" is what I thought you were referring to when you said "RAID0"...

Now let's look at 2.b.:
```

mkfs.btrfs -L bt_root -d raid0 -m raid0 -f /dev/sda3 /dev/sdb2
# that is real similar to one of my test cases:
mkfs.btrfs -L root -d raid10 -m raid10 -f /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1

```
That should have worked... I do it like that...

---

### Post by yuralamov on 2024-04-04
I know. This is a classic use of lvcreate. I conducted tests by feeding the partition to the windows virtual machine kvm as a disk. -i2 -I64 showed better than --type raid0. 64 is the best for my drives (WD 2T).

---

### Post by yuralamov on 2024-04-05
It's decided. The problem was with the BIOS keys, which prohibited installation. The second system on the computer is Windows 11, where device protection was enabled. Resetting the keys to default solved the problem.

---

### Post by #&amp;thj^% on 2024-04-05
=d> Good job

---

### Post by MAFoElffen on 2024-04-05
I have mentioned about your absence of using Codes Tags. Other Members have PM'ed me privately since then.

You need to go back and edit your posts here that contain commands and raw output and wrap it CODE Tags...

I have been told by other Members that they "refuse to answer you" until you do. I think you would get more active help if you formatted that differently.

---

### Post by #&amp;thj^% on 2024-04-05
> **mafoelffen said:**
> i have mentioned about your absence of using codes tags. Other members have pm'ed me privately since then.

You need to go back and edit your posts here that contain commands and raw output and wrap it code tags...

I have been told by other members that they "refuse to answer you" until you do. I think you would get more active help if you formatted that differently.
+1 :ks

EDIT: to help with that see "Code Tags" in my signature.

---

### Post by yuralamov on 2024-04-06
I checked it again step by step. Microsoft has nothing to do with it. The security key installs the fedora workstation 39 secure boot update. My apologies to Microsoft. Prejudice played a cruel joke.

---

### Post by MAFoElffen on 2024-04-06
> **yuralamov said:**
> I checked it again step by step. Microsoft has nothing to do with it. The security key installs the fedora workstation 39 secure boot update. My apologies to Microsoft. Prejudice played a cruel joke.
LMFAO!!! Yup. Microsoft deserves it even if this time it isn't them. They do enough other things. I do DEV testing for Win Insider & Win Server Insider... And Windows always has too much of an ego = It thinks it lives in a vacuum, without anything else present... So that anything it does affects 'nothing', because, without guilt, it is the only thing that matters in it's own life.

Wait... Isn't that the definition of a narcissistic psychopath? Why, yes it is:
> 
These individuals are often very destructive to the people around them. They are usually unable to feel empathy or guilt, and they have no problem manipulating others for their gain.

"Just the facts Mame..."

---


---
title: "Ubuntu server 10.04 + hardware raid 6"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by aznnico on 2011-06-28
Greetings everyone,

I am quite perplexed at this situation. I'm trying to install ubuntu-server 10.04 LTS 64-bit. Last week I set up a new server (intel cpu, supermicro mobo, 12 hdd raid 10 on LSI hardware raid) and it worked like magic.

Right now I'm doing a similar install (same hard drives, same raid card, same raid expander, but raid 6 this time). During the install, I choose:

 Guided - use entire disk and set up LVM
  SCSI1 (2,0,0) (sda) - 20.0TB LSI MR9260-8i
  
and then I get this error:

  Failed to create a file system. 
  The ext4 file system creation in partition #1 of LVM VG backup LV root failed.

Does anyone have a clue as to what I can do to solve this? A similar install just worked last week =P

Thanks everyone,
Howard

---

### Post by aznnico on 2011-06-28
Here is output from one virtual terminal (ctrl+alt+f4).

md-devices: mdadm: No arrays found in config file
partman: PV /dev/sda3 VG backup lvm2 [18.19 TiB / 0 free]
partman: Total: 1 [192.76 GiB] / in use: 1 [192.76.GiB] / in no VG: 0 [0  ]
partman: Reading all physical volumes. This may take a while...
partman: Found volume group "backup" using metadata type lvm2
partman-lvm: 2 logical volume(s) in volume group "backup" now active
partman-lvm: Logical volume "root" successfully removed
partman-lvm: Logical volume "swap_1" successfully removed
partman-lvm: 0 logical volume(s) in volume group "backup" now active
partman-lvm: Volume group "backup" successfully removed
partman-lvm: Labels on physical volume "/dev/sda3" successfully wiped
partman-lvm: Physical volume "/dev/sda3" successfully created
partman-lvm: Volume group "backup" successfully created
partman-lvm: Logical volume "root" created
partman-lvm: Logical volume "swap_1" created
kernel: [340.671158] Adding 23990264k swap on /dev/mapper/backup-swap_1. Priority:-1 extents: 1 across:23990264k
partman: mke2fs 1.41.11 (14-Mar-2010)
partman: mkfs.ext4: Size of device /dev/mapper/backup-root too big to be expressed in 32 bits
partman: using a blocksize of 4096.

---

### Post by aznnico on 2011-06-28
Does this have to do with the 32-bit/16TB limitation of e2fsprogs? Should I just use XFS?

---

### Post by aznnico on 2011-06-28
For anyone else that ran into this, there's a lot of talk about this already: [http://ubuntuforums.org/showthread.php?t=1287880](http://ubuntuforums.org/showthread.php?t=1287880)

Basically can't do >16TB on ext4 currently. Hope it saves someone some time.

---

### Post by tgalati4 on 2011-06-28
According to wikipedia's entry on ext4

You have hit a limitation of ext4:

Max volume size	1 EiB (limited to 16TiB because of e2fsprogs limitation)

Sounds like there are 32-bit libraries or programming limitations in mkfs.

XFS uses 64-bit addressing with some limitations, so that would be a choice, as well as ZFS which uses 128-bit addressing.

If you develop problems then you are on your own!  I would call this an edge case.

Update:  I have learned in another post that it has to with 32-bit address space for blocks in ext4 and it's not trivial to change.  64-bit addressing would give you an Exabyte maximum volume size, but for legacy reasons (I presume) there are some 32-bit limitations.

---

### Post by hunters1094 on 2011-07-14
Hi aznnico

I have a server with hardware raid that support raid 0 and raid 1. I want to install ubuntu server 10.04 on it, but i can not. Problem appears when partitioning the HDD. so, can you help me with this?

---


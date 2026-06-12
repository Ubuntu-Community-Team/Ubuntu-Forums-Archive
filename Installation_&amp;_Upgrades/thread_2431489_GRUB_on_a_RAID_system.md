---
title: "GRUB on a RAID system"
date: 2019-11-17
forum: Installation &amp; Upgrades
---

### Post by Elmi77 on 2019-11-17
Hi,

I have a server running which started with Ubuntu 10.08. Over the years it was updated to Ubuntu Bionic and was equipped with a RAID-system. This now causes some problems. To make it short: I have a separate boot partition with a size of 512 MBytes:

```
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system     Flags
 1      512B    512MB   512MB   primary  ext2            raid
 2      513MB   2560MB  2047MB  primary  linux-swap(v1)
 3      2560MB  610GB   608GB   primary  ext4            raid

```
Now when I try to install GRUB on /dev/sda, I get this error message:

```
Installing for i386-pc platform.
grub-install: warning: this msdos-style partition label has no post-MBR gap; embedding won't be possible.
grub-install: error: embedding is not possible, but this is required for RAID and LVM install.

```


So how can I solve this situation and install a valid, working GRUB?

My idea: generate a /boot-directory on /-partition, move everything out of the boot-partition to this directory, remove the boot-partition from /etc/fstab, remove the boot-partition via parted from the disk and then try installing GRUB again with grub-install /dev/sda

Could this work? Or are the chances good I end up with a non-working or non-bootable system?

The funny thing in this situations is, it is a remote server where I only have SSH-access...

Any help is welcome!

---

### Post by oldfred on 2019-11-17
Do not know RAID.

But old grub legacy did not need as large of an embedding area, the space after the MBR but before first partition. Since your RAID starts at 512 bytes, you left no space.

Also new 4k drives use even more space.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). 
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

And new UEFI systems use gpt which also has no space after gpt's protective MBR(just so old MBR tools see a gpt partition) and in BIOS mode require a bios_grub partition for BIOS boot or more often an ESP - efi system partition for UEFI boot.

It looks like you just have your Boot partition too close to start of drive?

---

### Post by Elmi77 on 2019-11-18
> **oldfred said:**
> It looks like you just have your Boot partition too close to start of drive?

This is exactly the problem I described in my post. Now the question is: how can I fix this without completely repartitioning/reinstalling the whole server?

---

### Post by rsteinmetz70112 on 2019-11-18
You can shrink the partition or relocate it if there is sufficient space available.  Best to have a good backup or three before attempting.
Removing the swap partition then relocating the first partition and either creating a swap file or using whatever is left for swap should do the trick.
This should probably be done from a live session.

---


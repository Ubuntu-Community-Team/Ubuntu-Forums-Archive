---
title: "LVM2: resize physical volume"
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by fela on 2011-04-11
I have a 500GB hard disk, /dev/sda. On it, there is /dev/sda1 for /boot, /dev/sda2 for an LVM PV (physical volume), and /dev/sda3 for another /boot (multiple Linux distros, one boot partition for grub legacy, another for grub2).

OK, so the LVM2 partition, /dev/sda2, is taking up ~465GiB. I want to add another OS (non-Linux), so I resized the *lvm2 physical volume* to 320GiB, successfully, using pvresize.

However, I now need to resize the partition so the lvm2 physical volume only just fits on it, ie to 320GiB. My plan of action is to use gparted (the partition table is GUID, so fdisk won't work), to first delete the partition from the partition table, then re-add it but this time with a smaller value (~320GiB).

The problem is that I need to know exactly how many MiB/cylinders the physical volume is taking up. So, I run:

```
root@sysresccd /root % pvdisplay
  --- Physical volume ---
  PV Name               /dev/sda2
  VG Name               vg0
  PV Size               320.00 GiB / not usable 3.81 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              81919
  Free PE               13003
  Allocated PE          68916
  PV UUID               WIdBTw-Ufqj-8CKz-n5Fo-53fs-FPph-jTKhtH
   
root@sysresccd /root % 

```

**What one of these values do I need to set the new lvm2 replacement partition to?**

Thanks very much

---

### Post by fela on 2011-04-12
OK, I managed to do it in the end, after much hard work and frustration ;)

Basically, all I had to do in theory was delete the LVM partition from the partition table, and recreate it at a smaller size (I made it exactly 321GiB). However, what I had to do first was fix the order of the partitions using fdisk, then fix the first two boot partitions (sda2, sda1) so they fitted on the cylinder boundaries (I used gparted to do this). Then, I deleted and recreated the LVM2 partition using fdisk+cfdisk and it all worked out fine :lolflag:

---

### Post by srs5694 on 2011-04-12
> **fela said:**
> what I had to do first was fix the order of the partitions using fdisk, then fix the first two boot partitions (sda2, sda1) so they fitted on the cylinder boundaries (I used gparted to do this).

Be aware that those "fixes," and particularly the cylinder boundary "fix," were not fixes at all. In fact, it's possible that you degraded performance a bit -- but if it's just for the /boot partition, you didn't do enough damage to make it worth the effort and risk of undoing the damage.

The partition-order issue is a non-issue as far as the computer is concerned, but if you like having your partition numbers match the order on disk, that's fine -- and it can sometimes head off confusion.

The concept of a disk cylinder is real, but the "cylinder" values reported by disk drives have been fictions invented by the drives' firmware for well over a decade. Thus, aligning partitions to cylinder boundaries is pointless at best. At worst, if you've got a recent Advanced Format drive (such as many models introduced by Western Digital in 2010 and 2011), your performance will be degraded, as described in [this article I wrote for IBM developerWorks.](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) If you don't have an Advanced Format drive, then shifting your partitions did no harm, but was risky -- any time you muck with partitions there's risk involved, and moving a partition's start point is particularly risky. If you *do* have an Advanced Format drive, then there will be so little degradation from a misaligned /boot partition that it's not worth fixing. (Note that the problem is almost nonexistent for disk reads and biggest for writes of small files, which you do very rarely on a /boot partition.) If you've got such a drive, though, you should check the sector start value of your LVM partition; if that's misaligned, you could have some serious performance issues with your hard disk.

---

### Post by fela on 2011-04-12
Hi srs5694, thanks for that.

The drive is a 500GB seagate, from late 2008/early 2009, so I doubt it's an 'advanced format' drive (not that I know what that is ;)). Also, just to be clear, the PC in question isn't vital for anything, it's just my desktop PC, and I haven't noticed any performance losses since 'fixing' the partitions. About changing partition start sectors, well I actually didn't change the start of the LVM2 partition. There's a small gap in between it and the end of sda2 (I was thinking of sticking some small distro in there for laughs, but it would have to be less than a few megabytes in size :)).

Naturally, all the data was backed up to my server before doing this, including the MBR (boot sector + partition table), the reason I was doing this was because it would have been a huge palava to reformat the drive and reinstall all the different Linux distros I have on it (including Gentoo :o).

---
Oh yeah, I forgot, I hardly ever write to the hard disk, the only reason it's so big is cause I had it lying around (used to be in the server before I upgraded that to 2TB). Almost all my data is stored on the network.

---

### Post by srs5694 on 2011-04-12
The first Advanced Format disks were released by Western Digital in very late 2009 (December, IIRC), and I've only recently heard of Seagate drives that use this technology, so you're safe -- for *this* drive. Unfortunately, this issue will become more of a problem, because Advanced Format seems to be the way the industry is going, and Linux partitioning tools were slow to make the necessary changes.

Advanced Format, BTW, is just drives with physical sectors that store 4096 bytes of data but report these as being eight 512-byte sectors. Most disks until now have had 512-byte physical sectors, and assumptions about sector size exist all through the software stack that deals with disks, which is why the drives do that "translation." This has a negative speed consequence, though: Many filesystem data structures happen to be 4096 bytes in size, and everything in most filesystems is laid out in 4096-byte multiples. If these structures happen to align properly with the disk's physical sector layout, then writing such a data structure involves a single write operation. If not, the data that the OS writes straddles two sectors. The drive's firmware must then read both sectors, modify both of them, and write them both back. That's a lot more work, and the drive has to wait for the heads to spin around to write everything back, so write operations are badly degraded. See the article I wrote (and referenced in my earlier post) for the details, but some operations can be 25 times slower on an improperly-aligned partition than on a properly-aligned partition. That's a *huge* degradation!

---

### Post by fela on 2011-04-12
I read your article, it seems like ReiserFS would be the worst off if that was the case - I've never actually used that as it happens.

Also, I wouldn't be surprised if the version of GParted I was using wasn't aware of advanced format drives - it was on a copy of system rescue CD I had lying around from at least a couple of years ago (I was surprised the CD still worked!).

Maybe it would have caused less confusion if they'd not bothered with backwards compatibility, and forced software to account for 4K block sizes? -EDIT-- a bit like the internet being forced to transition to IPv6....I'm excited to see what ISPs will do when that happens!--

Or, if they were feeling especially nice, code the HDD firmware to automatically fix cylinder alignment ;) (how hard could that be?)

---

### Post by srs5694 on 2011-04-13
> **fela said:**
> Also, I wouldn't be surprised if the version of GParted I was using wasn't aware of advanced format drives - it was on a copy of system rescue CD I had lying around from at least a couple of years ago (I was surprised the CD still worked!).

Until a few months ago (perhaps a bit over a year), GParted created partitions on "cylinder" alignment by default.

> Maybe it would have caused less confusion if they'd not bothered with backwards compatibility, and forced software to account for 4K block sizes? -EDIT-- a bit like the internet being forced to transition to IPv6....I'm excited to see what ISPs will do when that happens!--

This would have resulted in less confusion, but huge numbers of returns. I don't know the details at every level of the software stack, but I understand that many BIOSes can't handle drives with 4KiB sectors. Likewise for many OSes, boot loaders, and disk utilities. Until recently, even libparted (and therefore GParted, GNU Parted, etc.) couldn't handle such disks. I can't blame the drive manufacturers for trying to make their drives backward-compatible.

Moving forward, they may eliminate the sector size fakery, since the software issues are being addressed. For now, though, there's far too much legacy software to release drives with 4KiB physical and logical sectors, at least as internal disks. (External drives don't need BIOS compatibility, and often don't need boot loader compatibility, so that eliminates a couple of big sources of problems.)

> Or, if they were feeling especially nice, code the HDD firmware to automatically fix cylinder alignment ;) (how hard could that be?)

Much harder than you think. The drive firmware knows nothing about partitions; it just knows when particular sectors are being read and written. Suppose for the sake of argument that you as a user do a low-level dd copy of a disk from an old disk with 512-byte sectors to a new Advanced Format disk. Your old disk has partitions that begin at sectors 63, 192,780, and 1,012,095. Those values are 1 less than, 4 less than, and 1 less than, respectively, 8-sector boundaries. (I took these values from an actual MBR disk I've got.) The only way to get all three partitions to align would be to have the firmware analyze the data as they're being written to the disk to locate partition table data, record for its own future reference where partitions begin and end, and adjust sector values differently for each partition. What's more, the firmware would have to be able to ignore obsolete partition data (which might be leftover in currently-unallocated sectors), understand multiple partition table types (MBR, GPT, APM, BSD disklabels, and other more obscure types), and adjust things on the fly if and when users resize partitions. That's a *huge* order, and a bug in the firmware code that would handle all this would result in data loss and irate customers, who might decide to sue. I can't blame them for not attempting such a solution.

---

### Post by fela on 2011-04-13
Hmm...too bad the world runs on whether or not things are marketable ;)

(cause if not they wouldn't have worried about recalls, and forgot about 512B cylinders)

Although, I think the main issue here is that disks should always have been designed with 4KB cylinders. Or at least, transitioned in the 90s.

---


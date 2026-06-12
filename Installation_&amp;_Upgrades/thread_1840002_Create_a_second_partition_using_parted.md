---
title: "Create a second partition using parted"
date: 2011-09-06
forum: Installation &amp; Upgrades
---

### Post by Somelauw on 2011-09-06
My disk contains 932GiB or 1 TB of filespace.
It contains 1 vfat partition over the complete disk.
I want to half this vfat partition and create a new ext4 partition
I do want to preserve all data that is stored on the vfat partition.

I read a tutorial about how parted should be used and based on the information supplied, I think these are the commands I should execute:

```
parted /dev/sdb
(parted) resize 1 0 499.9
(parted) makepartfs primary ext4 500 999.9
(parted) quit
```Would this work?

---

### Post by YesWeCan on 2011-09-06
Hi there.
What did you use to create the vfat partition in the first place? If it was Windows and you can still use Windows, I'd use its Disk manager to shrink the partition. It's prudent to use Windows tools for Windows partitions.

Otherwise, is there a reason you don't use the GUI version GParted? If it were me I think I'd be less likely to make a mistake using GParted.

---

### Post by haqking on 2011-09-06
> **YesWeCan said:**
> Hi there.
What did you use to create the vfat partition in the first place? If it was Windows and you can still use Windows, I'd use its Disk manager to shrink the partition. It's prudent to use Windows tools for Windows partitions.

Otherwise, is there a reason you don't use the GUI version GParted? If it were me I think I'd be less likely to make a mistake using GParted.

+1

I know Gparted supports ext4 abut wasnt sure if parted did.

and does gparted support vfat ? I suppose it should in theory, just wasnt sure

[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)

---

### Post by Somelauw on 2011-09-06
> **YesWeCan said:**
> Hi there.
What did you use to create the vfat partition in the first place?
It was already formatted when I bought it.

> Otherwise, is there a reason you don't use the GUI version GParted? If it were me I think I'd be less likely to make a mistake using GParted.
Great, then I'll use the gui version to create the ext4 partition.

---

### Post by YesWeCan on 2011-09-06
> **haqking said:**
> +1

I know Gparted supports ext4 abut wasnt sure if parted did.

and does gparted support vfat ? I suppose it should in theory, just wasnt sure

[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)
I'm not sure either. I'm not sure I know what the difference is between VFAT and FAT and FAT32.

---

### Post by haqking on 2011-09-06
> **YesWeCan said:**
> I'm not sure either. I'm not sure I know what the difference is between VFAT and FAT and FAT32.

VFAT was just a name given to an extension which supported LFN as far as i remember, going back a bit.  WFW time period.

FAT is 16bit and FAT32 is 32 bit so supports larger hard drives etc amongst other features

---

### Post by YesWeCan on 2011-09-06
I guess the question is will GParted trash the data on a vfat partition if it is asked to shrink it? :-s

I have no idea. But this is why I recommend shrinking it with Windows.

---

### Post by srs5694 on 2011-09-07
> **haqking said:**
> [quote=YesWeCan]I'm not sure either. I'm not sure I know what the difference is between VFAT and FAT and FAT32.VFAT was just a name given to an extension which supported LFN as far as i remember, going back a bit.  WFW time period.

FAT is 16bit and FAT32 is 32 bit so supports larger hard drives etc amongst other features[/QUOTE]

This is basically correct, although VFAT was introduced with Windows 95, not Windows for Workgroups (WfW). I seem to recall there were some third-party add-ons to provide long filename support in WfW, though. In any event, there are two orthogonal variants of FAT:


[list]
[*]FAT size -- 12-bit, 16-bit, or 32-bit
[*]Filename support -- The original 8.3 filenames of DOS or the long filenames of Windows 95 and later
[/list]


In Linux, FAT size is determined automatically so you don't need to be concerned with it, for the most part. Long filenames are supported by the vfat kernel driver, whereas the msdos kernel driver supports only 8.3 filenames. Ubuntu uses the vfat driver to mount FAT partitions. Note that long filename support was designed in such a way that it's forward and backward compatible, so you can use a disk with DOS, Windows 95, Linux (using vfat and/or msdos filesystem drivers), and so on, and every OS will be able to access files stored by any other OS -- even 8.3-only OSes can read files stored with long filenames, although the 8.3-only OS will see a shorter version of the filename. VFAT long filenames are a bit of a hack, but they work remarkably well. Most utilities don't know or care if a disk uses short or long filenames because that difference is recorded on a file-by-file basis.

[quote=YesWeCan]I guess the question is will GParted trash the data on a vfat partition if it is asked to shrink it? :-s

I have no idea. But this is why I recommend shrinking it with Windows.[/quote]

AFAIK, GParted's FAT support is pretty robust. Certainly I've used it in the past to resize FAT partitions with no problems that I recall, although I've not used it much lately.

FWIW, the filesystem-handling code has been removed from libparted and parted, as of version 3.0. Ubuntu 11.04 still uses parted 2.3, so it still supports some filesystem operations, but they'll disappear in the future. (I don't know what version Ubuntu 11.10 will use.) GParted has its own way of adding filesystem support, so I don't believe it will be affected by these libparted changes.

---

### Post by ottosykora on 2011-09-08
I can confirm that if Gparted will do something right, it is manipulation on VFAT (=fat32) or other fat (fat16 etc).
Using it for years and never had any failures that way.
It does also manipulate ntfs fine, however here only one operation should be done at a time and not ask the gparted to do other ops in same go.

After partition magic was not updated to be able to work on bigger drives and crashed on drives created with vista partitioning, I started use gparted and found only it failed on some drives formated in some old sector/cylinder way.

---


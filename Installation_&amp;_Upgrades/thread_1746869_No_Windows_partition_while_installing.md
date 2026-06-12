---
title: "No Windows partition while installing"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by Xythus on 2011-05-02
Hello, (I can't think of a better introduction, how lame.)
I've been using Ubuntu since 2009, but recently I had to reinstall Windows (and Ubuntu.)
The problem is that ever since I reinstalled Windows the Ubuntu installation doesn't recognize the Windows partition. I've got a 500GB HDD, and the installation says there's 500GB of free space.

Is there any way to make Ubuntu recognize the Windows partition while installing, or is the only solution reinstalling Windows?

Thank you for your time,
Django

---

### Post by srs5694 on 2011-05-02
Your partition table is probably damaged. See [this page](http://www.rodsbooks.com/missing-parts/index.html) for general information and several possible solutions. The simplest solution is probably to use [FixParts](http://www.rodsbooks.com/fixparts/) on the disk. If you want a more precise diagnosis, launch the Ubuntu installer into "live CD" mode, open a Terminal window, and type "sudo fdisk -lu". Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags. That will tell me (and others knowledgeable about such things) what the precise problem is and what sorts of corrective measures are easiest.

---

### Post by Xythus on 2011-05-03
```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x88f11eea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *      206848   767055871   383424512    7  HPFS/NTFS

```

That's the message I get, and when I try to use "parted /dev/sda print" this message shows up:
```

Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?

```

I will try to look up some information and fix it myself, but I'm pretty scared of trying things out since I don't have any backups of my Windows installation, and I don't have any dvds laying around to backup important files. Any help would be greatly appreciated!

Kind regards,
Django

---

### Post by Mark Phelps on 2011-05-03
From what you posted, it looks like the only partitions on your drive are NTFS -- and the Ubuntu installer won't install to those.

Also, I don't think the installer recognizes GPT disks; I think it needs MBR disks.

But ... I've not installed 11.04 (Don't like Unity), so I could be wrong on this.

---

### Post by srs5694 on 2011-05-03
Is Ubuntu installed on the disk, or have you just left free space for Ubuntu after the Windows installation? If the former, you've got a more complex problem; but I suspect the latter, in which case it's relatively simple: The disk was used as a GUID Partition Table (GPT) disk at some point (in a Mac, a Hackintosh installation, or using GPT under Linux or some other OS), then re-used as a simple Master Boot Record (MBR) disk by a utility that doesn't understand GPT and therefore didn't wipe the GPT data. That's left a legal MBR disk, but with leftover GPT data that's confusing libparted-based tools, such as those used by the Ubuntu installer.

The solution is simple: Run [FixParts](http://www.rodsbooks.com/fixparts/) on the disk. It will detect the GPT data and offer to destroy it. Tell it to do so, then type "q" to exit the program. The problem will be fixed. *Do not*, however, do this if you think you've got more than those two NTFS partitions on the disk! In that case, it could be that *you* think your GPT partitions are valid (even if you don't know what "GPT" means), so destroying the GPT data would be a mistake.

As described on the FixParts Web page, backing up your data beforehand is always wise. You can back up just the MBR as described on the FixParts page, and that should be sufficient insurance *if* those two partitions are the only valid ones on the disk. (The main reason I keep harping on this point is that you've both said that you've re-installed Windows and that you've got valuable data on the disk, which suggests there might be another partition somewhere.)

---

### Post by srs5694 on 2011-05-03
> **Mark Phelps said:**
> Also, I don't think the installer recognizes GPT disks; I think it needs MBR disks.

No, the Ubuntu installer will install quite well to GPT disks. The problem is, as I wrote, a mixture of MBR and GPT data that's confusing the installer. (This configuration is technically a valid MBR setup, since the GPT specification is quite explicit about this point. No doubt libparted is doing "extra" checks that it either should not be doing or should be handling properly rather than flaking out when they produce ambiguous results.)

---

### Post by Xythus on 2011-05-03
> **srs5694 said:**
> Is Ubuntu installed on the disk, or have you just left free space for Ubuntu after the Windows installation? If the former, you've got a more complex problem; but I suspect the latter, in which case it's relatively simple: The disk was used as a GUID Partition Table (GPT) disk at some point (in a Mac, a Hackintosh installation, or using GPT under Linux or some other OS), then re-used as a simple Master Boot Record (MBR) disk by a utility that doesn't understand GPT and therefore didn't wipe the GPT data. That's left a legal MBR disk, but with leftover GPT data that's confusing libparted-based tools, such as those used by the Ubuntu installer.

The solution is simple: Run [FixParts]("http://www.rodsbooks.com/fixparts/") on the disk. It will detect the GPT data and offer to destroy it. Tell it to do so, then type "q" to exit the program. The problem will be fixed. *Do not*, however, do this if you think you've got more than those two NTFS partitions on the disk! In that case, it could be that *you* think your GPT partitions are valid (even if you don't know what "GPT" means), so destroying the GPT data would be a mistake.

As described on the FixParts Web page, backing up your data beforehand is always wise. You can back up just the MBR as described on the FixParts page, and that should be sufficient insurance *if* those two partitions are the only valid ones on the disk. (The main reason I keep harping on this point is that you've both said that you've re-installed Windows and that you've got valuable data on the disk, which suggests there might be another partition somewhere.)

Thank you, that fixed it!

---


---
title: "what do you use for GPT partitions?"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2011-09-24
with interest I am reading posts about all that new UEFI system.
Have from work one notebook which apparently allows it to switch bios to uefi if wanted.
So I thought I might try one day...

but how do you create all those partitions needed for that?

In past I was using all sorts of partition tools, now mostly gparted on parted magic disk.

But how is it done with those new partitions?

---

### Post by dino99 on 2011-09-24
[http://johnlewis.ie/converting-to-gpt-in-ubuntu/](http://johnlewis.ie/converting-to-gpt-in-ubuntu/)

[http://manpages.ubuntu.com/manpages/natty/man8/gdisk.8.html](http://manpages.ubuntu.com/manpages/natty/man8/gdisk.8.html)

---

### Post by srs5694 on 2011-09-24
All libparted-based tools (parted, GParted, Palimpsest Disk Utility, the Ubuntu installer, etc.) support GPT. Depending on the tool, you may need to explicitly tell it to create a fresh partition table as GPT rather than as MBR.

My own [GPT fdisk (gdisk, cgdisk, and sgdisk)](http://www.rodsbooks.com/gdisk/) family is intended to work more-or-less like the Linux fdisk (fdisk, cfdisk, and sfdisk) family, although there are unavoidable differences and sgdisk really bears little resemblance to sfdisk. Still, if you prefer fdisk to libparted-based tools, gdisk is the way to go. If you prefer GParted or some other libparted-based tool, keep using it for GPT.

If you're installing in UEFI mode to a completely blank disk (no partition table at all), the installer should default to using GPT, so you shouldn't have to worry about it. I'm not sure offhand how the Ubuntu installer reacts to a disk with an MBR partition table but not defined partitions, so if you attempt a fresh install like this, either create some GPT partitions ahead of time or completely wipe the partition table -- say, by doing "sudo dd if=/dev/zero of=/dev/sda bs=512 count=1". Be *very careful* with that command, though, at least if you've got another disk whose data you want to preserve!

UEFI uses a partition known as the [EFI System Partition (ESP)](http://en.wikipedia.org/wiki/EFI_System_partition) to hold boot loaders and other data for the firmware. Ubuntu's installer tends to create a small (sub-100 MiB) ESP, but some Linux boot loaders work best with a significantly larger ESP. I recommend creating one in the 200-300 MiB range. In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should *not* set the "boot flag" on any OS partition under GPT!

---

### Post by ottosykora on 2011-09-24
>All libparted-based tools (parted, GParted, Palimpsest Disk Utility, the Ubuntu installer, etc.) support GPT. Depending on the tool, you may need to explicitly tell it to create a fresh partition table as GPT rather than as MBR.<

hmm, this was the new part for me...

I did so far create all partitions before any installation, exemption was when I got some machine with preinstalled windows etc, then I redo it with some partitioning tool, in recent years I used mostly gparted or acronis disk director.

But now I will have to see how one goes to make gpt partitions with gparted, I have so far not seen there any setting or so for that.

If I create on a fresh disk gpt partitions (if the gparted really allows me to do so) can I then restore there image made from a partition on an mbr system? 
To me this seems unlikely to work, but can you tell me this for sure?

---

### Post by srs5694 on 2011-09-24
> **ottosykora said:**
> But now I will have to see how one goes to make gpt partitions with gparted, I have so far not seen there any setting or so for that.

Select Device -> Create Partition Table. A dialog box should open. Click to expand the Advanced item. You can now set the partition table type. It defaults to "msdos" (what libparted calls MBR). Change it to "gpt" to create GPT rather than MBR.

> If I create on a fresh disk gpt partitions (if the gparted really allows me to do so) can I then restore there image made from a partition on an mbr system? 
To me this seems unlikely to work, but can you tell me this for sure?

It depends on what the image was. If it was a tarball or a filesystem image, then yes, a restore will work fine. If it's a dd dump of an entire hard disk, then it will take some extra work, since you'll need to extract only the filesystem data for the filesystem(s) you want to restore, without the MBR data. In such a case, it would be simpler to restore the MBR image in its entirety and then convert from MBR to GPT form using [GPT fdisk (gdisk).](http://www.rodsbooks.com/gdisk/) If you need more advice on this issue, please post more details.

---

### Post by ottosykora on 2011-09-24
well will see...

I thought I could just practice little bit with this new thing.

I have images of all partitions on the drive, separate image of every partition. Images done by acronis true image mostly, some by driveimage xxl.
They are on external usb drives.

I thought, I could take new disk, fresh, nothing on it, partition it to the suitable system for this gpt and then try to restore the partitions from those images to it.

I have here w7 original install, with the 300mb 'system' partition and the real w7 partition, then xp also on a primary and then some data partitions on extended and ubuntu partitions (home and root) also in extended.

Well the xp will probably not like it, but do you think it is possible just to create the partitioning and then restore the partitions in question , w7 'system'(ntfs), w7(nzfs), data(nzfs), share(vfat), home(ext3), ubuntu(ext3).

if this acronis can read those partitions for knowing where to restore it ofcourse.
(I dont know this yet, it has some linux boot media)



On the other hand:
I could just make an identical clone of the current disk and then try to convert it...well xp will not like it probably.
Dou you think this would really work?

---

### Post by srs5694 on 2011-09-24
I can't speak to either of the programs you're using, but in general, a restore of a partition should work fine if the software supports the target partition table type.

That said, the restoration of a *bootable OS image* might not work, in the sense that the OS might not be bootable. Linux is much more likely to work (after a bit of tweaking) than Windows, since Microsoft has chosen to wed its partition table type to the computer's firmware type: If you use BIOS firmware, Windows will only boot from an MBR disk; and if you use UEFI firmware, Windows will only boot from a GPT disk.

---

### Post by ottosykora on 2011-09-25
AHA
>If you use BIOS firmware, Windows will only boot from an MBR disk; and if you use UEFI firmware, Windows will only boot from a GPT disk.<

means for my logic that only fresh windows install is then possible, while linux can be somehow persuaded to do it.

OK, will  think about it, obtain suitable hard drive and see what can be done.

---


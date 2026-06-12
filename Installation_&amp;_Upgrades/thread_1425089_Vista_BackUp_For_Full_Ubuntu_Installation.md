---
title: "Vista BackUp For Full Ubuntu Installation"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by kliffs on 2010-03-08
I currently have windows vista installed on my Acer Aspire 5220 laptop. I would like to remove vista from my computer and use only ubuntu  because i can't think of a reason to keep it. However if there is a something that needs vista i would like to be able to have it in an emergency. Is there a way to back up vista or reinstall it. There is a 9 GB unknown partition on my computer, could that be a recovery partition. Any thoughts,

Thanks

---

### Post by bumanie on 2010-03-08
The 9gb partition is most likely a recovery partition. I think they are normally formatted to fat32 rather than ntfs - but that may not be standard for all manufacturers. Just make sure you don't overwrite that partition, alternatively, you could image the partition and store it somewhere else if you have the space on another hard drive to store the image.

---

### Post by RHTopics on 2010-03-08
kliffs,

Just to confirm you do not want to dual boot both Vista and Ubuntu.  Instead you want to allow an Ubuntu installation to take the whole drive.  But you want the option of restoring the computer back to Vista.

bumanie gave you good advice on making an image copy of the Vista ntfs partition which you could use to restore from in the future if the need arose.

I am in similar circumstance, except that I am dual booting Ubuntu and Vista.  I decided to keep the Vista installation so that if a need came up for it, it would be available.  It is a little more hassle keeping both up-to-date, but that way I know Vista is ready and protected from viruses and malware.  But I still wanted a way to make a full backup of the Vista installation.

I found a good free application for making image copies of a Vista installation.  It is Macrium Reflect Free.  Here is a link to cnet which describes the application and provides the option to download it:

    [http://download.cnet.com/Macrium-Reflect-Free/3000-2242_4-10845728.html](http://download.cnet.com/Macrium-Reflect-Free/3000-2242_4-10845728.html)

---

### Post by adam814 on 2010-03-08
For me the simplest solution if you have enough disk space somewhere to do it is to clone the partition using dd.  It's not much more of a hassle to pipe the output through gzip to compress away the free space (i.e. even though your Vista partition is 100GB if you've only used 10GB that's all you need to store it).

There are definitely more elaborate schemes for doing what you need, but for me that's the fastest and simplest way to get a partition (or whole device for that matter) back the way it was.

A graphical alternative to do this would be CloneZilla.

---

### Post by coffeecat on 2010-03-08
If that 9GB partition is a recovery partition, it will restore Vista for you, but to the factory settings. That is, you will lose any installed apps, updates and personal settings.

If you want to make a ghost or image of Vista as it is now, I can recommend a proprietary but free piece of Windows software:

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

It's a lot simpler to use than clonezilla. You do the imaging from inside Windows - doing the backup to an external drive or another partition. You also use Macrium Reflect to make a bootable restore CD (which is actually Linux-based! :)). If you need to restore Vista from a Macrium image, you do it from the CD.

---

### Post by srs5694 on 2010-03-08
Personally, this is what I'd do:


[list=1]
[*]Install the ntfsprogs package in Ubuntu, if Ubuntu is already installed on the system. If not, download [PartedMagic](http://partedmagic.com/) and/or [SystemRescueCd.](http://www.sysresccd.org/Main_Page) At least one of them (I think both) provides the NTFS tools needed later.
[*]If your laptop manufacturer was cheap enough to omit a Windows install disc, locate the Windows utility to create a recovery/install DVD and run it. Twice. (DVD-Rs aren't generally as reliable as pressed DVDs.)
[*]Resize your main Windows partition to a much smaller size, but still with enough free space to be useful -- say 50% used. The ntfsresize tool from ntfsprogs will do this. Resizing is necessary because the backup I describe below can only be restored to a same-size or larger partition, so if you pre-shrink your Windows partition, you'll have more flexibility about how to restore it.
[*]Test that Windows still boots. If you didn't move the start point of the filesystem in the previous step, it should. If not, use the Windows install disc to repair it.
[*]Use ntfsclone (also part of ntfsprogs) to back up the resized Windows partition.
[*]Most pre-installed Windows systems include a partition of type 0x27 that's important for Windows, so back it up, too. The 9GB partition you mention may be this one, or it could be a partition with the OS install/recovery tools that you burned to DVD in step #2, so you shouldn't need to back it up in the latter case.
[*]Use your favorite partitioning tool to record the *exact* start and end points of the Windows partitions. By "*exact*" I mean sector-exact. You can use sfdisk for this: "sfdisk -d /dev/sda > backup.txt".
[*]Store all these backups, including the sector-exact partitioning data, on a DVD or some other backup medium. You may need to split it across multiple DVDs.
[*]Repartition the disk for Linux. If possible, re-use the existing Windows partitions in a way that enables you to easily stop using them. For instance, they could be partitions in an LVM array that also includes at least one other partition, or you could use them for temporary files or even /home, if you've got good backup facilities. That way, should you need to restore Windows, you'll be able to do so using its original partitions.
[*]If you need to restore Windows, recreate its partitions exactly. The starting sectors, in particular, must match, and the new partitions must be at least as big as the originals.
[/list]


Another approach is to use a Windows-native backup tool. One I've been experimenting with of late is called [DriveImage XML.](http://www.runtime.org/driveimage-xml.htm) This allows restoration to a location other than the original one, but you'll be left having to create a Windows emergency boot disc, which is a much harder thing to do than just downloading one of the many Linux emergency discs that are available.

---

### Post by srs5694 on 2010-03-08
> **coffeecat said:**
> If you want to make a ghost or image of Vista as it is now, I can recommend a proprietary but free piece of Windows software:

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

It's a lot simpler to use than clonezilla. You do the imaging from inside Windows - doing the backup to an external drive or another partition. You also use Macrium Reflect to make a bootable restore CD (which is actually Linux-based! :)). If you need to restore Vista from a Macrium image, you do it from the CD.

Do you happen to know if the images can be restored to another location and remain bootable? That's the big drawback to ntfsbackup, in my experience -- they boot fine if restored to their original locations, but not if you change their locations. If Reflect backups work after restoring to another location, then the presence of a Linux-based restore CD makes this sound very useful.

---

### Post by coffeecat on 2010-03-08
> **srs5694 said:**
> Use ntfsclone (also part of ntfsprogs) to back up the resized Windows partition.

Cautionary note (from man ntfsclone):

> Windows Cloning
       If you want to copy, move or restore a  system  or  boot  partition  to
       another computer, or to a different disk or partition (e.g. hda1->hda2,
       hda1->hdb1 or to a different disk sector offset) then you will need  to
       take extra care.

       [B]Usually,  Windows  will  not  be able to boot, unless you copy, move or
       restore NTFS to the same partition which starts at the same  sector  on
       the  same  type of disk having the same BIOS legacy cylinder setting as
       the original partition and disk had.[/B]

       The ntfsclone utility guarantees to make an exact copy of NTFS  but  it
       won't  deal  with  booting  issues.  [B]This  is by design: ntfsclone is a
       filesystem, not system utility. Its aim is only NTFS cloning, not  Win&#8208;
       dows  cloning.[/B] Hereby ntfsclone can be used as a very fast and reliable
       build block for Windows clonning but itself it's not  enough.  You  can
       find useful tips following the related links on the below page
       [http://wiki.linux-ntfs.org/doku.php?id=ntfsclone](http://wiki.linux-ntfs.org/doku.php?id=ntfsclone)I've emboldened some important bits.

---

### Post by lisati on 2010-03-08
My laptop came with Vista preinstalled. Included was software which lets me make a backup of the recovery partition on to a set of bootable CDs or DVDs.

---

### Post by coffeecat on 2010-03-08
> **srs5694 said:**
> Do you happen to know if the images can be restored to another location and remain bootable? 

I've managed to restore an image to a different hard disk successfully, but as a replacement disk for the original. I've never tried to restore a Windows system that was originally on partition #1 (say) to partition #2. I don't think this is possible without some editing of the Windows bootloader. When I tried moving a Windows partition from sda2 to sda1 using Acronis a few years ago, it failed to produce a bootable copy, so maybe Macrium will too. I don't know enough about the Windows booting process to understand what's going on.

One limitation of Macrium (not shared by Acronis iirc) is that you cannot restore to a partition smaller than the original even if there is plenty of room. For example, say you have an original C: partition of 100GB with only 25GB used, you can't restore the image to a 60GB partition.

---

### Post by Mark Phelps on 2010-03-09
> **srs5694 said:**
> 
If your laptop manufacturer was cheap enough to omit a Windows install disc, locate the Windows utility to create a recovery/install DVD and run it. Twice. (DVD-Rs aren't generally as reliable as pressed DVDs.)
Unlike in Win7, only SOME Vista versions have this feature. So, don't be surprised if your version does not have this feature.

> Resize your main Windows partition to a much smaller size, but still with enough free space to be useful -- say 50% used. The ntfsresize tool from ntfsprogs will do this. Resizing is necessary because the backup I describe below can only be restored to a same-size or larger partition, so if you pre-shrink your Windows partition, you'll have more flexibility about how to restore it.

Test that Windows still boots. If you didn't move the start point of the filesystem in the previous step, it should. If not, use the Windows install disc to repair it.
Preinstalled Vista systems nearly always do NOT come with a Windows install disk.  So, doing this runs the risk of corrupting the Vista OS, rendering it unbootable -- with no way then of repairing it.

Plus, CDs/DVDs provided with preinstalled systems, and utilities provided with the same, generally only provide the capability to restore the initial install from scratch -- wiping out all files and data in the process.

---


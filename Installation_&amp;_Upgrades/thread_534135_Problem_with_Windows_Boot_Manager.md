---
title: "Problem with Windows Boot Manager"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by StreetProphet on 2007-08-24
I just tried to install Feisty Fawn and the install went just fine.  Until I tried to boot into Ubuntu.

I had formatted my hard drive that had a previous Vista install on it.  However, whenever I boot up I'm welcomed with a message from Windows Boot Manager telling me that \windows\system32\winload.exe is missing.  This makes it so I can't boot into Ubuntu--which is the only operating system installed.

GRUB seemed to install fine and I've tried the different recovering methods that have been mentioned in various threads here.  I even used a XP CD to boot into the recovery console to run FIXMBR, but that didn't do anything.  Is there a way to get rid of whatever is causing me to go to Windows Boot Manager rather than into GRUB/Ubuntu?

Thanks for any help!

---

### Post by Pumalite on 2007-08-24
Use DBan: [http://dban.sourceforge.net/](http://dban.sourceforge.net/) and then Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php). Then install again.

---

### Post by logos34 on 2007-08-24
Grub didn't install if you're getting the windows loader.  And doing 'fixmbr' actually restores (or tries to restore) the windows boot loader to the MBR--not what you want to do.

Did you try this method to install Grub --
[http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstalling+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstalling+grub)

---

### Post by StreetProphet on 2007-08-24
I just tried what both of you posted and I'm still getting dumped into the Windows Boot Loader with the error that winload.exe is missing.  I don't get it, there's nothing on the drive except Ubuntu.

---

### Post by merlinus on 2007-08-24
Given the nature of vista and consciousness (rather, lack of same) existing in redmond, it may well be that you have a hidden boot partition from the vista installation.

Did you follow Pumalite's suggestion to use dban and gparted live cd?

Also, look in your BIOS to see if some nasty setting still exists that tries to boot vista.

-merlin

---

### Post by StreetProphet on 2007-08-24
I just tried DBan again and it's giving me a message saying:

DBAN finished with non-fatal errors.
This is usually caused by disks with bad sectors.

Then it saves the log file to a floppy disk, but I don't have a way of getting the log file off of the disk since my laptop doesn't have one (which is where I'm posting from).

---

### Post by logos34 on 2007-08-25
I think you better post your fdisk (from the live CD).  Maybe a leftover boot partition is causing some mischief like merlinus says, or you installed grub to the bootsector of the root partition rather than MBR.

**sudo fdisk -l** (lowercase L)

So, you have just Ubuntu installed on the disk (or did you wipe it?), and no second hard drive, right?

---

### Post by StreetProphet on 2007-08-25
I have two hard drives.  Ubuntu is installed on the disk, but I had wiped it before I installed.  One is simply for storage and the other is my main OS disk.  Would this be causing a problem?

fdisk results:

disk /dev/sda: 80.0 GB 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 - 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 9327 74919096 83 Linux
/dev/sda2 9328 9729 3229065 5 Extended
/dev/sda5 9328 9729 3229033+ 82 Linux swap / Solaris

Disk /dev/sdb: 80.0 GB 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 - 8225280 bytes


Device Boot Start End Blocks Id System
/dev/sdb1 * 1 9730 78148608 7 HPFS/NTFS

---

### Post by merlinus on 2007-08-25
Check the boot order of your hdds in BIOS, and make sure the ubuntu one is first.

You also may need to remove the boot flag from the ntfs partition.

logos34, however, knows lots more about this kind of stuff than I do.

-merlin

---

### Post by StreetProphet on 2007-08-25
> **merlinus said:**
> Check the boot order of your hdds in BIOS, and make sure the ubuntu one is first.

You also may need to remove the boot flag from the ntfs partition.

logos34, however, knows lots more about this kind of stuff than I do.

-merlin

I removed the boot flag from the NTFS drive, GRUB loaded and now I can boot into Ubuntu.  Thanks a bunch guys!

---

### Post by logos34 on 2007-08-25
> **StreetProphet said:**
> I removed the boot flag from the NTFS drive, GRUB loaded and now I can boot into Ubuntu.  Thanks a bunch guys!

I thought there might be another drive.  Just to clarify: what drive are you booting from and did you change it or only remove the flag?

---

### Post by StreetProphet on 2007-08-25
> **logos34 said:**
> I thought there might be another drive.  Just to clarify: what drive are you booting from and did you change it or only remove the flag?

I'm booting from sda.  I removed the boot flag from sdb.

---


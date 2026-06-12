---
title: "Wubi - hard drive has disappeared from Bios"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by Suse on 2010-07-13
Quick background: I've always had problems with Ubuntu on my external hard drive, but I think it's actually with grub in Gnome - any Gnome. I had Karmic installed until after grub upgraded and a bootloader error made it impossible to log in, so I went over to PCLOS KDE. 

I've missed Ubuntu and really wanted Lucid, so I tried reinstalling it to the external. Same problem. I tried PCLOS Gnome, and, yep, same - though I could reinstall the KDE version no problem. Anyway, after umpteen attempts, which included formatting the external drive in Windows (which doesn't ever recognise the external in My Computer till I do), letting Ubuntu do the partitioning, doing the partitioning myself, I finally tried to install through Windows via Wubi - still to the external drive.

It failed, and now the drive is not recognised in the BIOS, Ubuntu, or Windows (I've now installed a dual Ubuntu-Windows boot on my internal).

Have I stuffed up my external drive? Is there some way I can make it recognisable (changing BIOS settings???). Do I need to supply more information?

Thanks.

---

### Post by Suse on 2010-07-13
OK, this error has actually eventually popped up. Seems Ubuntu is now recognising the disk, but I don't know what it's talking about, though perhaps NTFS is inconsistent is the problem?:

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read of MFT, mft=6 count=1 br=-1: Input/output error
Failed to open inode FILE_Bitmap: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

I tried reformatting the drive in Disk Utility and quickly got: Error creating file system: helper exited with exit code 1: Error calling fsync(2) on /dev/sdb1: Input/output error.

When I clicked OK, the drive disappeared again from peripherals devices.

Please say if I need to repost this to a Hardware section, so I don't waste anyone's time.

---

### Post by Mark Phelps on 2010-07-13
> **Suse said:**
> ... Have I stuffed up my external drive? 
Quite possibly.  While Linux CAN access NTFS filesystems, the Linux utilities can not fully repair such filesystems when they become damaged -- which is one of the many good reasons for NOT using Wubi.

> Is there some way I can make it recognisable (changing BIOS settings???). Do I need to supply more information?
If the BIOS can't see it, I doubt any OS is going to see it, either.

If you can connect the drive to an MS Windows box, and IT sees the drive, try running chkdsk on it.  There's a possibility that might repair the filesystem and make it mountable again.

---

### Post by Suse on 2010-07-13
After I tried and failed to reformat it in Ubuntu, it reappeared in the BIOS. It's now in the Windows disk utility till I try to format it, then the power light goes off though the disc still spins, and of course it won't format. Bizarrely, if I disconnect it from the pc so the only thing attached is the power, the light comes straight back on. 

I think it's goosed. :sad: I haven't done anything else, entirely because none of the live cd's or Windows will let me wipe or partition, but now I can't access my internal drive. I think this is all to do with trying to install Wubi in a drive that didn't have Windows, but I was desperate. I'm just going to just make the entire internal drive Ubuntu and maybe I can live without Windows, Gulp.

Thanks Mark.

---

### Post by Suse on 2010-07-15
Just in case anyone with similar problems stumbles on this thread, I hooked up the hard drive to an ancient computer running XP and it was recognised. It even lets me delete and format partitions for a bit, then sadly throws errors. I don't know if there's something about old pc's/old Windows... I'm admitting defeat now, though.

---


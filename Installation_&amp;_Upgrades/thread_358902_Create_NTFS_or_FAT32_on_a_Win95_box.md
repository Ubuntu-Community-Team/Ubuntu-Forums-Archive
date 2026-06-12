---
title: "Create NTFS or FAT32 on a Win95 box?"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by matthewboh on 2007-02-11
I'm trying to install 6.1 on a very old PC without a bootable CD.  I've gotten Boot Loader, starts up, the CD starts up then the Ubuntu CD is read, but then it looks for an NTFS share, but can't find one.

How do I create an NTFS partition on my hard drive?  I don't care if I wipe out the entire two drives.

Thanks,

---

### Post by budgie9 on 2007-02-11
Why should you want one?  Ubuntu uses ext3 not NTFS
So if you are cleaning off the Win95 you don't need either FAT32 or NTFS. Ubuntu will format the drive accordingly.
If you wish to retain some Win95 or later, then retain those drives aprtitions as FAT32 so they can be read by Ubuntu without trouble.

---

### Post by matthewboh on 2007-02-13
I'm using Smart BootManager to get the CD-ROM to boot - would that require NTFS - the error message I'm getting says that it's searching for USB HDD, not finding that, then searching for NTFS drives, not finding that, then dropping into DR-DOS - which I think is the DOS that's on the CD install.

Hmm - I have an idea - I formatted the diskette using XP, but trying to install it on a Win95 box.  I'm going to try and format with Win95 and see if that helps...

Any help greatly appreciated.

Update - gave up.  Finally got a new error message - "Error.  No USB drives found".  Also discovered that it had only 64MB of memory and 1GB of disk space - I'm getting a used Lenovo lap top this afternoon, so I'm going to work on that...

---


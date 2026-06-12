---
title: "Ubuntu not recognizing hard drives."
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by caver_w on 2010-07-05
I've tried multiple times to install Ubuntu on a second computer. The installation always stops at the partition step. Ubuntu does not recognize the hard drives. Drive 1 is a 1 TB Seagate and drive 2 is a 160 GB Samsung. Both are sata drives and both are formatted NTFS.

Ubuntu will boot from the install CD. When I do this and look for files, the hard drives are not present. If from a terminal window I list all devices, the floppy and DVD show up but not the two hard drives.

I tried removing the larger drive and swapping sata ports but no change.

System:
Board XFX  M1-A788-8200 Ver 1.1
Processor  AMD Athlon 64 X2
4 GB ram installed

I do have a SCSI card to support two old scanners. I tried disabling the SCSI but that didn't make any difference.

Computer is presently running Windows XP Home with SP3 build 2600. No problems with MS Windows XP.

Goal is to install Ubuntu on the 160 GB HD and select boot drive on system startup.

I do have Ubuntu 10.04 running on my main computer and Compact laptop with no problems. Both also have Athlon 64 X2 processors.

I read a number of posts with similar problems but none fit this case.

Any suggestions are welcome.

Thank you,
Bill Walden

---

### Post by khuttger on 2010-07-05
Have you tried installing NTFS support? 
```
sudo aptitude install ntfs-3g
```

That is all I had to do to make mine work.

---

### Post by garvinrick4 on 2010-07-05
Before you install remove dmraid from cd.
It has been the solution for not being able to see
your drives at install when page comes up to install
and does not recognize any drives. Worked for quite a few
users. Worth the try.

```
sudo apt-get remove dmraid
```

---

### Post by oldfred on 2010-07-05
Try running chkdsk on all your NTFS partitions.

I had trouble with gparted seeing a drive. Iwas was taking forever to scan drives and then sda was missing. I was able to boot my windows on that drive, but gparted ended up telling my I had issues. I went back to windows and ran chkdsk. Then the entire drive immediately mounted.

---

### Post by caver_w on 2010-07-06
I tried all suggestions but still Ubuntu does not recognize the hard drives.

sudo apt-get remove dmraid   Procedure ran OK but Ubuntu still doesn't recognize the hard drives.
sudo aptitude install ntfs-3g Procedure ran OK but Ubuntu still doesn't recognize the hard drives.
chkdsk  Already ran chkdsk. Did not help.

Pulled the SCSI Card    Did not help.

Clue:  I just plugged my external backup drive into the computer and Ubuntu running from the CD recognized the drive immediately. Perhaps this will allow a work around by swapping drives in the external case.

If anyone has other suggestions, please let me know.

Thank you,
Bill Walden

---


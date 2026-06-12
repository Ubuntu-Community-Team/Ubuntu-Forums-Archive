---
title: "Always has no options when picking partitions(?) when installing"
date: 2013-01-10
forum: Installation &amp; Upgrades
---

### Post by chetlin on 2013-01-10
(forgot to mention: this is 12.10)

Hello,

So for quite some time I've been trying to get Ubuntu installed on this laptop that I got in October.  Every time I use the disk to install I get as far as here, then I have to stop because I have no more options:  [http://i.imgur.com/bZw2x.png](http://i.imgur.com/bZw2x.png)

As you can see I've gone as far now as to create new partitions to try to put Ubuntu in there (did I do it right if I did?).  Apparently the partition with Windows in it has some weird thing going on that causes it to get flagged, which it has had since I got this laptop.  It doesn't cause any problems in Windows, but Ubuntu doesn't like it and won't use it.  There is pretty much nothing on this laptop yet (I got it, given to me by the school, to do my graduate work on) so I don't have to worry about losing any documents, files, etc. that aren't essential to performance.

Is there a way to get Ubuntu installed on its own partition like this so I can keep it separate from Windows (no file sharing between them is necessary or desired)?

I swear this laptop has been the most annoying thing ever to work with.  (If you look in my post history you'll see that I tried something with a "Windows Installer" that didn't work right either.)

Thank you in advance!

---

### Post by efflandt on 2013-01-10
That looks pretty standard for a Dell computer with Windows 7.  The question is, what does gparted say when you hover or click on the OS partition?

For Vista or Win7 it is best to resize a Windows partition from within Windows, but I rarely boot Windows, so I think it is in **Administration Tools**, **Disk Management**.  Then reboot so Windows can check the partition and make sure it is okay.

My guess is that either install shrunk the "OS" partition or you did, which marks it as dirty so Windows will check it next boot.  But if you have not booted into Windows since then, the (!) is probably because the "OS" partition is still marked as dirty and gparted will likely suggest checking it with **chkdsk /f** from Windows (which it should do automatically if you boot into Windows).

This is an example of Dell computer with 64-bit Win7, 64-bit Ubuntu 12.04 on sda4 and 64-bit 11.10 on sdb (SSD).  I have 8 GB RAM and do not hibernate, so no swap needed:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920    24743935    12331008    7  HPFS/NTFS/exFAT
/dev/sda3        24743936  1748717567   861986816    7  HPFS/NTFS/exFAT
/dev/sda4      1748717568  1953523711   102403072   83  Linux

efflandt@XPS8100-1204:~$ sudo blkid
/dev/sda1: UUID="EED2-7775" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="E6CAD622CAD5EF35" TYPE="ntfs" 
/dev/sda3: LABEL="OS" UUID="6440DA0C40D9E538" TYPE="ntfs" 
/dev/sda4: UUID="029ce074-e30a-4351-8652-a566f2fdaf4d" TYPE="ext4" 
/dev/sdb1: UUID="1b68a308-8400-41fc-a1f1-0197397f37b7" TYPE="ext4"
```

---

### Post by chetlin on 2013-01-11
I used to get this same box (no options) before doing any partition resizing.  We did try the "chkdsk /f" and even "chkdsk /b" from within Windows, which fixed things but did not get rid of the flag.  So the next thing I tried was to shrink the Windows partition and try to put Ubuntu into a new partition..this is what I did here with those 2 in the extended partition.  I shrunk the Windows partition from within Windows and then made the 2 new ones from the Ubuntu on the CD.  I've rebooted since then but I'm still having this "no options" issue.

In GParted, the OS partition says that 1 inode is corrupt and that 8578 clusters are referenced multiple times, and then tells me to run chkdsk /f on Windows and reboot twice (which I have already tried 2 times).

Is it possible to put Ubuntu on this other partition manually somehow, so I don't have to deal with the "OS" (Windows) one at all?

---

### Post by oldfred on 2013-01-11
Is this an UltraBoot with a small SSD? That uses RAID and causes lots of issues.

---

### Post by chetlin on 2013-01-12
Yes, it was the RAID thing.  Man.

After such a long time, I finally got it installed, on its own partitions.  These links helped me a lot:
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

---


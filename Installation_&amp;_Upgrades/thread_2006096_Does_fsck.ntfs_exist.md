---
title: "Does fsck.ntfs exist?"
date: 2012-06-18
forum: Installation &amp; Upgrades
---

### Post by orangep on 2012-06-18
Hello. I have four external USB disk drives, three with ext3 or ext4 file systems, and one with NTFS.
The ext3 and ext4 drives work flawlessly.

I added the ntfs drive to /etc/fstab, so that it will automount at
boot-up, thus:
UUID=40284A46284A3AE4   /d2a    ntfs    defaults        0       1

I get strange error messages like:
fsck.ntfs not found

Indeed, there is no /sbin/fsck.ntfs.  They exist for lots of other
things, including msdos and vfat, but no ntfs. Does it exist?

I just did the big system upgrade, and all appropriate packages are installed and up-to-date.

---

### Post by sudodus on 2012-06-18
No I don't think so. NTFS should be maintained with ***chkdsk*** booted from Windows, or
```
chkdsk /f
``` to repair the file system.

---

### Post by Mark Phelps on 2012-06-19
There is ntfsfix -- but it only repairs trivial NTFS problems.

Unfortunately, to repair any major NTFS problems, you still need MS Windows.

---

### Post by oldfred on 2012-06-19
Only the root file system should be 1. So change your fstab entry for your NTFS mount to 0. Then periodically use Windows chkdsk to repair the NTFS partition(s).

man fstab
> 
 The sixth field (fs_passno).
              This field is used by the fsck(8) program to determine the order
              in which filesystem checks are done at reboot  time.   The  root
              filesystem  should be specified with a fs_passno of 1, and other
              filesystems should have a fs_passno of 2.  Filesystems within  a
              drive will be checked sequentially, but filesystems on different
              drives will be checked at the same time to  utilize  parallelism
              available in the hardware.  If the sixth field is not present or
              zero, a value of zero is returned and fsck will assume that  the
              filesystem does not need to be checked.


---

### Post by orangep on 2012-06-23
Ah so. Thanks for the tips. Have a good day now.

---


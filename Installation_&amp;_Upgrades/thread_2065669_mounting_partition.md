---
title: "mounting partition"
date: 2012-10-02
forum: Installation &amp; Upgrades
---

### Post by AnLGP on 2012-10-02
I want to mount my /dev/sda1 partition to my /home/userftp/Desktop/slitaz folder.

how do I accomplish this?  I know it involves editing my /etc/fstab but not more than that.

Thanks!

---

### Post by darkod on 2012-10-02
If sda1 is the windows system partition usually it's better to mount temporary when you need it, instead of always at boot.

If you do want to do it, is it ntfs or ext4? You can mount it either way in /etc/fstab with something like:
```
/dev/sda1   /mount-path   ntfs   defaults   0   2
```

Use the location you want for the mount point. The folder has to exist.

---

### Post by Mark Phelps on 2012-10-02
Would help if you told us (1) what filesystem is on dev/sda1 and (2) why you want it mounted automatically.

If sda1 is NTFS and if it's a Win7 OS partition, then mounting it using FSTAB (unless you force it to mount read-only) is risking filesystem corruption, which could then render Win7 unbootable.

If your reason is for sharing data between Win7 and Ubuntu, it's generally safer to have a shared NTFS "data" partition -- which then will not encounter booting problems.

---

### Post by AnLGP on 2012-10-02
Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   466350079   233174016   83  Linux
/dev/sda3       466352126   625141759    79394817    5  Extended
/dev/sda5       466352128   616900607    75274240   83  Linux
/dev/sda6       616902656   625141759     4119552   82  Linux swap / Solaris

I want to mount automatically so I don't have to keep doing it.  I believe it is an ext3 filesystem, but it could be ext4.  It is not a windows partition.

---

### Post by darkod on 2012-10-02
sudo parted -l

will show you the filesystem too. Then just use ext3 or ext4 in the line I proposed for fstab and it should be fine.

---


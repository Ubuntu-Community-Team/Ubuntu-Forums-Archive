---
title: "Cann't write to Secondary HD D:\"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by RaigyCar on 2007-07-21
I have two HD installed on my machine, but i cannot write to my secondary HD D:\

I can read files from it but cannot write to it.  

How do i resolve this problem?

---

### Post by lisati on 2007-07-21
What kind of file system is on the HD you wish to write to? If it's NTFS you might find that you need some extra tools loaded onto your computer.

---

### Post by RaigyCar on 2007-07-21
The file system is:

vfat (FAT32)

---

### Post by lisati on 2007-07-21
I'm not sure of the answer - anyone else?

---

### Post by ddrichardson on 2007-07-21
Post a copy of /etc/fstab

---

### Post by Pumalite on 2007-07-21
Make sue it's recognized by your BIOS. If yes, then it might be a matter of permissions. But can you see it at all? Could you post: sudo fdisk -l (small L)

---

### Post by koganinja89 on 2007-07-21
you might have to:

> sudo chown username /folder

---

### Post by RaigyCar on 2007-07-22
sudo fdisk -l:

Disk /dev/sda: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3736    30009388+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4865    39078081    c  W95 FAT32 (LBA)
ubuntu@desktop:~$ 

When i type /etc/fstab into the terminal is says:

bash: /etc/fstab: Permission denied


I installed Ubuntu using the Wubi installer using 4GB of my D:\ drive.

What does:  sudo chown username /folder            do?

---

### Post by ddrichardson on 2007-07-22
sudo cat /etc/fstab will print it.

---

### Post by RaigyCar on 2007-07-22
sudo cat /etc/fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults          0   0
/media/host/wubi/disks/system.virtual.disk      /               ext3        loop,sync         0   1
/media/host/wubi/disks/home.virtual.disk      /home           ext3        loop,sync         0   2
/media/host/wubi/disks/swap.virtual.disk      none            swap        sw                0   0

---

### Post by ddrichardson on 2007-07-22
OK, I'm not familiar with Wubi - but there's no entries in the fstab about a second disk. Perhaps someone with more knowledge in wubi can help with mounting. fat32 should be r/w by default.

---

### Post by Pumalite on 2007-07-22
Sorry. Don't know Wubi either.

---


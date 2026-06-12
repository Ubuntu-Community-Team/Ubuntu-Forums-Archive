---
title: "how to recover my ubuntu 9.10 after installing windows"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by woodmawa on 2009-12-31
tried to read the posts on similar topics but not sure i'm getting this.


scenario - 

installed windows 7 on new machine - fine.  
installed ubuntu9.10 64 bit on a another drive in the machine.

ubuntu overwrote my MBR with the grub loader stuff but this worked okay for a while.

Had to install windows xp on main drive which overwrote the MBR again.  Resurrected my windows 7, and xp in dual boot mode by editing easybcd.

so far so good 

now trying to get my ubuntu back - stumped.

found a posting that looked good - tells bootmanager how to load the linux - take a copy of the linux boot boot sector 
(used sudo dd if/=dev/sdb1 of=/tmp/linux.bin bs-512 count=1) and copied the boot sector into my active partition on main drive where bootmanager can see it.

my disk setup from fdisk is 
> 
ubuntu@ubuntu:/$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50207789

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       96105   771857408    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           96106      121600   204788587+   f  W95 Ext'd (LBA)
/dev/sda5           96106      121600   204788556    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07164d5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23330   187398193+  83  Linux
/dev/sdb2           23331       24321     7960207+   5  Extended
/dev/sdb5           23331       24321     7960176   82  Linux swap / Solaris


I booted into live CD and mounted my linux build (mkdir /mnt/root and then mount /dev/sdb1 /mnt/root)

I then tried grub install telling it to do so with root-directory set as the "boot" dir from linux install.  HOwever this gives the following errror that doesnt look good.  

> ubuntu@ubuntu:/mnt/root$ sudo grub-install --root-directory=/mnt/root/boot /dev/sdb1
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly



How do i install grub2 from live CD into my existing linux build so i can try and chain load it from bootmanager on my active bcd config?

---

### Post by dstew on 2009-12-31
My understanding of the grub 2 installation command is that the argument of the --root-directory parameter is the root directory of the Linux filesystem that will be used to store the grub configuration, not the /boot directory. The grub-install command expects to find a /boot directory in the root directory you designate. So, if you designate /boot as the root directory, there will not be a /boot directory in there. Try the command:```
sudo grub-install --root-directory=/mnt/root/ /dev/sdb1
```and see if that works.

---


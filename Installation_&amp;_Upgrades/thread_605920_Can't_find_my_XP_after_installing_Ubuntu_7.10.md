---
title: "Can't find my XP after installing Ubuntu 7.10"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by tapuach on 2007-11-07
I've installed Ubuntu 7.10 on my Dell 1500 laptop and can't access my XP anymore....
I can't find the XP partition and when I try to add it manually to GRUB menu.lst, I'm getting "Error 13".
Any idea?

root@abc-laptop:/boot/grub# fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     3903794     1951866   82  Linux swap / Solaris
/dev/sda2   *     3903795    42973874    19535040   83  Linux


root@abc-laptop:/boot/grub# cd /media/
root@abc-laptop:/media# ls -la
total 12
drwxr-xr-x  3 root root 4096 2007-10-16 01:17 .
drwxr-xr-x 21 root root 4096 2007-11-07 14:30 ..
lrwxrwxrwx  1 root root    6 2007-11-07 14:16 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-11-07 14:16 cdrom0

Thanks,
Eli

---

### Post by logos34 on 2007-11-07
sure you didn't mistakenly choose 'Guided - use entire disk' instead of 'Guided - resize' during installation?  If the former, xp's gone.  

[http://img379.imageshack.us/img379/4594/feistydual07vo7.th.png](http://img379.imageshack.us/img379/4594/feistydual07vo7.th.png)

What does gparted show?

sudo gparted

---

### Post by tapuach on 2007-11-07
> **logos34 said:**
> sure you didn't mistakenly choose 'Guided - use entire disk' instead of 'Guided - resize' during installation?  If the former, xp's gone.  

[http://img379.imageshack.us/img379/4594/feistydual07vo7.th.png](http://img379.imageshack.us/img379/4594/feistydual07vo7.th.png)

What does gparted show?

sudo gparted


I've used the manual option and created two new partitions: swap (2GB) and ext3 (20GB).
I did NOT use the "use entire disk" option!

The gparted was not installed but after installing it:
Partition Filesystem Mountpoint Size Used Unused Flags
/dev/sda1 linux-swap  1.86GiB --- ---
/dev/sda2 ext3 / 18.63GiB 2.34GiB 16.29GiB boot
unallocated unallocated  91.3 GiB --- --- 

Thanks!
Eli

---

### Post by logos34 on 2007-11-07
Get [Super Grub Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")...if XP is still there and bootable, SGD will likely be able to get you into it.  Of course that still doesn't solve the problem of why windows shows up as unallocated space.  It's possible that shrinking XP (assuming that's what you did to make room for linux) messed up the partition table.  If you have a XP install cd you could try running chkdsk from the recovery console.

---


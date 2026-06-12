---
title: "Grub Error 22"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by Redlazer on 2008-11-18
I'm making a server for testing purposes, so I installed a bunch of OS's. I got the error message that you can't have more than 4 primary partitions, so I left it at 4: one XP(fat32), one Vista(ntfs), one Kubuntu(ext3), and one for data(xfs).

There are three other harddrives attached to the machine.

All of them should be working just fine.

When I boot, i get 

"Grub Loading 1.5....

Error 22"

I've already tried reinstalling Kubuntu, to no effect.

Any ideas?

-Fred

---

### Post by pennacook on 2008-11-18
I'd suggest looking at this [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
to fix the grub install.

---

### Post by caljohnsmith on 2008-11-18
You can actually have more than four partitions if you delete one of your primary partitions and turn it into an "extended" partition; inside the extended partition you can create about as many logical partitions as you want (up to 63 I think). :)

But about your Grub problem, how many HDDs do you have? And do you have a Live CD that you can boot for troubleshooting purposes? If you do, boot that up, open a terminal (applications > accessories > terminal), and please post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by Redlazer on 2008-11-18
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes                               
Disk identifier: 0x819355ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976768064   488384001   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1b90f18a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    20482874    10241406    7  HPFS/NTFS
/dev/sdb2        20482875    61448624    20482875    7  HPFS/NTFS
/dev/sdb3        61448625   102414374    20482875   83  Linux
/dev/sdb4       102414375   234436544    66011085    5  Extended
/dev/sdb5       230532750   234436544     1951897+  82  Linux swap / Solaris
/dev/sdb6       102414501   230516684    64051092   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0b9d9cd1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdd: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcd77cd77

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   586067264   293033601   83  Linux

--------------------------------------------
for sda: GRUB
for sdb: missing operating system
for sdc: GRUB
for sde: nothing
-------------------------------------------
for sda: 8102
for sdc: 8102

each of them has a blank line after the 8102, if that matters.
-----------------------------------------

As far as the setup is concerned, I have four drives (as you can see), each on SATA. The sda should be the drive with all the OS's on it (XP,Vista,Kubuntu), but its sdb, upsettingly. Now that i think about it, i may have switched the SATA cables. 

-Fred

---

### Post by psusi on 2008-11-18
What is on sda?  It looks like a single linux partition.  This is the drive that grub thinks your system boots from, so this is where it installs itself.  Is this the drive your bios is set to boot from?  If not you will need to reinstall grub to the correct drive.

---

### Post by Redlazer on 2008-11-18
Ok, its working now!

However, i'm now missing the XP and Vista partitions.

-Fred

---


---
title: "Please help:  Two-disk installation - Windows Partition Gone"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by unMourned on 2008-05-10
Please, please help.

I installed HH8.04 onto hard drive "B"; Windows XP resides on hard drive "A".

Ubuntu asked me where I wanted to install GRUB, with the default set as (hd0).  I selected /dev/sda1 because GRUB found the XP installation there.  Completed the installation and...

I now cannot boot into XP.  Booting off the Windows XP CD detects no XP installations.

sudo fdisk -l gives me:

> pjohnston:/boot/grub$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e3d9768

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        1782    14305851    7  HPFS/NTFS
/dev/sda2            1783        3741    15735667+   f  W95 Ext'd (LBA)
/dev/sda3            3742        4785     8385930    7  HPFS/NTFS
/dev/sda4            4786        9729    39712680    7  HPFS/NTFS
/dev/sda5            1784        3741    15727603+   7  HPFS/NTFS

Disk /dev/sdb: 15.3 GB, 15367790592 bytes
255 heads, 63 sectors/track, 1868 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb400c3af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1784    14329948+  83  Linux
/dev/sdb2            1785        1868      674730    5  Extended
/dev/sdb5            1785        1868      674698+  82  Linux swap / Solaris


My menu.lst file ends with:
> 
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c184c007-0826-42e8-bd2d-3db28022330b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c184c007-0826-42e8-bd2d-3db28022330b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1


I have tried using "root" for the XP HDD as:
(hd0,0)
(hd0,1)
(hd0,2)

hd0,0 bounces back to the main grub menu.
hd0,1 hangs as loading.
hd0,2 provides ntldr missing error.

Again Windows XP is on hdd "A," or /dev/sda1

In Ubuntu, I cannot see extended, logical partitions of /dev/sda1, but not the main physical partition.

I've looked through several forum postings and nothing has enabled me to boot into XP.  At this point in time, my wife may kill or maim me when she finds out she cannot check her non-web-based email.

Please help.

Thank you,
Paul

---

### Post by unMourned on 2008-05-10
I am in somewhat of a crisis situation, and need to get into windows as soon as possible.

Any help?

Please?

Thanks,
Paul

---

### Post by Sef on 2008-05-10
Check out [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") and see if you can recover it.

---

### Post by Pumalite on 2008-05-10
See if Super Grub can boot either one or both: 
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Burn to disk and boot from it.

---

### Post by unMourned on 2008-05-20
What a strange experience.  My wife needed the computer for work later in the day, so I decided to scrap the Ubuntu installation altogether.

However, I couldn't boot from the cd.  Her computer would boot right into Ubuntu 8.04.  I finally disconnected the Ubuntu hard drive, leaving the windows hard drive as the only hard drive on the system.  Nothing.  Went into BIOS, and had to re-enter boot sequence as CD-ROM, hdd--after which I was able to boot from WinXP install CD.

I then ran "fixmbr" and then "fixboot" and then ran checkdisk on all volumes on that hdd.

I could then boot her system.

I guess a two-disk dual o/s install is a little more in-depth than I thought.

-p

---

### Post by confused57 on 2008-05-20
> **unMourned said:**
> What a strange experience.  My wife needed the computer for work later in the day, so I decided to scrap the Ubuntu installation altogether.

However, I couldn't boot from the cd.  Her computer would boot right into Ubuntu 8.04.  I finally disconnected the Ubuntu hard drive, leaving the windows hard drive as the only hard drive on the system.  Nothing.  Went into BIOS, and had to re-enter boot sequence as CD-ROM, hdd--after which I was able to boot from WinXP install CD.

I then ran "fixmbr" and then "fixboot" and then ran checkdisk on all volumes on that hdd.

I could then boot her system.

I guess a two-disk dual o/s install is a little more in-depth than I thought.

-p

It's really not that difficult to set up a dual boot with 2 hard drives.  When I first started using Ubuntu, here's how I set up my system:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---


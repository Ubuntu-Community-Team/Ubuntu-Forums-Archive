---
title: "trouble mounting an internal  ext3 drive"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by swiftor on 2008-03-24
i have been following this tutorial.. [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) and after editing the fstab and saving, when i am trying to mount the drive with "sudo mount -a" i get this error... 

mount: special device /dev/disk/by-uuid/DC54CF8F54CF6ABA does not exist


but when i fdisk -l i get

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x222c222b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        3886      498015   82  Linux swap / Solaris
/dev/sda3            3887       19457   125074057+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a48a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60424   485355748+  83  Linux
/dev/sdb2           60425       60801     3028252+   5  Extended
/dev/sdb5           60425       60801     3028221   82  Linux swap / Solaris


the partition i am trying to mount is the dev.sdb1 


any ideas?

---

### Post by pietjanjaap on 2008-03-24
Instal "gparted", start this with "gksu gparted", then you can mount it.
With "gksudo nautilus" you can change the user permissions.
Then remove the harddisk from the fstab, and reboot.

---

### Post by swiftor on 2008-03-24
thanks! that fixed it right up! you rock :)

---


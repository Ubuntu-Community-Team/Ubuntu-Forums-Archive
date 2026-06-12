---
title: "Install to Multiple Drives, but only one OS"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by Goldambre on 2012-01-21
Greetings all
 
I may be over thinking or complicating this.
 
I have an older computer with 2@ 20 GB hard drives plus a 30 GB USB drive.  I am trying to set my partitions for optimal performance (relatively).  The question for you experts is what is the best way to create the partitions on this old machine?  There is one additional challenge: because of the BIOS, this machine will only boot from CD or one of the 20GB hdds.
 
Any guidance would be appreciated!

---

### Post by fantab on 2012-01-21
I would have made one 20GB HDD or /dev/sda a single primary partition, /dev/sda1 and installed Ubuntu with Ext4 "/". The other 20 GB or /dev/sdb could be my /dev/sdb1 /home or just a DATA Partition. The 30GB or /dev/sdc will be my DATA partition. 

OR

If your "older computer" can support [**LVM** (Logical Volume Management)]("http://www.howtoforge.com/linux_lvm") , then you should consider it. I have personally never used LVM and so I cannot help you beyond the provided link. The Gurus here might be able to help you better.

---

### Post by sudodus on 2012-01-21
> **fantab said:**
> I would have made one 20GB HDD or /dev/sda a single primary partition, /dev/sda1 and installed Ubuntu with Ext4 "/".The other 20 GB or /dev/sdb could be[/COLOR] my /dev/sdb1 /home or just a DATA Partition. The 30GB or /dev/sdc will be my DATA partition. 

OR

If your "older computer" can support [**LVM** (Logical Volume Management)]("http://www.howtoforge.com/linux_lvm") , then you should consider it. I have personally never used LVM and so I cannot help you beyond the provided link. The Gurus here might be able to help you better.
+1 (or at least something similar)

I suggest you keep things simple: Install on the first one, /dev/sda, and let the other disks contain data partitions. I also suggest that you give ***labels*** to the partitions on the two data disks. You can easily do that starting a live session from the install CD or USB drive and use ***gparted***. The labels makes it easy to recognize the two data drives in the file browser.

Furthermore, you can create symbolic links in your home folder or on your desktop to the data drives. That helps you rememeber to put your data there instead of crowding the system disk.

But if you want to do something more advanced, I suggest that you make a /home partition on the second drive and use the third drive for a swap partition of twice the RAM size and a data partition (using the rest of the drive space).

---

### Post by Goldambre on 2012-01-21
Thanks folks.  That helps a lot!

---


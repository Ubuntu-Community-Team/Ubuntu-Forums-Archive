---
title: "Ubuntu 12.10 SSD Harddisk"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by wolvelopez on 2012-10-23
Hello fellow.
I'm trying to install Ubuntu 12.10 on my laptop HP Pavilion DV2000 and when I get to the point of the partitions do not recognize the hard disk SSD (Samsung 830).
I've never had problems with SATA disks and for example if you try to install Xubuntu recononce smoothly.
Do you know what can be? Worth SATA Windows driver for Ubuntu and have to load the driver side?
Thank you very much.

---

### Post by oldfred on 2012-10-23
Welcome to the forums.

Does BIOS see SSD ok?

Was SSD in RAID or Intel Smart Response?

Does SSD have any corruption. If previously NTFS and it needs chkdsk Linux will often not mount it to prevent further damage.

Post this from terminal  liveCD.

sudo parted /dev/sda unit s print

---

### Post by wolvelopez on 2012-10-23
Thanks,
The SSD in BIOS is reconize.
CHKDSK is OK
I managed to install Ubuntu 12.10 and leaving formatting the disk without partitions with gparted.
But after installing grub fails.
"Error read write HD0..."
Thanks!!

---


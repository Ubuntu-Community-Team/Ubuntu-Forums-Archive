---
title: "how to change drive enumeration order"
date: 2011-04-12
forum: Installation &amp; Upgrades
---

### Post by Wej on 2011-04-12
Hello,

I am installing Ubuntu Server 10.04 LTS on a new server that has 21 hard drives. My OS/boot drive is plugged into a SATA port on the motherboard, and the other 20 drives are plugged into cheap 4 port SATA adapter cards plugged into the PCIe slots on the motherboard.

When I first get to the part of the installer where I set up partitions and such, it is enumerating my disks in a somewhat weird order. The first 4 disks sda, sdb, sdc and sdd are disks connected to one of the SATA controllers, then sde is my smaller OS disk. **Is there any way to force the small OS disk to be sda before I continue setting up my RAID?** It's not a huge deal, but I'd like to have the system drive be sda, as it is in all my other systems. This is the 3rd system I've built like this, but it's the first time I've run into this issue (newer motherboard than the last one).

If possible I'd like to use the menu system in the installer to setup the RAID, as typing all those disk names manually into an mdadm config manually is going to be a huge pain. That precludes me from just unplugging the extra drives until after I get the base OS installed and working.

Thanks!

---

### Post by Hedgehog1 on 2011-04-12
Wej,

If you cannot use UUIDs from the drives (and I don't think you can in this case) I found this:

> If you want to make /dev/sda be allways specific drive, you will have to mess around with UDEV scripts.

From: [how-to-force-hard-drive-device-number-linux]("http://serverfault.com/questions/236803/how-to-force-hard-drive-device-number-linux")

Intro to UDEV:   [http://www.reactivated.net/writing_udev_rules.html]("http://www.reactivated.net/writing_udev_rules.html")

> ... If you wish to provide alternate names for this device node, you use the symbolic link functionality. With the SYMLINK assignment, you are actually maintaining a list of symbolic links, all of which will be pointed at the real device node. To manipulate these links, we introduce a new operator for appending to lists: +=. You can append multiple symlinks to the list from any one rule by separating each one with a space.

KERNEL=="hdb", NAME="my_spare_disk"
The above rule says: match a device which was named by the kernel as hdb, and instead of calling it hdb, name the device node as my_spare_disk. The device node appears at /dev/my_spare_disk.

KERNEL=="hdb", DRIVER=="ide-disk", SYMLINK+="sparedisk"

This means you could set:

/dev/sde to /dev/os_drive
/dev/sda to /dev/ctrl1_drive1
/dev/sdb to /dev/ctrl1_drive2
and so on...


***The Hedge***

:KS

---


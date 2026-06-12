---
title: "cleanoff xp hard drive using live cd"
date: 2011-07-20
forum: Installation &amp; Upgrades
---

### Post by pmdelage on 2011-07-20
Can I use a liveCD of 11.4 to clean off my xp hard drive before installing Ubuntu?

---

### Post by Quackers on 2011-07-20
Welcome to UF.
If you just elect to use the whole drive for installing Ubuntu it will format the drive.
Or you can choose the "try Ubuntu" option and when the desktop loads open gparted and delete all the existing partitions.

---

### Post by pmdelage on 2011-07-20
Thanks, now the install stops and says, "No root file system is defined.  Please correct this from the partitioning menu."  But I can't see what to do or how to do it.  PMD

---

### Post by Quackers on 2011-07-20
duplicate post!

---

### Post by Quackers on 2011-07-20
With the automated install option I don't think that should happen - or are you using the manual approach?
If the latter you need to give a mount point for the main Ubuntu partition, which is " / " for root. If you have a separate partition for /home you need to give that a mount point of /home, by clicking on the down arrow next to "mount point" and selecting them from the drop-down box.

---

### Post by pmdelage on 2011-07-23
Had to leave this for awhile.  I have installed ubuntu 11.04 on Toshiba laptop hard drive, but it will not boot.  I can boot it using a 9.04 livecd (often almost boots using livecd but then immediatley shuts down, but that is another story, I think. I just keep trying and finally it boots up.) Here is a screen shot, which I gather shows why it does not boot.  Can someone tell me steps to take to get the bootloader in the right place.  Thanks from a real noobie.  Paul

---

### Post by Quackers on 2011-07-23
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by pmdelage on 2011-07-23
Herewith as directed:
 
```
       Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

   File system:       ext3
   Boot sector type:  -
   Boot sector info:
   Operating System:
   Boot files:        /etc/fstab

sda2: __________________________________________________________________________

   File system:       Extended Partition
   Boot sector type:  -
   Boot sector info:

sda5: __________________________________________________________________________

   File system:       swap
   Boot sector type:  -
   Boot sector info:

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000f1e77

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    37,351,124    37,351,062  83 Linux
/dev/sda2          37,351,125    39,070,079     1,718,955   5 Extended
/dev/sda5          37,351,188    39,070,079     1,718,892  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs
/dev/ramzswap0                                          swap
/dev/sda1        89a9b2b1-34ab-4ec5-a28f-6f2d76bcce8e   ext3
/dev/sda5        fd6efa53-15f9-455d-9cb5-a8624f70bf6b   swap

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=89a9b2b1-34ab-4ec5-a28f-6f2d76bcce8e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fd6efa53-15f9-455d-9cb5-a8624f70bf6b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------


```

---

### Post by Quackers on 2011-07-23
Ubuntu may not be properly installed. There are no grub files present in the sda1 partition and there should be and no operating system type is shown.
I would re-install again using the same partitions (just use them again, choosing to format the root partition).

---


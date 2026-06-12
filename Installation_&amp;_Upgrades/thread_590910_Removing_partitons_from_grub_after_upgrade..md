---
title: "Removing partitons from grub after upgrade."
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by Whitewater155 on 2007-10-25
Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Hey everone

I recently went from Ubunty 7.04 to 7.10. I didn't run the upgrade utility. I had 7.04 installed on /dev/sdb1 w/swap on /dev/sdb2 .  When I went to 7.10, I repartitoned /dev/sda and installed Ubuntu on the free space.

Here's the disk layout:

Units = cylinders of 15120 * 512 = 7741440 bytes

Disk identifier: 0xa342ef6f

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         658     4974448+   b  W95 FAT32
/dev/sda2   *         659       10367    73400040    7  HPFS/NTFS
/dev/sda3           10368       25645   115501680   83  Linux
/dev/sda4           25646       25841     1481760    5  Extended
/dev/sda5           25646       25841     1481728+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00009a41

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15349   123290811   83  Linux
/dev/sdb2           15350       15505     1253070   82  Linux swap / Solaris
/dev/sdb3           15506       19457    31744440    b  W95 FAT32

/dev/sda1 is a Compaq Recovery Partition. I can remove it, but would prefer not to.

Grub is installed on /dev/sda and /dev/sdb. Do I need to remove it from /dev/sdb or is it OK to leave it. If I need to remove it, how would I do that.

I want to repartition /dev/sdb and combine /dev/sda1 and /dev/sda2 as ext3 file systems.

Any ideas? advice?

Thanks in advance
David  :confused:

---

### Post by meierfra on 2007-10-25
> Grub is installed on /dev/sda and /dev/sdb. Do I need to remove it from /dev/sdb or is it OK to leave it. If I need to remove it, how would I do that.

No need to remove it.

> 
want to repartition /dev/sdb and combine /dev/sda1 and /dev/sda2 as ext3 file systems.

Use the gparted live CD to do the partitioning ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)) and backup any valuable data  beforehand.

---

### Post by mrfelker on 2007-10-25
As the prior poster said - no need to uninstall GRUB from either hda or hdb. Use Gparted as the gentleman suggests to make either hda0 or hdb0 the "active" partition.

---

### Post by meierfra on 2007-10-25
> Use Gparted as the gentleman suggests to make either hda0 or hdb0 the "active" partition.

Ignore this. Leave the boot flag at the "windows partiton".  Grub does not use the boot flag. As far as I know only windows sometimes has problems if it is not on  an active partition.

Edit:  Oops. I only thought about the different grub installs, and forgot that the OP is going to delete windows. If grub is installed to the MBR you still don't need to set any boot flags. But  if some other boot loader is in charge of the MBR,  you might have to set the boot flag  to the ubuntu boot partition.

---

### Post by mrfelker on 2007-10-25
This last response isn't quite accurate - no offence to the replier at all.  If you use the text alternate install you will see that the Ubuntu boot partition must be flagged as "bootable" in order for Ubuntu to boot - otherwise you will only get Windows.  

BTW - if you just want to bypass a OS when booting Ubuntu - just remove it from /boot/gurb/menu.lst (make a backup of the file first!).  Since I am using a multiple boot product I comment out the section to boot Windows using chainloader +1 on the Windows partition (usually sda1 or hda1).

---

### Post by Whitewater155 on 2007-10-25
Hey everyone,

Thanks for the replies. I now know what I need to do.

I knew I'd have to edit the menu.lst for grub. It's a pretty long list of OS's, New Ubuntu, Old Ubuntu, and Windows.

Dave

---

### Post by meierfra on 2007-10-25
I edited my previous post just  to avoid problems for anybody else who  comes across this thread.

---


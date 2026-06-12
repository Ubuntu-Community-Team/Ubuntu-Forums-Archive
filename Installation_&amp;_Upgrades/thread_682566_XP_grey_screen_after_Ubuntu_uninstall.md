---
title: "XP grey screen after Ubuntu uninstall"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by Rames on 2008-01-30
My Dell desktop shows blank grey screen with XP setup CD while trying to recover XP home SP2 partition.

Config: Dell desktop with 120GB HDD has XP Home OS in 34.5GB partition, and Ubuntu in a 20GB partition at end of the disk.

Problem: Uninstalling Ubuntu removed the OS loader for XP. Recovered C partition with XP OS and ran chkdsk successfully. Playing with Testdisk, I restored Linux partitions, but  lost a 39MB Dell Utility partition in beginning of disk. After this, the XP setup CD could not get thru to the recovery console - after setup inspects system config, it leads to a blank grey screen.

The Dell utility partition could not be recovered in Testdisk search; creating a FAT16 partition with DE type did not work. Reinstalled Ubuntu to see if it repairs the MBR with no luck.

Current status: Ubuntu boots fine; can see ntfs partition & data in it. No access to XP recovery console with XP setup cd to fixboot & fixmbr, & as a result XP does not start.

sudo fdisl -lu

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xedd3edd3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       80325    72404954    36162315    7  HPFS/NTFS
/dev/sda2        92550465   216524069    61986802+   f  W95 Ext'd (LBA)
/dev/sda3       216524070   234372284     8924107+  83  Linux
/dev/sda5        92550528   139460264    23454868+   7  HPFS/NTFS
/dev/sda6       139460328   192137399    26338536    7  HPFS/NTFS
/dev/sda7       192137463   214532009    11197273+  83  Linux
/dev/sda8       214532073   216524069      995998+  82  Linux swap / Solaris

sudo /boot/grub/menu.lst
XP portion:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition (on Volume 1)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Appreciate advice on getting to recovery console beyond the blank, greay screen from XP setup CD:

Thanks!

---

### Post by nasov on 2008-01-30
format c:/ -q

?

have u tried that?

---

### Post by nasov on 2008-01-30
but for real...

try popping the winxp cd into the drive, start from CD, when it loads ASR (Automatic System recovery) press F3 or F2 - can't remember (this might be also one of the options to choose from after the initial files were copied onto your hdd) and when it brings you to the command line type in

**fixmbr**

plus...
I'm not too sure but this might overwrite GRUB... so you'll "*loose*" ubuntu - i would google that.

see if it works!
if not you can always try **format c:/ -q**



wink wink nodge nodge

---

### Post by Rames on 2008-01-30
The XP setup does not go as far as ASR; it blanks out the screen immediately after inspecting system config.

Good one about the format :-)

---


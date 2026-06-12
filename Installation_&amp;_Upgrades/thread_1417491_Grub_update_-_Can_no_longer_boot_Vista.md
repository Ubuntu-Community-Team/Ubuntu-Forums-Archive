---
title: "Grub update - Can no longer boot Vista"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by sdpkelkar on 2010-02-27
Hi.
I am a total noob on Linux and recently installed Ubuntu (Karmic Koala) on a Dell Inspiron 1525 which already had Vista installed on it. The installation went just fine and I could boot into either Ubuntu or Vista using the Grub bootloader options. After updating grub through the update manager however, I can no longer boot into Vista and get an error message that says

"Windows cannot start. A recent upgrade or hardware change may have caused this (blah
blah)

And below that:

File: \boot\bcd
Status: 0xc000000e
info: An error occurred while attempting to read the boot configuration data"

When I run sudo fdisk -l, I get the following:

[[COLOR=blue][/COLOR]]("http://www.vistaheads.com/forums/#")Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       13619   109345113+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           13619       15936    18605117+   7  HPFS/NTFS
/dev/sda4           15937       19457    28282432+   f  W95 Ext'd (LBA)
/dev/sda5           19066       19457     3148708+  dd  Unknown
/dev/sda6           15937       18930    24049242   83  Linux
/dev/sda7           18931       19065     1084356   82  Linux swap / Solaris

Partition table entries are not in disk order

I have the Vista recovery disk but was wondering whether using it to repair the Vista bootloader might mess up Grub. Any advice would be appreciated!

---

### Post by oldfred on 2010-02-27
There are several commands in the Vista repair if you do it from the command line. Do not run fixboot as that will overwrite the MBR with grub. It is not all that difficult to reinstall grub if necessary. I think if you run the automatic repair it will overwrite grub.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

---

### Post by darkod on 2010-02-27
You have to be very careful when using a recovery disc, and depending what sort of disc it is. If it's one of the discs allowing to repair the boot process, fine, but if you are actually talking about the restore disc coming with the computer, that kind of disc can easily delete all the hdd and recreate the factory default setup.

So depending what we are talking about, be VERY CAREFUL!!!

---

### Post by sdpkelkar on 2010-02-28
Thanks a ton! I'll try it out.

---

### Post by sdpkelkar on 2010-02-28
Voila! All I had to do was boot from the recovery disk and select the startup and repair tool. The problem was a corrupted BCD file..and now everything works just fine. Many thanks!

---

### Post by Gen2ly on 2012-04-27
Thanks oldfred.  This is exactly what I needed.  Ignoring the /fixmbr and doing the following three commands fixed the problem.  Not sure why installed Grub broke this but it's working good now.

---


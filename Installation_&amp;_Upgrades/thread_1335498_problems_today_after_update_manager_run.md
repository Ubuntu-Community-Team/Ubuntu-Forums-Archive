---
title: "problems today after update manager run"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by ak331 on 2009-11-23
this morning i ran update manager and it was working fine before that.

when it told me to restart what i got was grub starting followed by the following :

> >grub to see menu hit tab to see all acpi

I followed all I could comprehend but reboot brings it to grub menu and does not any further.

when I do the following > $ sudo fdisk -l

I get the following message.
     Disk /dev/sda: 60.0 GB, 60022480896 bytes
240 heads, 63 sectors/track, 7753 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x0000675f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7752    58605088+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x761360a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14195   114019888+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2           14196       19457    42267015    5  Extended
/dev/sdb5           14196       18815    37110118+  83  Linux
/dev/sdb6           18816       19457     5156833+  82  Linux swap / Solaris

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x017b966e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    7  HPFS/NTFS
 

I checked the /boot/grub directory there is no menu.lst in the directory.

I wonder what happened here. I hope to fix it without reinstalling the ubuntu 9.10 all over again.

any help appreciated.

---

### Post by phillw on 2009-11-23
Hi,

If you're running a clean install of 9.10, then grub has changed to a new version.

For issues dual booting (It looks like you have windows & ubuntu), then [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  Should sort you out.  

I'm reading your system as the operating systems (windows & ubuntu) being on your 2nd hard drive - so, you'll be looking to do grub work / mbr work on sdb.

If you need to rebuild Grub2 from the LiveCD, then it's step 12 here -->  [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)   which also has a link to  more in depth look at it.

If you're still unsure, please post back & I'll get drs, our Grub2 guru, to look at it for you.

Regards,

Phill.

---


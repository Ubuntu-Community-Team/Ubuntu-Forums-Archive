---
title: "Ubuntu 12.10 cannot boot up after installing Windows 8"
date: 2012-12-23
forum: Installation &amp; Upgrades
---

### Post by shinnyx on 2012-12-23
Hi all, 

As the title said, I tried to fix with boot-repair but it does nothing. When I looked into the url [http://paste.ubuntu.com/1460797/](http://paste.ubuntu.com/1460797/) , sda4 where the ubuntu is installed show nothing.

Below shows my fdisk output
```

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd39bb0d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   614402047   306841600    7  HPFS/NTFS/exFAT
/dev/sda3       614402048  1157943295   271770624    7  HPFS/NTFS/exFAT
/dev/sda4      1157945342  1465147391   153601025    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1449148416  1465147391     7999488   82  Linux swap / Solaris

```

Thanks in adv for the help!

---

### Post by 2F4U on 2012-12-24
To me it looks as if /dev/sda4 doesn't contain anything. Can you mount the partition from a liveCD and see if it contains anything? Maybe the partition was formatted during the Windows 8 installation?

---

### Post by oldfred on 2012-12-24
Windows does not see Linux partitions and probably did not rewrite partition table correctly.

It looks like your extended partition is larger than just swap, so it may have had another partition in it?

I would try test disk and see what it says.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
       [https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")
    repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Also:
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---


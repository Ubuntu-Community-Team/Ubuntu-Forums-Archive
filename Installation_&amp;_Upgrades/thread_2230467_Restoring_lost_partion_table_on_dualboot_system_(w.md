---
title: "Restoring lost partion table on dualboot system (windows 8 and Ubuntu 13.04)"
date: 2014-06-19
forum: Installation &amp; Upgrades
---

### Post by sanjayjohny-mec on 2014-06-19
I have a 64 bit system with 750gb hard disk with 2 partition in windows 8 and one root and home partition in Ubuntu 13.04.
  I installed Linux mint 17 by choosing option 
  [INDENT]   Erase Ubuntu 13.04 and install  
 [/INDENT]  After installation their is only Linux Mint and 692.1 GB free space.Please help me to recover my files

---

### Post by Mark Phelps on 2014-06-19
You will need to have access to another PC, one running Windows and able to burn a CD.

When you get that, download and burn a CD of the Minitool Partition Wizard Boot CD.

Boot from that CD and use the option to Recover the partition(s).

If that works, you should be OK.

---

### Post by oldfred on 2014-06-19
Mint is changing the wording, Ubuntu does not seem to want to since it is not a bug just really poor description.

[https://github.com/linuxmint/ubiquity/commit/8bfc98e60cc80cefe7986774f3740a5b0530e364](https://github.com/linuxmint/ubiquity/commit/8bfc98e60cc80cefe7986774f3740a5b0530e364)

---

### Post by sanjayjohny-mec on 2014-06-20
But i am on my laptop

---

### Post by oldfred on 2014-06-20
Did you try the mini-tool partition wizard?

Linux also has testdisk which does many of the same things.
But because some of your data has been written over, you will not recover a working system just some files that were not overwritten. Linux is not large and writes to entire drive where Windows system & data are usually at the beginning of the drive.

To restore a working Windows you can restore from your backup which the vendor suggests since they only provide an image on the hard drive, check with Vendor to see if they offer images for your system at nominal charge, or purchase a new copy of Windows. Your product key is imbedded inside the UEFI and only works with the vendor image not any other copy.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

            Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---


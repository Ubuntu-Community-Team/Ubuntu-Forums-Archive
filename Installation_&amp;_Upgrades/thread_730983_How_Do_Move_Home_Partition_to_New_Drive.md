---
title: "How Do Move Home Partition to New Drive?"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by landsg on 2008-03-21
Hi:

I just added a new 320g HD to my system which I intend to use for personal data storage.  I have formatted it using gparted. 

Now, I want to move the /home partition (on hda1) to the new drive (to hdb1).  How do I accomplish this without  losing any data?   See partition table below.  Thanks for your help.



Disk /dev/hda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002e042

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+  83  Linux
/dev/hda2           12002       12188     1502077+   5  Extended
/dev/hda3            2551       12001    75915157+  83  Linux
/dev/hda5           12002       12188     1502046   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009526a

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       38913   312568641   83  Linux

---

### Post by frankos44 on 2008-03-21
System->Administration->Users and Groups
Select properties

Here you can set your home directory to whatever you want.

Make sure that the other drive is automatically mounted at boot time and Ownership / Permissions are correct for the folder on the new drive.

I have never tried this but it should work.

---

### Post by Pumalite on 2008-03-21
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by landsg on 2008-03-21
OK.  I have read the Pyshocat page on the /home partition.  However, this assumes you don't already have a /home partion, which I do.  So, again, how to I move my current home files to the new drive, and then relabel the new drive as the new "/home" partition?

Maybe this is so easy I am making it more difficult than it really is.  Thanks!

---

### Post by wRonG1 on 2008-03-22
I'm watching this thread ! Got the same type question . I formated a separate drive for Ubuntu install with Swap , Ubuntu , and (mistakenly) , user , in ext3 (except swap) . "user" has file names but no data ; remains in "home' directory in Ubuntu with data .
Do I need to reformat "user" partition , rename "home" , and place mount point ? No data to lose . May I then simply copy + paste from the "Ubuntu" partition ? Only got Ubuntu to boot in a dual-boot configuration _today_ - very new !

---


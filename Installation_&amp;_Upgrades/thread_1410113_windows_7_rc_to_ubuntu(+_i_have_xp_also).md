---
title: "windows 7 rc to ubuntu(+ i have xp also)"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by harshswami929 on 2010-02-18
hello guys,

i have acer aspire 4736 laptop - 4gb ddr3 ram, 320gb hd, 2ghz t6400 core2duo processor.

I have windows 7 rc installed with windows xp

Following ntfs partitions
70gb-win 7 os
10gb - xp
70,70,85 other partitions

i am planning to delete win 7 partition n install ubuntu in it, 8gb swap n rest /.

queries 
1. is it necessary to convert these ntfs partitions to fat32(it is said that linux has more robust support for fat32)
2. will my other partitions and xp will get detected automatically
3.is 70gb enough
4. is there anything like ubuntu specially for 64 bit architechture support

I am new in ubuntu land. kindly help me

thank you...

---

### Post by harshswami929 on 2010-02-18
One more query

will i require acer's drivers(webcam, trackpad etc, cause i also have fingerprint sacnner...

---

### Post by Mark Phelps on 2010-02-18
> **harshswami929 said:**
> queries 
1. is it necessary to convert these ntfs partitions to fat32(it is said that linux has more robust support for fat32)
Ubuntu will not install in NTFS or FAT32 partitions.  You will need to install Ubuntu in unallocated space.
> 2. will my other partitions and xp will get detected automatically
Yes, that should happen.  IF the other OS is not detected, after install (presuming you're installing 9.10), open a terminal and run "sudo update-grub" -- and watch as it lists the kernels and OSs it finds.
> 3.is 70gb enough
You can install Ubuntu in a lot less than that -- it's not nearly the space-hog of Vista or Win7.  How much TOTAL space you need will depend on what additional files (video's, music, pictures) you want to store in the Ubuntu filesystem.
> 4. is there anything like ubuntu specially for 64 bit architechture support
Yes, Ubuntu comes in 32-bit and 64-bit versions.

> will i require acer's drivers(webcam, trackpad etc, cause i also have fingerprint sacnner...
You will NOT be able to use the ACER-provided MS Windows drivers for any of the devices you list.  If you want to check these out first, run from the LiveCD and see how well it detects your hardware and installs the correct drivers.  Anything that does not work with the LiveCD is going to range from trivial to impossible to get working later.

---

### Post by harshswami929 on 2010-02-19
thanks a lot mark...

---


---
title: "Boot problem with Win8 + Ubuntu after using easyBCD"
date: 2014-01-03
forum: Installation &amp; Upgrades
---

### Post by augusto.mombach on 2014-01-03
Hi, can you help me to restore my boot?


the problem is this...


Once I had 4 partitions on my HD. 


1. reserved by system

  2. Files NTFS (120 GB)

3. Ubuntu EXT3 (120 GB)

4. Windows NTFS (250 GB)


and my boot used to work (configured by easyBCD)


but  I want more space for files and less for windows, so I split the  Windows partition into 2 (by windows management disk without format the  partition), removed the Ubuntu partition, increased the files partition  and created a new ext3 partition after windows one, became this way...
 
1. reserved by system
2. Files NTFS (250 GB)
3. Windows NTFS (130 GB)
4. Ubuntu EXT3 (100 GB)


but,  when I`ve reconfigured the boot with easyBCD, it started an error 0x00000000098 and  didn`t boot anymore. I've used boot-repair program to reconfigure it and recreating  grub. So now, when I turn on the PC, it starts on grub, and linux works  perfectly, but when I choose windows option it gives me the same error.  The configuration is on [http://paste.ubuntu.com/6683998](http://paste.ubuntu.com/6683998)
 

I tried restore the MBR on windows ([http://paste.ubuntu.com/6684130](http://paste.ubuntu.com/6684130)) and on reserved partition ([http://paste.ubuntu.com/6684178](http://paste.ubuntu.com/6684178)) without success, returning to the first error message. 

If somobody know how to fix the MBR again or how to boot windows 8 with grub it would be really nice..

---


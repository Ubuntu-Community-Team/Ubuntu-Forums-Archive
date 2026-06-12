---
title: "Ubuntu Installation Issue"
date: 2012-01-09
forum: Installation &amp; Upgrades
---

### Post by seeker007 on 2012-01-09
Hello Experts, 
I'm installing Ubuntu Desktop Edn on Acer Travelmate 2400. 
I used to Install 10.10 and it throwed me an error that the memory was not sufficient.
Hence I Upgraded to 2 GB RAM. 
 While I Install I get the following Error 

(initramfs) mount:  mounting /dev/loop0 on //filesystem.squashfs failed: Input/output errror 
Can not mount /dev/loop0 ( Cdrom/casper/filesystem.squashfs) on //filesystem.squashfs 
udevd[75]: worker [204] unexpectedly returned with status 0x0100 

udevd[75]: worker [204] failed while handling '/devices/virtual/block/loop0'

I did run the chkdsk/f ( As mentioned in some other Threads) 

Can some one advise what could have gone wrong 

Thanks

---

### Post by mikewhatever on 2012-01-10
It looks like the problem is either with the CDROM, the CD (defected or bad burn), or with the downloaded ISO. Running chkdsk/f should check the Windows file system alright, but it's irrelevant to any of the above.

Check the ISO integrity: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Re-burn the CD at slow speed.

---

### Post by Mark Phelps on 2012-01-12
Why are you running CHKDSK -- that is only for Windows filesystems!

Does your Acer already have Windows on it?

If so, which version? And, how many partitions are already on your drive?

---


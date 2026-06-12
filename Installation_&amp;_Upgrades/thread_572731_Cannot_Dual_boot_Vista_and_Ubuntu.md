---
title: "Cannot Dual boot Vista and Ubuntu"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by uberlaff on 2007-10-10
Hi everyone...
   I'm having an issue that I cannot find a solution for in the forums.  I've recently had Windows Vista and Ubuntu working dual boot great together using GRUB and one day it just stopped working.  Believe it or not the only change that I made for it to stop working was I upgraded Apple Quicktime in Vista.  Now GRUB doesn't boot.  I've followed many different threads here trying to reinstall GRUB even using a SuperGRUB disk and all have had no effect on the situation.

  Now, I backed up my data and deleted my linux partitions to go with a fresh install of Ubuntu 7.10 beta.  I installed to the partition with the largest continuous free space and still it boots straight to Vista.  Grub will not load even with a fresh install of Ubuntu 7.10.  

  Anyone have any ideas on how to get my system dual booting again?  I really don't want to delete Vista and reinstall it.  It is not a pretty site getting all my programs back on it and configuring it correctly.

Thanks!

---

### Post by gwoodard on 2007-10-10
One, You Used the BETA version of 7.10... Two, Vista probably doesn't like the Quicktime... The list goes on forever... just wait for the "official version" of 7.10

---

### Post by uberlaff on 2007-10-11
My bad, I wasn't clear in the beginning.  I was originally using 7.04 when all this started happening.  It won't install grub over Vista's bootloader.  I found a little program called EasyBCD that allowed me to modify the windows bootloader to dual boot to linux.  

The weird thing is that when I select Ubuntu from that bootloader it takes me to grub.  So I'm assuming that GRUB is not writting to the correct part ot the drive.  I'm going to keep investigating this issue.  

If that clues anyone in on what the issue is let me know!  
Thanks...

---

### Post by Mark Phelps on 2007-10-12
Don't have an explanation for how upgrading QuickTime broke Grub, but from your description of how booting is working now, it sounds like you installed Grub to the Linux boot partition. Thus, when you boot the machine and use EasyBCD to select Linux, it sends you to the first Linux partition, which has Grub in it, and Grub starts.

As to Grub overwriting the Vista boot loader, of course it won't -- because the (new) Vista boot loader (which doesn't use boot.ini or NTLDR) is contained inside the Vista partition.  However, if you install Grub to the MBR, it should then be the default boot loader, and you would then be able to launch either Linux or Vista from Grub.

---


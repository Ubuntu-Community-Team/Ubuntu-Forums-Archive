---
title: "help system recovery!"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by soumo on 2010-05-04
So I've gone and royally screwed my system!

I had a triple boot in order XP, 7, Ubu (Karmic).  In there was also a swap partition, and an NTFS one for storage.

My partition tables had been messed up for a while, but I had a usable system.  Figuring I could do without XP, I tried to format the partition but was unable to using 7's manager or Lucid gparted via usb key.  I figured it was a space issue and foolishly started wiping off almost allthe files in XP from within 7.  Some would not delete (eg. bootmgr).  I then tried to format XP from 7 or shrink the partition -no joy.  I tried using Easeus Partition Manager but it said I needed to do a reboot (presumably it would repartition after doing so).  On reboot I got: bootmgr is missing error and realized my stupid silly mistake!

I had initially set up the tri-boot via easybcd or bcdedit -can't remember which.  File recovery is not a problem thanks to testdisk and Lucid Live, however I'd like to recover without starting from scratch.

Any ideas?  I'm thinking maybe using a windows XP or 7 recovery cd to "fixboot", or dragging and dropping bootmgr to the right place in XP for rebooting.  But before proceeding, I love to get some suggestions.  I don't really care about the ubu partition and was going to install LL over it anyhow. 

-Thanks in advance.

---

### Post by soumo on 2010-05-04
Solved!  I just used ubu LL usb Live to boot in, then went to my cannabalized XP found bootmgr and basicallycopied it back to everywhere I could think of.  

On reboot, it worked!  Now I will figure out how to safely remove XP.  Hope this helps someone else.

---


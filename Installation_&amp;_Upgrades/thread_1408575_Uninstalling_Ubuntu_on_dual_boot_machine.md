---
title: "Uninstalling Ubuntu on dual boot machine"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by IrishCatGod on 2010-02-16
Hi I recently installed Ubuntu w/ dual boot on a Windows 7 machine. I have unfortunately quickly run out of room on my HDD. (I really need to get a new one)... is there a way to uninstall Ubuntu and delete the booter for linux (think it's called grub or something) while keeping my Windows 7 filesystem intact? 
 
I installed Ubuntu 9.10 Desktop 64 edition. 
 
I shrunk the Windows 7 partition to do so. 
 
As far as I know, if I just simply delete the Ubuntu partition, it will ask for the grub(?) loader when I go to boot up again... is there a way around this? 
 
Well think that's about it, if you need more info let me know and thanks in advance.

---

### Post by wilee-nilee on 2010-02-16
You are correct that just removing Ubuntu will leave you possibly unable to boot into W7. If you get no answers here, try here.
[http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by Mark Phelps on 2010-02-16
BEFORE you do anything else, boot into Win7 and use the backup function to create and burn a Win7 Repair CD.  You can then use that CD to restore your Win7 boot capabilities -- and avoid the hassle of having to reinstall anything.

To restore Win7 boot, boot from the CD and select Startup Repair.  Do that three times -- fixes one thing on each pass.

After the third pass, you should be able to boot directly into Win7. 

You can then boot from an Ubuntu LiveCD and use Partition Editor to remove the Ubuntu partition(s).

You should then boot back into Win7 and use the Disk Management utility to extend your Win7 partition to fill the available space.

---


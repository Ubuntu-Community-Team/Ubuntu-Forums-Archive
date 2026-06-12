---
title: "confused"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by stp1974 on 2009-12-10
hi everyone.

i am trying to bring my laptop back to an xp environment.  when i run the xp cd from boot everything seems to start out ok.  however, about 2 or 3 minutes in to the setup i get a blue screen telling me that windows has shut down to avoid causing damage to my computer.  i like the ubuntu, but having too many problems to keep as my operating system.  i want to reinstall xp and maybe run linux on the side somewhere.  

it also tells me that there are no drives installed.  someone told me to use the live ubuntu cd to format the hard drive in NTFS, however i can not find anywhere that allows me to do this.  

this is my drive info : CSI1(0,0,0)(SDA)-250.1 GB ATA WDC WD2500BEVT-2

any help would be hugely appreciated.

thanks

---

### Post by fancypiper on 2009-12-10
[How to Remove Linux and Install Windows XP on Your Computer]("http://support.microsoft.com/kb/314458/EN-US/)

---

### Post by darkod on 2009-12-10
> **stp1974 said:**
> hi everyone.

i am trying to bring my laptop back to an xp environment.  when i run the xp cd from boot everything seems to start out ok.  however, about 2 or 3 minutes in to the setup i get a blue screen telling me that windows has shut down to avoid causing damage to my computer.  i like the ubuntu, but having too many problems to keep as my operating system.  i want to reinstall xp and maybe run linux on the side somewhere.  

it also tells me that there are no drives installed.  someone told me to use the live ubuntu cd to format the hard drive in NTFS, however i can not find anywhere that allows me to do this.  

this is my drive info : CSI1(0,0,0)(SDA)-250.1 GB ATA WDC WD2500BEVT-2

any help would be hugely appreciated.

thanks

You could format as ntfs but it's not needed at all. You can delete all ubuntu partitions from the XP installer and create as many ntfs partitions as you want (depending if you want C:, D: etc in windows).
But I have no answer why your XP install cd would give you blue screen. That's up to XP.
If you stil want to format the drive before trying with XP install cd, boot with ubuntu LiveCD, Try Ubuntu option, and open Gparted (in System-Administration). Your swap partition might be mounted, you will notice keys symbol, if it has you can't delete it. Right click it and select swapoff. For other partitions use Unmount if they are mounted.
You can delete any partition you want with right click Delete. Initially the operations are just scheduled. You need to click on the big green tick mark button in Gparted to execute them.
You are aware that this WILL ERASE YOUR HDD AND DATA right???

After deleting partitions, you can create new ones in the unallocated space, as you wish.

---


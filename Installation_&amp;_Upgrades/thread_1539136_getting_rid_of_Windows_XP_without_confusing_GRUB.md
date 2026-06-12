---
title: "getting rid of Windows XP without confusing GRUB"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by andi99 on 2010-07-26
Hi everybody,

I made the change to linux some month ago and now I  finally want to get rid of my old Windows XP installation. I know how  to remove/change/... partitions with GParted and the like, but I have  one problem: 

The Windows partition is the first primary  partition on the disk. If I remove it and resize the second partition  (with Ubuntu in it)  to fill the space, won't the patition labels be  renumbered (what was 1 becomes 0 and so on)? Will GRUB recognize the  change "automagically" (I read somewhere that newer versions of GRUB  create the boot menu entreis automatically...)?  Or do I have to change  the configuration of GRUB or mtab/fstab/something else manually? 

I  don't want to blow my working Ubuntu installation, that's why I aks  first! ;)  Some googeling unfortunately didn't provide answers. I'm using Ubuntu  10.04 x64. I haven't the exact partition layout here with me but I can  find out and post it this evening if it matters.

Thanks for any  advice!! 
Andi

---

### Post by Lucifer The Dark on 2010-07-26
Once you've removed the Windows Partition running the command "sudo update-grub" in Terminal will sort out Grub & remove the Windows entry from the list.

---

### Post by andi99 on 2010-07-26
Hey, that's easy! :p Thanks a lot! I Think I will try this soon!

---

### Post by mikewhatever on 2010-07-26
The Ubuntu partition might change its number, and if that happens, reinstalling Grub from live cd is the solution.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---


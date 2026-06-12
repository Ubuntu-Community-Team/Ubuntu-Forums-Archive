---
title: "Dual-booting Ubuntu and FreeBSD - just need Grub entry for BSD"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by trilobite on 2007-05-27
Hi all - 

  This should be an easy thing to fix (hopefully!).  I've looked around the forum here and also Googled for info, but most of the stuff is about dual-booting Ubuntu and Windows. 

  Anyway - I've now got a dual-boot system with Ubuntu and FreeBSD 6.2 (just installed that). I made sure during the FreeBSD install that I told it not to touch the MBR, and it hasn't.  All I need to know is the Grub entry that I put into menu.lst so that I can boot into FreeBSD.  I'm fine with doing Grub entries for other Linux distros, but just need a hand with doing one for BSD. 

*** UPDATE - SOLVED! *** 
Hi again all -   
 I've found the entry to put into Grub, and it works perfectly!  Found this while browsing the FreeBSD forum.  
  For future reference, here it is - 

  title  FreeBSD 6.2  
  rootnoverify  (hd0,3) 
  chainloader  +1  

  (  The (hd0,3) is because FreeBSD is on my fourth partition.  ) 
 Anyway, sorry for the noise.....  ;)  
- trilobite

---


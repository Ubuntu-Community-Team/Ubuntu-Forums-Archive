---
title: "Installation kubuntu 12.04 with Wubi"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by San32 on 2012-05-15
Hi,
I would like to have some information.
I got problem before after installing kubuntu 12.04, I cannot boot on kubuntu after the installation.  
I would like to try to install kubuntu with wubi (Windows installer).
I have windows 7 AMD64.
Someone knows if I need to work on my partition before ?  My partitions are NTFS.
Thanks,

---

### Post by jadtech on 2012-05-15
it installs  on windows right on the C drive..

you don't have to do anything to install, it installs like any other window program then boots using dos grub , there is no special partition it sets up a bubble File on the NTFS that acts as Root.disk (virtual partition )  for ubuntu ..

the space is not self growing  though make sure on set up you make the space large enough I found that 50 gb was more then I could use though it will install with 10 or 15 just for test purposes :) 

how ever if full install has gave you issues it may take some tweaking and adjusting to get this going too it could  just work if you can boot from live cd no trouble , the wubi will most likely boot  as well ..

---

### Post by mastablasta on 2012-05-16
if normal install didn't work then wubi won't either. it would be better to troubleshoot the normal install. 
 
what went wrong? what exactly happens? any error messages?
How to get support faster: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by wilee-nilee on 2012-05-16
> **San32 said:**
> Hi,
I would like to have some information.
I got problem before after installing kubuntu 12.04, I cannot boot on kubuntu after the installation.  
I would like to try to install kubuntu with wubi (Windows installer).
I have windows 7 AMD64.
Someone knows if I need to work on my partition before ?  My partitions are NTFS.
Thanks,

Can you describe the failed install on a partition, I suspect we can get you into a standard dual boot. 

As suggested in post 2 kubuntu when installed via wubi is not a partition install, and I believe it is 30 gigs max actually.

---


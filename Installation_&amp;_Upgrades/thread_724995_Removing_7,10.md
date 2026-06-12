---
title: "Removing 7,10"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by Patto77 on 2008-03-15
I've cut my teeth on Gutsy and am now keen to try some other Linux distros.  I'm currently tri-booting xp/Vista and ubuntu.  xp and vista are on my primary Hard drive and ubuntu is on a partition on a secondary hard drive.

To remove gutsy, do I simply delete that partition and recreate it for the new distro or am I going to have trouble with the grub loader?

Is there another way to remove gutsy that won't hurt the mbr?

---

### Post by ugm6hr on 2008-03-15
It depends on where you installed GRUB.

This is probably your best bet: [http://ubuntuforums.org/showpost.php?p=2668386&postcount=14](http://ubuntuforums.org/showpost.php?p=2668386&postcount=14)

Easy BCD will allow you to access future Linux installations.

---

### Post by Pumalite on 2008-03-15
You can install on top of Gutsy. Most distros will just replace the Grub. Others won't. Research a little. If you end up without Grub, you can fix your Windows MBR with Super Grub: 
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Patto77 on 2008-03-15
I installed Ultimate Edition 1.7 straight over the top of the Gutsy installation and so far so good.  

Thanks for the help.

---


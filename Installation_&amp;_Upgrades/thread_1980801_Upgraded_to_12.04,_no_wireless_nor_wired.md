---
title: "Upgraded to 12.04, no wireless nor wired"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by voy108 on 2012-05-15
I upgraded via upgrade manager from 11.10 to 12.04. It seemed to go OK but on  reboot...no wireless nor wired network and cannot revive it. I eventually  booted thru GRUB and tried "previous Linux version" and voila, got the wireless  working.  Now, how can I tell Grub to boot into that version. It is on "previous version"  menu as "generic" not generic-pae.  I would like to "redo" install from  live CD but it wants me to do something about the root directory.  I'm  dual booting into Win 7.  I indicated the large ext4 which is where my Unity is but it  wanted me to do something about "root".  There is 3 ntfs for Win7 and 3 ext4's plus a swap...I tried Puppy Linux also.  Obviously I'm lost. 

I can run  Unity from Grub but have to go thru "Previous Linux versions" and use Generic(no -pae). I tried recovery mode but didn't seem to help.  Also, there was a post about using the  terminal and b43 and went thru that but since wired was not working, it couldn't repair it.

Will reinstall correct this using Live CD?  If so, how do I reinstall/repair.  A little hand-holding here will help.  I'm not a wizard on partitions so...

I have 12.04 LTS and was able to update it(Generic) via wireless.  I have wired network attached but will not work even in this version.  This is on a dual-boot Win7 Acer Aspire One.

---

### Post by zvacet on 2012-05-18
> Now, how can I tell Grub to boot into that version.

With [Startup Manager]("https://help.ubuntu.com/community/StartUpManager")

---

### Post by voy108 on 2012-05-18
Thanks avacet:
Tried to do Startup Manager but could not find it. After further search I came across recommendation to use grub customizer, that 12.04 has eliminated SM.  You have to go thru some gyrations to get it but finally loaded it, It allowed me to re-arrange the grub menu. Now I'm wondering, what is the difference between "generic" and "generic-pae" on the grub startup interface?   

I'm able to boot into Unity and 12.04 and upgrade it but what am I working with? Not knowing the hierarchy of Linux, am I going to have problems later?

Thanks for your help...it got me searching for a new solution to my questions.

---

### Post by voy108 on 2012-05-18
OOPS. S/B zvacet. Sloppy fingers.):P

---


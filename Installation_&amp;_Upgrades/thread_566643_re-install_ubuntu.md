---
title: "re-install ubuntu"
date: 2007-10-03
forum: Installation &amp; Upgrades
---

### Post by Deanb-mmv on 2007-10-03
I decide to install Ubuntu today and did so without consequence.
however i updated my graphics driver as i had read in the forum somewhere and it then loaded without the GUI saying that x-server wasn't working, so i checked the forums (luckily i had vista still on) and tried several fixes of the forums but non have worked so i was wondering how i would re-install Ubuntu, with windows i just pop in the disc and choose to re-install or at least recover the OS but i just pop in the liveCD and it just boots up (which is what i am on now)
so how do i go about re-installing Ubuntu cos it wont let me install over the previous partition i made.
or failing that how do i get rid of it completely?

---

### Post by dabl on 2007-10-03
Make a GParted Live CD, boot that, and format the partition where you previously installed *buntu.  Then you can either install *buntu again, or use it for Windows, or save it for a rainy day.  :lolflag:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by rsambuca on 2007-10-03
I believe gParted is on the liveCD as well.

---

### Post by Deanb-mmv on 2007-10-03
how do i get hold of this gparted thing? i am currently on the live CD cos i wanted to see if i could reinstall from here.

---

### Post by rsambuca on 2007-10-03
You can re-install from the liveCD.  Just select manual partitioning and select the partition that you already have Ubuntu on.

---

### Post by Deanb-mmv on 2007-10-03
I will try that now.

---

### Post by timofthec on 2007-10-28
Guys,

I seem to have exactly the same problem as the OP and have decided to try a re-install because I cannot resolve the problem.  My question is that this was recomended: -

> **rsambuca said:**
> You can re-install from the liveCD.  Just select manual partitioning and select the partition that you already have Ubuntu on.

but, will this work with a dual boot setup?  My pc dual boots xp and ubuntu, therefore, is it as simple as putting the disk in, restarting the pc, formatting the ubuntu partition and re-installing?  What about the Grub menu, will that have to be amended after the install?

Any help for a user of limited ability would be welcome

---

### Post by rsambuca on 2007-10-28
> **timofthec said:**
> Guys,

I seem to have exactly the same problem as the OP and have decided to try a re-install because I cannot resolve the problem.  My question is that this was recomended: -



but, will this work with a dual boot setup?  My pc dual boots xp and ubuntu, therefore, is it as simple as putting the disk in, restarting the pc, formatting the ubuntu partition and re-installing?  What about the Grub menu, will that have to be amended after the install?

Any help for a user of limited ability would be welcome

When you re-install, the grub loader will detect your existing Windows setup and add it to the menu.

---


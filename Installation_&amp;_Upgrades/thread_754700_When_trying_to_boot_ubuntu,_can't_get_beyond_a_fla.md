---
title: "When trying to boot ubuntu, can't get beyond a flashing cursor in the left corner"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by refsland on 2008-04-14
Hello,

I am trying to assemble a dual boot xp/ubuntu 7.10 desktop on a Dell Optiplex 320 machine.  I used the 7.10 iso disk to successfully install ubuntu. It required adding the line HPET=disable to get the live CD up and running.  Now, upon boot up, it appears in the list of available OSes.

When i select Ubuntu, either the recovery or regular option,  the system displays a cursor at the top left corner, but the boot will not commence.  

When looking through the grub commands, root (hd0,2) seems to return, but the system never seems to return from the kernel grub command. Not sure how else to diagnose. XP works properly.

Any ideas??

Thanks

---


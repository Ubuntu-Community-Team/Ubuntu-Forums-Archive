---
title: "Black screen when trying to install on Aspire D250"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by paco_strano on 2010-03-11
Hi guys 

I have a Acer Aspire D250 the new ones that comes with the win 7 starter kit.

When I try to install or just even try to load from the live CD from Ubuntu 9.10 or Ubuntu 9.10 remix the logo come up and screen goes black. I'm using a 4gig Sanddisk cruzer and I formated to fat32.

Is it an option that I need to change into the bios? do you think I really need to use a external DVD to install it?

I tried to find a solution on google but can't find anything

Thanks all =)

---

### Post by presence1960 on 2010-03-11
> **paco_strano said:**
> Hi guys 

I have a Acer Aspire D250 the new ones that comes with the win 7 starter kit.

When I try to install or just even try to load from the live CD from Ubuntu 9.10 or Ubuntu 9.10 remix the logo come up and screen goes black. I'm using a 4gig Sanddisk cruzer and I formated to fat32.

Is it an option that I need to change into the bios? do you think I really need to use a external DVD to install it?

I tried to find a solution on google but can't find anything

Thanks all =)
Booting from a Live ubuntu USB should work. Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso you used prior to creating the bootable USB?

If you can get to the menu screen when you boot select "check disk for defects". If it checks out OK then at the menu screen hit F4 and select safe graphics mode. For more info on this and other boot options see [here]("https://help.ubuntu.com/community/BootOptions").

If all else fails try the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

### Post by paco_strano on 2010-03-11
> **presence1960 said:**
> Booting from a Live ubuntu USB should work. Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso you used prior to creating the bootable USB?

If you can get to the menu screen when you boot select "check disk for defects". If it checks out OK then at the menu screen hit F4 and select safe graphics mode. For more info on this and other boot options see [here]("https://help.ubuntu.com/community/BootOptions").

If all else fails try the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").


Thank for your reply I will try this

---


---
title: "Trying to install ubuntu"
date: 2020-05-14
forum: Installation &amp; Upgrades
---

### Post by azer012 on 2020-05-14
hello all,
Im trying to install ubuntu for the first time, along with windows.I liked the idea of the dual boot till I can decide.
1- I did create the free space.
2- Im ready with the pin drive and booted from it.
3- the thing is when I start the setup it doesnt give me the option of installing aside with windows 10 , knowing that secured boot is disabled!!!
can someone help please as I really need to try it.

---

### Post by CatKiller on 2020-05-14
> **azer012 said:**
> 3- the thing is when I start the setup it doesnt give me the option of installing aside with windows 10 , knowing that secured boot is disabled!!!


You need to turn off Fast Startup in Windows for its partitions to be accessible; otherwise it just hibernates rather than shutting down and leaves the drives marked dirty. 

You also need the drives to be accessed by AHCI rather than something else like RAID, which is a UEFI setting. You may need to install a driver in Windows to be able to use Windows with AHCI.

---

### Post by ActionParsnip on 2020-05-15
Be sure to free up space on your disk (if required) using Windows disk manager. This will make free space you can install Ubuntu to. If you planned your partitions then this can be ignored but Ubuntu needs allocated space to install itself to

---


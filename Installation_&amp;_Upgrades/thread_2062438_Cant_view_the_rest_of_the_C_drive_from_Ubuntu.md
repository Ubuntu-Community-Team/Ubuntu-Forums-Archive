---
title: "Cant view the rest of the C drive from Ubuntu"
date: 2012-09-24
forum: Installation &amp; Upgrades
---

### Post by Herbalist on 2012-09-24
Hey guys,i just installed ubuntu 12.04 through wubi from windows 7 and i choose the local disk (C) as the hard drive to install ubuntu on,the installation was easy and straight forward but when im on ubuntu i can only view the local disk (D) and part of the (c) drive where ubuntu was assigned to be installed on...
any ideas on how i can access the rest of the drive ?
Regards..

---

### Post by coffeecat on 2012-09-25
Open a file browser, click on "File System" in the left pane, and then open the "host" folder which you will see in the main pane. That's your C: partition.

Be wary when accessing your C: drive. Ubuntu shows files which are hidden in Windows - if you accidentally delete or move any, you could make Windows unbootable. Also, if you are in the habit of hibernating Windows 7 and you then write to your C: partition from Ubuntu, you will lose any files you wrote from Ubuntu. When waking up from hibernation, Windows 7 (and 8) will restore the filesystem to its pre-hibernation state.

---

### Post by darkod on 2012-09-25
And when you are sure you like ubuntu i suggest you start thinking about a proper dual boot on its own partition, not wubi. Don't forget, wubi was developed only as a short try, if you try to use it as long term install sometimes things start breaking up. :)

The goal should be a totally separated dual boot, not wubi inside windows.

---

### Post by Herbalist on 2012-09-25
Thanks a bunch coffeecat,and @darkod the only reason i installed ubuntu through wubi is that im to lazy to get a disc to burn the iso on :P

---


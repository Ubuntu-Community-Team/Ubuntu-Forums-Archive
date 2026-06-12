---
title: "Ubuntu has destroyed my Windows"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by andrewcow on 2011-01-10
So I have been searching for hours and cant find anything that has worked. So I installed ubuntu on my windows 7 machine and it works fine. The problem comes when I try to boot windows. The boot manager(ubuntu one) only detects Ubuntu. I don't think the windows boot loader is broken, I just cant get to it. 

I installed Ubuntu on a partition on my windows HDD that I made in windows. I have tried reinstalling grub2 but no luck. The worst thing is Ubuntu won't mount the windows partition. I have tried every way I can, even using NTFS-3G. What should I do??
I have been trying everything to no avail. Please help
AndrewCow

---

### Post by Rubi1200 on 2011-01-10
Hi,
you need to get hold of a LiveCD and boot the computer choosing to try not install.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here so we can take a look at the current state of your system.

Thanks.

---

### Post by kansasnoob on 2011-01-10
> **Rubi1200 said:**
> Hi,
you need to get hold of a LiveCD and boot the computer choosing to try not install.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here so we can take a look at the current state of your system.

Thanks.

+1! We need to see that output to understand what's going on.

---

### Post by cgroza on 2011-01-10
For the NTFS partition problem, install ntfs-config from Ubuntu Software Center or if you like it more fast, with this command:

```
sudo apt-get install ntfs-config
```

That utility should show up somewhere in the menu and use that to configure you NTFS partitions.

When I installed ntfs-config, I had a problem with it and I solved by installing hal.
If this happens to you just run:
```

sudo apt-get install hal
```

---


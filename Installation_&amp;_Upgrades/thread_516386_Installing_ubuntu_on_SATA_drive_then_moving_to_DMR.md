---
title: "Installing ubuntu on SATA drive then moving to DMRAID set"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by DJMatty on 2007-08-03
Hi

Last night I decided to have another go at getting Ubuntu running from my raid 0 drives, rather than the single sata drive it's running on now.

As a test I am only using a single partition for boot, root and home, with an additional partition for swap.

So I did the following steps:

1 ) Install a new copy of ubuntu on my single drive
2 ) Used envy to install the nvidia gfx card drivers
3 ) I thought I had installed dmraid here but it turns out I hadn't
4 ) Booted to the live-cd
5 ) installed dmraid in the live environment
6 ) partitioned and formatted the raid drive
7 ) mounted the root of the new install as /source
8 ) mounted the root of the raid partition as /target
9 ) issued 'cp -rp /source/* /target/'
10) modified /target/etc/fstab to point at the /dev/mapper/nvidia_xxx partitions
11) chrooted to /target
12) discovered here that the partitions were missing, so installed dmraid
13) set up grub, using hd1 and the correct partitions
14) modified /boot/grub/menu.lst to contain correct settings for root etc.

This all seemeds to go ok, and surprisingly I got the grub settings right, as it booted to the orange ubuntu logo with the progress bar, however, that's as far as it gets. If I boot to recovery mode I see it start to boot, but then stops quite early on and just does nothing.

I do remember reading a how-to that describes the process that I was trying to do, but couldn't find it. I have a few concerns:

1) Did I get the cp options right? as I wonder if I missed any files like symbolic links?
2) Would installing dmraid after I had chrooted to /target install it correctly? Would I be better re-doing it and installing dmraid in the main install?
3) How do I go about diagnosing the issue with the boot?

Any help or pointers in the right direction would be appreciated!

Thanks

Matt

---


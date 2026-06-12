---
title: "Dual boot 7.04 and 7.10 with one /boot"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by eternicode on 2008-01-05
I've recently repartitioned my hard drive to have one /home, one /, and one /boot partition for my main Kubuntu Feisty install.  I've read about a lot of issues with Gutsy (it may actually be the issues normal to the current mainstream distro, but this is my perception :p ), so I decided to also partition off 4GB ext3 to install Gusty's / on.

I figure I'll just tell Gutsy to mount my current /home, but it will surely require me to format the /boot partition before it will use it.  Not to mention overwriting my current grub.

If at all possible, I'd just as soon NOT overwrite my current GRUB, and just add Gutsy's kernels to Feisty's grub boot list.  But how would I go about having Gutsy mount my /boot without having to format it?  Perhaps tell it to leave /boot on the root partition for the install, then transfer the kernel images, modify the menu.lst, and edit the fstab after the fact?

Thanks for any advice; if more info is needed, let me know :)

---

### Post by confused57 on 2008-01-06
There are instructions here for sharing a /boot partition:
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

---


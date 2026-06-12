---
title: "installing"
date: 2016-10-24
forum: Installation &amp; Upgrades
---

### Post by marvinB on 2016-10-24
I added a hard drive to my computer now when I install ubuntu 16.04 it installs a raid whick is what I want
but it crashes cannot install grub /dev/sda ask mje to pick a different location with a list but non of them work 
try to select install without boot loaded and it won't budge what to do

---

### Post by ian-weisser on 2016-10-24
Hardware RAID or Software RAID?
I do not recall a RAID option in the Ubuntu Installer, so perhaps there are a few intermediate steps you have left out? We need to know those.

When I used to do RAID for data, I kept the bootable system on a separate, non-RAID drive to avoid precisely this kind of problem.

---

### Post by marvinB on 2016-10-24
when I install a hardware raid it turns off my dvd so I did a software raid
how do you set up the boot loader on a non raid drive?
thanks so much for the help
new to linux and I love it

---

### Post by ian-weisser on 2016-10-24
> **marvinB said:**
> how do you set up the boot loader on a non raid drive?
The easy way is to unmount/unplug the RAID drives before installing...or before running grub-install if you already have Ubuntu installed on a non-RAID drive. 
GRUB won't try to install to a drive that it is unaware of.

---


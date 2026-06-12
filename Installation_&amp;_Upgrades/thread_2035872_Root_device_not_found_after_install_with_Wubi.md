---
title: "Root device not found after install with Wubi"
date: 2012-07-31
forum: Installation &amp; Upgrades
---

### Post by tommyk19 on 2012-07-31
Hi everyone,

I'm quite new to linux and this forum as well so please be patient with me.

I have dusted off recently my old Acer Aspire One (KAV60)just to play with it a little and because I'm more and more being upset by Windows issues I've decided to learn little bit about Ubuntu.

Because my netbook run WinXP and I don't have external CD-drive at the moment I've decided to install Ubuntu 12.04 along with WinXp using WUBI installer.

I got drive split in to 2 partitions and Win is installed on first partition so I've installed Ubuntu on 2nd just to avoid any possible issues.

Installation went OK but after rebooting my pc and choosing to boot in to Ubuntu it came up with these:

Gave up waiting for root device. Common problems
- Boot args (cat/proc/cmdline)
-check rootdelay= (did the system wait long enough?)
-check root= (did the system wait for the right device?)
-Missing modules (cat/proc/modules, ls/dev)
ALERT! /dev/disk/by-uuid/A6904D8C904D6441 does not exist. Dropping to a shell!

I've seen multiple threads on this forum with similar error but majority of them suggest to run live cd which I can't at the moment.

Any tips or sugestions?


p.s: i've tried uninstall and install ubuntu couple times everytime with same result 

thanks

---

### Post by irv on 2012-07-31
Here is what I would suggest. I'm not a big fan of Wubi. What Wubi does is creates a image file of the OS and runs along with Windows. I tried it once along time ago. Here is what I would do. I would follow the instructions found [HERE:]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")
This will create a USB stick so you can install Ubuntu on your computer. Install it on the space you created for it.
If you wouldn't have created this space you could have installed it side by side and just let the install take care of this for you.

If you haven't use this computer for awhile you could just use the whole Hard Drive and run just Ubuntu. The choice is your.

---

### Post by tommyk19 on 2012-08-01
Thanks a lot for quick reply. I will try that later and will let you know.

I know that around 2 years ago I was installing Ubuntu from a scratch on similar netbook from USB and it did work fine.

---

### Post by irv on 2012-08-01
> **tommyk19 said:**
> Thanks a lot for quick reply. I will try that later and will let you know.

I know that around 2 years ago I was installing Ubuntu from a scratch on similar netbook from USB and it did work fine.

I don't have a Netbook, but I read somewhere that the Netbook need to be booted from one of the USB ports. I am not sure if it is the left or right?

---


---
title: "Chrubuntu no longer boots after adding a 4GB linux swap partition in gparted?"
date: 2016-10-28
forum: Installation &amp; Upgrades
---

### Post by wulgulmerang on 2016-10-28
Dear Ubuntu,

First of all, apologies if this thread has multiple related issues.

I recently installed ChrUbuntu to an external USB stick using this thread on Reddit:
[https://www.reddit.com/r/chrubuntu/comments/4w3f0x/guide_install_chrubuntu_on_tegra_k1_chromebook/](https://www.reddit.com/r/chrubuntu/comments/4w3f0x/guide_install_chrubuntu_on_tegra_k1_chromebook/) 

The machine is a HP Chromebook 14 G3 (Tegra K1 nyan_blaze) and the GPU acceleration works very well. 
(60fps on some webgl benchmarks)

There were a few bugs in the script, so here's an updated version, where you can edit the header for your own hostname, username and
password. 
[https://goo.gl/qfW2Ry](https://goo.gl/qfW2Ry)

After installation I booted into ChrUbuntu using Ctrl-U on the Chromebook developer screen.

After tweaking the user-interface,
I noticed in gparted that the 32GB USB stick had 4GB left at the end of the disk.  Quite recklessly :) I decided to simply
add a 4GB swap partition using gparted to see if that made things faster.

Unfortunately, after doing this, ChrUbuntu would no longer boot.

(1) Is it possible to fix ChrUbuntu and get it booting up again (without having to reinstall)?
(2) Is it possible to add a 4GB linux swap partition without breaking ChrUbuntu, and therefore make the system faster?

Best Wishes, wulgulmerang.
 
**PS: I tried signing KERN-A using the vbutil_kernel snippet but to not avail**

[B]PPS: I've reinstalled and all is well

PPPS: Apparently ChromeOS only supports ZRAM so no linux swap partitions[/B]

---


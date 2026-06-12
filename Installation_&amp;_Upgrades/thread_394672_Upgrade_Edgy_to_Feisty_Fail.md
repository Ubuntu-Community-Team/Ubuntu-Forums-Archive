---
title: "Upgrade Edgy to Feisty Fail"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by mjs on 2007-03-27
Hi Guys,

I have tried to upgrade my edgy Ubuntu, all apparently works fine, however the system doesn't start anymore.

The message showed is:

"
Please append a correct "root=" boot option
Kernel panic: VFS: Unable to mount root fs on unknown-block(0,0)"

I already boot using a live CD and all the files and partitions are ok.

My system is in the /dev/hda1 but when I go to the grub has a reference to (hd0,2). I even tried to try to change it to (hd0,0) but grub still can't find the Filesystem to boot. For better explain:

/dev/hda1 - /
/dev/hda3 - /boot
/dev/hda5 - /home

Can somebody help me?

Thanks in Advance

---


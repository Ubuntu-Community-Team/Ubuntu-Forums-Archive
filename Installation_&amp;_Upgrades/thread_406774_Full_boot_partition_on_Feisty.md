---
title: "Full boot partition on Feisty"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by idumych on 2007-04-11
I installed Feisty beta 1 a couple of weeks ago with a 50 MB boot partition. This partion is now full, and I can't install updates anymore because of this. How can I safely migrate to a boot folder on my root partion without having to re-install?

---

### Post by bollix47 on 2007-04-11
I have the current kernel (-14) and the previous (-13) in my boot directory and it's taking around 33meg.  Do you have some older kernels that you can remove via synaptic or apt-get?

---

### Post by kidders on 2007-04-11
Hi there,

50MB should be easily big enough for a /boot partition. The most straightforward thing to do might be to remove some old kernels that you have no intention of using any more. (**Edit:** bollix47 beat me to this suggestion!) Since you've gone to the trouble of creating a /boot partition, you might as well keep it ... rather than throwing away the advantages it gives you.

If you *do* still want to remove it though, it's relatively simple to do...[LIST=1]
[*]**umount /boot** (if it's mounted ... which it _shouldn't_ be).
[*]**mkdir /mnt/goodbye ; mount /dev/whatever /mnt/goodbye**.
[*]Then maybe **cp -dpR /mnt/goodbye/* /boot**.
[*]Then, you should revise your **/boot/grub** so no attempt is made to use the /boot partition.
[*]If you're not sure how to tell what's what, renaming (rather than deleting outright) everything in /mnt/goodbye might be a good idea, so you can be sure the files won't be used. Perhaps something like **find /mnt/goodbye -exec mv {} {}.old \;** would work.
[*]Don't forget to remove the /boot **/etc/fstab** entry.
[*]After a successful reboot, open **cfdisk**, **gparted**, etc. and remove the 50MB partition.[/LIST]

---

### Post by idumych on 2007-04-11
thanks for the help, I'll try it when I get home from work and let you know how it goes.

---

### Post by rumil on 2007-04-11
My 2 cents:
I also use separate /boot partition (100MB) and I was also very surprised when recently it got full. For me it was backup initrd images which took a lot of space. You can remove them: ```
sudo rm /boot/initrd*.bak
```
Agreed with kidders that /boot shouldn't be mounted during normal system usage, however dpkg doesn't seem to try to mount it on kernel update :(
In my case I need to use separate /boot, otherwise resuming from suspend takes forever.

---


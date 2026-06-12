---
title: "Ubuntu 8.04 not booting"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by khalidaziz on 2008-05-04
Kernel panic - not syncing: VFS: unable to mount root on unknown-block(0,0) 

I keep getting this error when booting. I'm a complete noob and have no idea how to fix it. From what I've read on the forums, I have to run update-grub. How do I do that directly from the GRUB menu. Any help would be appreciated!

---

### Post by fixitdude on 2008-05-04
I'm not sure but I think you can boot the live CD and then try to finish your upgrade, it should fix the grub problem. Someone else might correct me, I am just giving you a direction.

The command to do a reinstall of some package:
sudo apt-get install --reinstall NAME-OF-PACKAGE-HERE

But since you are running from live CD that may not work.

Someone else mentioned uninstalling the kernel using apt-get and then reinstalling it to have it fix grub, but I think the above command would also work if you know the exact name of the kernel version you want to reinstall.

---

### Post by khalidaziz on 2008-05-04
I don't have the 8.04 live CD, I installed Gutsy and updated from there.

---


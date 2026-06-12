---
title: "Install from USB stick can't find install media"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by bean1975 on 2007-04-28
So I got as far running the installer from the stick, I switch to another TTY, I try to mount /dev/sdc1 (dmesg tells me that's my stick) and mount /dev/sdc1 /cdrom says Invalid argument. Tried -t fat , tried /mnt, no dice.

Here's how I got to this point I downloaded the alternate installer, loop-mounted it, copied all files to stick, ran syslinux -f, ran install-mbr .

---

### Post by bean1975 on 2007-04-30
You see I forgot to subscribe to this thread and when trying to find my post, I found [http://ubuntuforums.org/showpost.php?p=1694569&postcount=3](http://ubuntuforums.org/showpost.php?p=1694569&postcount=3) this. Which actually helps. There is no FAT module in the Feisty alternative install initrd. Thanks to myself :D I can change the initrd... :lolflag:

---


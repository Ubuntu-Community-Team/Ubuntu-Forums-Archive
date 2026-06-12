---
title: "[SOLVED] How do I redirect GRUB to a new configuration file?"
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by sab0403 on 2007-07-16
Okay... I've searched the forums but I can't seem to find any info on this. So here it goes...

As you know, GRUB looks for a configuration file as soon as it loads. Since I have two different distros installed it's now looking for this configuration file on the /boot/grub directory of the partition of my second distro (which is in sda4). I'd like to change this so GRUB looks for this config file on another partition (so that the boot loader isn't disturbed when/if I erase any of the distros/partitions). So how do I do this? I read the manual for GRUB but it only addresses this point when you're installing GRUB, not after it's installed.

Thanks in advance.

---

### Post by Pumalite on 2007-07-16
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by sab0403 on 2007-07-16
So then, it involves (re)installing GRUB... hmm...

Oh well. I hoped it was somehow editable without actually reinstalling, but this is ok.

Thanks!! :popcorn:

---


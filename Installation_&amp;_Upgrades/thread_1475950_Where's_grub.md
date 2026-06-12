---
title: "Where's grub?"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by ImageAcoustique on 2010-05-07
Hi,
I recently installed Ubuntu 10.04 on my system. The disk is split in two partitions, on the other one there's Ubuntu 9.04. They share /home. 
I can't manage to change /boot/grub/menu.lst, as ... there isn't.
Where did it go? Where is the editable file?
Thanks.

---

### Post by kansasnoob on 2010-05-07
Lucid (10.04) has grub2, just try running this command:

```
sudo update-grub
```

That should find your Jaunty.

Lot's more about grub2:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by ajgreeny on 2010-05-07
Once you get used to grub2 it is so much better than legacy grub.

Any changes made to any of the OSs on your machine will be found by that update-grub command so you do not need  to mess around making manual edits to anything any more.

It took a while for me to understand what was going on, but now I love it!

---

### Post by oldfred on 2010-05-07
I agree with ajgreeny. It took a bit to get used to some new as it was a large change, but it offers a lot of flexibility.

 GRUB 2 has three main parts:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts. And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Already posted above:
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
drs305's hack to get hidden timeout to work:
[http://ubuntuforums.org/showthread.php?t=1319672](http://ubuntuforums.org/showthread.php?t=1319672)

---

### Post by GameDog(A) on 2010-05-07
I'll have to try this when I get home.  I've been having problems too.

---


---
title: "How to restore GRUB in a /boot partition?"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by narcisgarcia on 2010-02-06
I've read the rescue methods for reinstalling GRUB2 in this page:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

But I have damaged the GRUB2 configuration in a computer with an independent partition for /boot because there is a software RAID configured.

Then I cannot mount the root of the installed Ubuntu, because the root (/) is in the RAID, and only the /boot is outside in a traditional partition.

Which is the procedure to reinstall GRUB2 with a Live-CD, and having only easy access to the /boot of the hard disk?

---

### Post by darkod on 2010-02-06
I think you would need to do this first (in live desktop):
If you boot up the ubuntu desktop live CD and need to access your raid,  then you will need to install mdadm if you want to access any software  raid arrays:


```
sudo apt-get update
sudo apt-get install mdadm
```

quote from here:
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

If that allows you to see the root partition in the array, just follow the standard procedure:

1. Mount root
2. Mount /boot (because it's separate you have to do this)
3. Reinstall grub to the MBR

It should work.

---


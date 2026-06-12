---
title: "Ubuntu's good...it's time to remove suse 11....but how?"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by thinkdigit on 2008-09-25
Well...I got to partition the disk and installed XP, Ubuntu as well as Suse. The latter is buggy and I keep getting internal errors. I found it no superior than ubuntu with the little experience that I have. Nonetheless, I want to get rid of it.

I have three partitions on my 40 GB (~37 GB) hard disk, 28 for XP, 9 for ubuntu, 9 for suse and remaining for swap. After installing suse, there have been changes in boot loader. I had installed XP, ubuntu and Suse...in that order.

On booting, I get a menu with boot options for suse, ubuntu and windows. If I select ubuntu, i get another menu, three for ubuntu and one for xp.

Now, I want to "uninstall" suse and merge that 9 GB with partition where ubutu is installed. How can I do that without damaging the boot loader and the ubuntu installation?

---

### Post by Elfy on 2008-09-25
It is likely that suse installed it's bootloader so removing the partition will cause a boot problem. Tha can easily be dealt with using the [livecd]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick Start")

You can also use the livecd to accomplish the partition resize, so in order

Use the partition editor on the livecd - system >admin menu to delete the suse partition, then you should be able to resize the ubuntu partition. Before you do that turn off the swap otherwise you will not be able to work on the partitions

```
sudo swapoff -a
```

Once you have resized the ubuntu partition, use the above link to reinstall grub for ubuntu.

---


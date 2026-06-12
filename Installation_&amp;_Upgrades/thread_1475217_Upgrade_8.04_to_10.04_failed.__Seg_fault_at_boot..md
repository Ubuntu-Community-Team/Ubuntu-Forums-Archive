---
title: "Upgrade 8.04 to 10.04 failed.  Seg fault at boot."
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by kroxic on 2010-05-06
I followed the instructions here [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

There were a few failed or strange items while updating. The only one I can remember off the top of my head is mysql so I didnt think much of it.  The update stopped at a blinking cursor and I hit enter and I was back to command line.  The desktop looked different and everything.  I was not asked to reboot.  everything I normally use was functioning.  I had to reboot the server this morning after last nights update and I land at a (initramfs) prompt with this message at the top.  There is a bit more info after it but this if needed but I am typing from memory ATM.

EDIT:  forgot to add, when I go to boot options in grub it shows 8.04 and not 10.04
```

mount: mouting none on /dev failed: no such device
udevd[937]:error getting socket :invalid argument

error initializing netlink socket
udevd[937]: error initializing netlink socket

libudev: udev_monitor_new_from_netlink: error getting socket: invalid argument
segmentation fault

```

---

### Post by quixote on 2010-05-08
Unfortunately, segmentation faults are double-plus Not Good.  Boot with a liveCD, and mount the partition that has your data on it.  Back that up elsewhere.  You could also back up your home partition, because then your settings and config files will be saved.

What happened was the upgrade went wrong when you got just the blinking cursor.  The system still worked because it was still running as Hardy.  Using it afterward instead of fixing the upgrade probably didn't help matters.  (It's a good idea not to do that in future.)  Once you rebooted, it tried to re-access the system files, but they'd been corrupted by the bad upgrade.

The simplest thing to do, if possible, is a clean install rather than trying to fix whatever mess the upgrade created.  If you haven't before, use a separate home partition for your new install.  

Can you boot into a recovery console? Or is that hosed too?  If the latter, I think a clean install will be the only option.  :(

Sorry to be the bearer of bad tidings!

---

### Post by kansasnoob on 2010-05-08
I have been able to rescue a few failed upgrades using a chroot, basic info about the chroot process:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

A couple of examples:

[http://ubuntuforums.org/showthread.php?t=1471507](http://ubuntuforums.org/showthread.php?t=1471507)

[http://ubuntuforums.org/showthread.php?t=1471183&page=3](http://ubuntuforums.org/showthread.php?t=1471183&page=3)

Each install is different though.

---


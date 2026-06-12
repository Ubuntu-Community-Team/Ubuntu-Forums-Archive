---
title: "Install broke everything"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by Choragos on 2011-04-20
Hello.  I just tried to install Kubuntu on my wife's computer.  She is running Vista 64.  I installed a new HDD (1TB), and ran the Kubuntu 10.04 live CD.  The hard drive was not initialized prior to installation.  I had three options: install the systems next to each other (both on sda), install kubuntu to a whole drive (which crashed the install choosing sdb), and define partitions manually.  OK, so I boldly stepped forth to define them manually.

sdb1 was a ext4 system, using 800 GB, mount point at /.  sdb5 was a 35 gb or something swap.  I left the rest free.  Last step before install, I checked the advanced, and it told me that the bootloader (which I presume to be grub) was to be installed on sda.  OK, great.  We went forth with apparent success.  On reboot, I get the following problems:

The computer boots to what is sda.  I get
error: no such device: 1c326...etc.
and it enters grub rescue> which I have no idea how to use.  If I try to force it to boot to sdb, it locks up completely.  What can I do to (a) return everything to how it was before so my wife doesn't kick me in the netherregions, or (b) fix my installation.  I'd love to give you more information but I can't get past the boot screen...

---

### Post by Choragos on 2011-04-20
More information:

I can run the live CD and have a look at the drives.  Drive OS (windows, or sda) still has everything there and is great.  sdb appears to have a linux file system installed on it.  So it appears something is messed up with the grub config, but I don't know enough to fix it! 

Thanks all.

---

### Post by malangaman on 2011-04-20
I recommend you take a look at these links:


[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?p=7584483](http://ubuntuforums.org/showthread.php?p=7584483)

---

### Post by Choragos on 2011-04-20
Thanks!  I don't know why but I find grub so complicated.

Reinstalling grub on sdb worked by using the following link:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

The issue was that somehow the uuid wasn't working.  Grub seemed to be fine, but referencing sdb1 by it's uuid wasn't getting the job done.  Changing it to /media/disk instead of /media/1c....... fixed it.

Thank you.

---


---
title: "No hard drive selection in ubuntu installation, trying to install on an HP a6700y."
date: 2013-04-11
forum: Installation &amp; Upgrades
---

### Post by Hambooger on 2013-04-11
I want to install Ubuntu on a partition I made, C:\ is the original HP installation, whereas my new partition (H:\) is 120GB. The ubuntu installer, when I click "Install ubuntu" installs the files to my Usb drive. Why is this? I want it to install to my partition. I get no screen that asks me where I want to install it.

I used the installer from linuxliveusb (I won't link just in case it's against forum rules). The USB in question is 950MB.

Thanks in advance for the help.

---

### Post by Mark Phelps on 2013-04-11
If this PC was running Win7 and you used the Win7 disk management utility to create the new partition, it's very likely you forced the creation of a Dynamic Disk -- because you pushed the primary partition count over the maximum of 4. Look in Disk Management and see what is there -- and report back on that.

---

### Post by darkod on 2013-04-12
The most probable reason is because using the auto install method it tries to use the largest available unallocated space present on any disk in the machine.

Since you made the 120GB partition as ntfs from windows, it's useless for the installer. Linux doesn't install on ntfs, DO NOT create partitions for linux from windows. The only thing you need to do from win7/win8 is to shrink the windows partition using Disk Management, if you need some unallocated space to install ubuntu.

Boot windows and delete the 120GB ntfs partition. Leave the space as unallocated.

Try the ubuntu installer again.

---


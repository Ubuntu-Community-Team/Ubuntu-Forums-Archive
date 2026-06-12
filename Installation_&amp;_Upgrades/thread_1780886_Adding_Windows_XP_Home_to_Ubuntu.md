---
title: "Adding Windows XP Home to Ubuntu"
date: 2011-06-12
forum: Installation &amp; Upgrades
---

### Post by Shadow Warrior on 2011-06-12
I have a semi-stable installation on my Dell Dimension 2350 of Ubuntu which I'd kinda like to keep. I'm accustomed to the process of adding a 2nd OS to a hard drive (computer) with a Windows based machine (I can literally do this in my sleep). It just so happens that I have 2 Installations of Ubuntu installed on a single hard drive in 2 different partitions. When I boot to the Windows XP Home CD, it does recognize the partitions created by Linux; but, cannot identify them.

Is there a tool that can install on the Ubuntu I want to keep that will allow me to format the partition I want to use for XP Home that the XP Home Install Disk will recognize both as a location it can install to and a boot loader will present me the of option of booting to Linux or XP?

---

### Post by sanderd17 on 2011-06-12
You can use Gparted to format a partition, if you format it to NTFS, windows will be able to read it.

You can only format partitions that are not mounted, so you might need to use a live CD if you can't do it from the current installation.

Once XP is installed, you won't be able to boot Linux, you will need to boot a live CD first and run the grub-install script to get grub back.

Off coarse, you could also install a virtual xp inside Ubuntu (I don't know how much you want to use xp, but for occasional use, this is excellent)

---

### Post by oldfred on 2011-06-12
+1 on sanderd17's suggestions.

The NTFS partition you create has to be a primary partition and have the boot flag for the XP installer to see it.

Depending on version of Ubuntu you may have grub or grub2. So not mix up the reinstall instructions as they are different and using the wrong one makes repair more difficult.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by geoff07 on 2011-06-12
My suggestion would be to install Oracle Virtualbox (free) to create a virtual machine and install XP inside that. I use it everyday on my desktop and it works very well and is rock solid. That way you don't have any messing with GRUB and you can run both systems in parallel at the same time.  On a double-header machine it is indistinguishable from having two separate machines.

---


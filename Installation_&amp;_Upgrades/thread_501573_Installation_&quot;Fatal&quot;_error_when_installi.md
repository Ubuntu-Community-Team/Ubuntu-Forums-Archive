---
title: "Installation &quot;Fatal&quot; error when installing bootloader"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by runemaster on 2007-07-15
I am installing the 64 bit verison of Ubuntu on my Sager 9260 laptop (Core 2 Duo E67 00), not on the main drive though but on an external one. I keep getting a fatal error when I try to install GRUB, LILO gives me the same error. I tried using the alternate CD and the main CD to install. On the live CD it gave me an error about some mount point on the freeagent external HDD (which I have 1 partition for my main os to use and rest is partitioned into ext3 and swap for Ubuntu. I have no idea what to do, is there a way to manualy install the bootloader?

---

### Post by anti-user on 2007-07-26
i had the same problem with installing GRUB in the installation process of ubuntu.
then i realized GRUB has support for many filesystems but not for ext3. i was using an ext3 formatted partition for the root filesystem, so i thought that might be the problem.
next i tried reiserFS, but then the installation hang at 15% at the point of 'scanning filesystems' or something.
then i tried the ext2 filesystem for the root partition, and everything worked fine!

good luck.

---

### Post by dabl on 2007-07-26
Trying to boot from a connected external USB drive is a tricky proposition, due to the dynamic numbering of USB devices.  Here's a tutorial from Kubuntu forum that covers the subject pretty well:

[http://kubuntuforums.net/forums/index.php?topic=3081748.0](http://kubuntuforums.net/forums/index.php?topic=3081748.0)

:)

---

### Post by logos34 on 2007-07-26
> **runemaster said:**
> I am installing the 64 bit verison of Ubuntu on my Sager 9260 laptop (Core 2 Duo E67 00), not on the main drive though but on an external one. I keep getting a fatal error when I try to install GRUB, LILO gives me the same error. I tried using the alternate CD and the main CD to install. On the live CD it gave me an error about some mount point on the freeagent external HDD (which I have 1 partition for my main os to use and rest is partitioned into ext3 and swap for Ubuntu. I have no idea what to do, is there a way to manualy install the bootloader?

I'd recommend using the alternate CD but when you get to the grub part, choose NOT to install it.  You can then [use the livecd and attempt to manually install it]("http://ubuntuforums.org/showthread.php?t=224351&highlight=catlett+grub"), but I'm not sure that's going to work if all the other installs failed.  'Fatal error' is not as dire as it sounds--I get it all the time on the live cd installs when I override the default grub location and leave it blank, although that occasionally does something to mess up the existing bootloader on the MBR so that I have to boot the live cd once more after install to restore grub manually.  Not sure what's causing this. Make sure you are creating a root (type ext3) partition mounting at '/' and a linux swap (type 'swap') mounting at /swap.

---


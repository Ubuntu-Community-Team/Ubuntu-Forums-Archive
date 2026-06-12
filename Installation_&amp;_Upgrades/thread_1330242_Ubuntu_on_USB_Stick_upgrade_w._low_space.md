---
title: "Ubuntu on USB Stick upgrade w. low space?"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by Flavian on 2009-11-18
Hi there.

I've got the following problem.
I have a 16GB USB Key w. 2 partitions on it.
1) 4 GB root partition = ext2
2) 12 GB Data partition = fat32

Because of space issues the root partition is quiet full. (Obviously)
Since ubuntu downloads ALL the installation data onto the root partition I won't be able to upgrade.

Is there any way of downloading the Data to the Fat32 partition into a specific folder and install from there?

I've like 300 MB left on the root partition.

Thanks for any advice.
Flo
Ps: Don't want to install from scratch, because I would have to configure Evolution again (which was a pain) and install the other progs I already installed and configured.

---

### Post by phillw on 2009-11-18
That's a pretty small partition ....

try apt-get autoclean & autoremove on the ubuntu area, it should clear some room up for you.

[http://ubuntuforums.org/showthread.php?t=394952](http://ubuntuforums.org/showthread.php?t=394952)

Regards,

Phill.

---

### Post by phillw on 2009-11-18
If you have sufficient room on your FAT area, you can download the iso image of the ALTERNATIVE image there and follow these instructions.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Regards,

Phill.

---

### Post by darkod on 2009-11-18
Using Gparted to shrink/expand partitions should also work. But you can not use it from within that installation, the drive has to be unmounted. And as with any shrink/expand tool, I guess there is always some level of risk for data corruption.

---

### Post by Flavian on 2009-11-18
Thanks for your replies guys! :)
I've done autoclean, clean and autoremove, freed up like 100 Mb, not enough though for an upgrade ;)

So I've decided to try the the iso image install method and if that doesn't work out, I will try resizing partitions :)

Thanks for the kind help.
Flo

---


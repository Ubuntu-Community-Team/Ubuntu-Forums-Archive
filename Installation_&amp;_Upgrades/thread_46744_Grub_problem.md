---
title: "Grub problem"
date: 2005-07-06
forum: Installation &amp; Upgrades
---

### Post by aviceda on 2005-07-06
Hi All,

Just installed Ub5.04 am am quite impressed so far, however I'm still a bit of a linux novice and have noticed a problem when booting. I told Grub to install on the MBR and when booting I get a logical list of the OS, first Ubuntu, then Fedora Core3 and XP.
XP seems to boot OK but when I try Fedora it comes up with many 'fatal errors' and Ubuntu seems to 'take over' in it's place....any ideas?

Another question, I've configured my dial-up modem thru the Gnome networking configuration utility (activate/deactivate) but I think there must be an easier way,
(...and why is my connection so slow?...it's much faster with fc3!)

Also I would like to mount my NTFS partitions (as many other distros seem able to do)

Any assistance will be gratefully received, look forward to hearing from you,

Tom

---

### Post by apollo2011 on 2005-07-06
You might take a look at your GRUB configuration.  You can either look at it in /boot/grub/menu.lst or install [Grubconf](http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb)

If you mount the Fedora partition into Ubuntu, you can view the Fedora menu.lst, and compare the entries.

There is also a complete howto on mounting NTFS drives in Ubuntu on the Wiki
 [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28mount%29](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28mount%29)

---


---
title: "Bootmgr not found CTRL+ALT+DEL to restart"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by madhusker on 2010-05-09
I have done many upgrades on my machine and it has always had a windows partition on it.  This time however when going from 9.10 to 10.04 it screwed my windows 7 partition.  Now I get the "Bootmgr not found CTRL+ALT+DEL to restart" message.  Why would it screw with my windows partition, or my boot loader???  I just asked it to upgrade my ubuntu distro, not screw with my windows partition!  The grub menu looks normal and the windows 7 option is still listed there however it will not boot.  What the heck... ?.?.?  :evil:

---

### Post by kansasnoob on 2010-05-09
In all likelihood this is the problem:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

We can only be sure by looking at the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Bug reports have been filed:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

---


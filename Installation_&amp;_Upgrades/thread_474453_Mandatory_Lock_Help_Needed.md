---
title: "Mandatory Lock Help Needed"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by Dirty Ol' Man on 2007-06-15
Let me start with a disclaimer:  I have little experience with Linux, and none with Ubuntu specifically.  Your help and patience will be greatly appreciated.

I recently installed Ubuntu 7.04 x86 DT version.  OS installation was successful (eventually), and everything seemed to work.  Then I added several packages.  Most worked ok, but three of them, including Dansgaurdian, complained during installation that the filesystem did not support mandatory locks and that it should be mounted with the "mand" option.  On consulting my Linux ref book, I determined (rightly or wrongly) that I needed to add the option to the line of /etc/fstab pertaining to the root partition.  I did so, but I missed that it should be seperated by a comma from other options (I used a space).  Then when I rebooted, I got a rather unpleasant error message that xserver failed to start.  I tried booting all of the boot options presented by the boot loader, boot the result was the same in each case.  Using a recovery boot option I was at least able to boot to a command shell, and changed the fstab file back to the original one, and rebooted.  I still got the same nasty error message.  I again booted to the shell and again added "mand" but this time with a comma; same error message.  Then I tried "nomand" option; same error message.

I also tried reinstalling Ubuntu without formatting the partitions, hoping not to have to reinstall all of the apps, but the installer will not allow that.

Can anyone advise me how to restore my system to bootable condition without starting over from scratch with all of the installations from the beginning???

Thanks in advance.

---


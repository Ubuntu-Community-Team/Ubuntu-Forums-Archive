---
title: "Not so normal install?"
date: 2005-06-12
forum: Installation &amp; Upgrades
---

### Post by juicemansam on 2005-06-12
Sorry if this has been mentioned before, but I couldn't find any similar answers.

I recently tried a dist-upgrade by following the [Hoary upgrade notes](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes), and ended up re-installing the system, well kind of. The thing is during the upgrade parts of the system didn't work (don't recall which), and decided to do a fresh install. That fresh install involved moving essential directories (such as etc, home, and any other directories that I had stuff to move over) to <name>.old, so as to not get the warning regarding the install over an existing system. Well everything went fine, except with the apparent need to partition the disk, even if nothing will be changed (to be exact would be writing the table to disk). After installing the system, I noticed that the install/configuration of grub, and later lilo, would lock up the install process; grub at 33% and lilo at 50%. I later found out that the system never had a working /etc/fstab, it was the single commented line version. I believe that somehow the installer never created a working /etc/fstab, and that's why grub/lilo install/configurations never worked, during the install and after booting via floppy. I'm assuming that both gurb and lilo use the /etc/fstab file to guess the boot devices, which are supposed to be set up beforehand, either by the install program or by hand.

So now that I've rambled quite a bit, I'm wondering if this is a common, or not so common but has happend before, problem? I'm also wondering if there's a difference in the way Hoary boots, with relation to the /etc/fstab file, compared to Warty? And finally, is there a way to recreate the fstab as the installer should, such as a script or program that the installer would use but that can be run manually?

---


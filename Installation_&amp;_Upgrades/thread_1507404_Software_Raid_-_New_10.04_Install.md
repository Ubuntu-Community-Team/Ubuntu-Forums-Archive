---
title: "Software Raid - New 10.04 Install"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by cmulcahy on 2010-06-11
OK, I'm finding way too much conflicting or outdated information regarding software RAID under 10.04.  

I have 4 x 1TB SATA drives.  I am setting them up in a RAID10 configuration.  I'm able to get the \dev\md0 device created, formatted and the OS installed.  Rebooting does not work, however.  It sits there for a while without loading GRUB before it gives up with an error "gave up waiting".  

Can someone either point me towards an updated walkthrough or give me a pointer to what the problem may be?

Thanks

---

### Post by cmulcahy on 2010-06-11
For more information, I have attempted putting the /boot partition into a non-RAID partition.  No help.

It is reporting that it is unable to find the partition in /dev/by-uuid/xxxxxxxxxxxxx which, indeed, is not there.  The /dev/md0 is not there.  I'm just missing a step somewhere, I'm sure of it. 

Any help appreciated!

Thanks

---

### Post by cmulcahy on 2010-06-12
OK, I figured it out.  CHROOT into the new environment and install mdtools.  Without that, the new install doesn't know how to start the raid.  Easy enough after 15 or so installs.

---


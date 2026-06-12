---
title: "Restoring failed server from a tar-ball"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by egandt on 2010-12-07
Normally I backup my servers with Acronis software, but I have a single DMZ server on which I can not install it as I am unable (due to security) to install the required packages to get it to work.

I regularly backup the server as tarballed bzip2 images (only about 600megs).  Today the HD failed, so I swapped it for a new one.  Next I reinstalled the base OS to get it partitioned and have the boot loader installed.  lastly I exploded the tarball back to the system.  Now I backed up fstab and grub.cfg as I have newer kernels, updates ... and the UUID will have changed, so I need to know the current one for the new drive.

The problem it does not work at all.  Grub says it can not find the primary of secondary kernels, now they are there and booting into recovery mode and mounting boot everything seems correct, but I still can not get system to boot after exploding the tarball.

Now the hardware is the same the HD size is the same, the configuration is the same the only difference is that the drive changed, so the UUIDs are different.  Yet even replacing fstab and grub.cfg with the orginal ones does nothing to fix the boot problem.

I need to understand what else I could be missing that is breaking grub as there is no other file that contains a UUID (based on the use of grep)?
Also I'm now concerned since I restore backs 95% of the time due to HD failures and have no idea if any Acronis back (from the 12 servers I backup) will actually work, my guess would be they will not work.

Thanks,
ERIC

---

### Post by egandt on 2010-12-17
Solution is to reinstall, upgrade to same version of kernel, then backup fstab and grub.conf then explode tarball and restore these 2 files.  To be sure everything was ok, I also installed the same exact packages before exploding the tarball.

---


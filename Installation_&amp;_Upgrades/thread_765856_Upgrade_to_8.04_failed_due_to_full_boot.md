---
title: "Upgrade to 8.04 failed due to full /boot"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by Bogtha on 2008-04-24
I've just got to the very end of the upgrade procedure with do-release-upgrade, and it bailed out because there was no space left on /boot (it would have been nice to know at the *start* that it needed more room than 7.10 did!).

Here's what happened:
> 
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1

Could not install the upgrades 

The upgrade aborts now. Your system could be in an unusable state. A 
recovery will run now (dpkg --configure -a). 

Setting up initramfs-tools (0.85eubuntu36) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic

gzip: stdout: No space left on device
cpio: write error: Broken pipe
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1

Could not install the upgrades 

The upgrade aborts now. Your system could be in an unusable state. A 
recovery will run now (dpkg --configure -a). 

Setting up initramfs-tools (0.85eubuntu36) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic

gzip: stdout: No space left on device
cpio: write error: Broken pipe
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1
r

So I went into the partition manager to resize /boot and the following partition.  It successfully shrunk the following partition, but then failed to grow /boot - the fsck failed because the /dev/hda3 file had disappeared.  From that point on, going into the partition manager brings up a warning that some actions are unavailable until I unmount all of the partitions on the disk.  This is not possible without rebooting as it holds the root partition, and of course the system is no longer bootable.

There was some free space at the end of the disk, so I created a new partition.  The system couldn't see it until I did /etc/init.d/udev restart, after which I put an ext3 partition on it, changed /etc/fstab to point /boot to it, and mounted it.

Then I performed dpkg --configure -a, which resulted in this:

> Setting up initramfs-tools (0.85eubuntu36) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic


I tried do-release-upgrade again, and it tells me I'm up to date.

Looking in /boot now, there is only initrd.img-2.6.24-16-generic and nothing else, and I suspect the boot loader won't be pointing at the new partition anyway.

What I really need to know is if there is any way of resuming the upgrade, and if not, which files need to be in /boot and which actions the do-release-upgrade performs after that point.

I'm old to Linux, but new to Ubuntu, so if anybody could point me in the right direction it would be very much appreciated.  I don't mind doing things by hand, but I need to be pointed in the right direction first.

---

### Post by Bogtha on 2008-04-24
Update:

Now the partition manager is telling me I have no partitions whatsoever on the disk, and cfdisk is telling me that my ext3 root partition and reiserfs home partition are free space.

Both of these partitions are currently mounted and I can see stuff on them fine, but obviously I'm worried that if I reboot, I'll lose a lot of data.  Any suggestions?

---


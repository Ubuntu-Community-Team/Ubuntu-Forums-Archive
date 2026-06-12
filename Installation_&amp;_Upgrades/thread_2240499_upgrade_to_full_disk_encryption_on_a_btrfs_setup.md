---
title: "upgrade to full disk encryption on a btrfs setup"
date: 2014-08-20
forum: Installation &amp; Upgrades
---

### Post by miguelnegrao on 2014-08-20
Hi

I'm running 14.04 on a single partition which uses the btrfs filesystem. The system was installed from the 13 version installer, so it has the usual @ and @home subvolumes.  I'm running this system on macbook pro, which has efi. the efi partition is mounted to /boot/efi and /boot is just a directory of / which points to the @ subvolume:

/dev/sda5 / btrfs rw,relatime,ssd,space_cache 0 0
/dev/sda1 /boot/efi vfat rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0
/dev/sda5 /home btrfs rw,relatime,ssd,space_cache 0 0


I would now like to upgrade to full disk encryption using a LUKS but maintaining my btrfs filesystem. What is the easiest way of doing this ?

I already tried in a virtual machine to create install a brande new 14.04 system with btrfs on  a luks volume (for / and /home) and a ext2 partition for /boot, and this boots the system fine. My plan would be to copy my btrfs filesystem to another disk with btrfs send ... | btrfs receive ... , then wipe the disk, install from the installer with a luks partition and a btrfs filesystem inside it and /boot on another ext2 partition, then send the btrfs subvolumes back to the disk and just do mv @ @delete; mv @old @ . But this doesn't account for the fact that now /boot is in another partition. Which files would I have to change ? /etc/fstab ? anything else ?

---


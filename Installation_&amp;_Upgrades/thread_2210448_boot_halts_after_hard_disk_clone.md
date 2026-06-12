---
title: "boot halts after hard disk clone"
date: 2014-03-10
forum: Installation &amp; Upgrades
---

### Post by rbates2 on 2014-03-10
I cloned a failing hard disk, copying all partitions.  After sorting out some other problems, the boot halts after
mounting my file systems and a couple of messages from ohci1394.  I can not get a command prompt.
The two virtual terminals I have at this point each have a flashing underline cursor and echo typed characters, but
do not otherwise respond.  

There are no files in /var with dates as recent as the recent boot attempt.  This is true both of the recently
mounted (according to a message still visible on the screen) /var partition and of the /var in the slash
partition, when nothing is mounted on it.  

More details:
ubuntu 10.04, 64-bit.  I plugged in a new disk (as sdb), partitioned like the old failing one, except for
size changes, copied contents with back-to-back piped tar instances, then swapped the disk plugs
so the new disk was sda.  This booted, but was using the slash partition on the old disk.  All other
partitions, including /boot were taken from the new disk.  

Fixing UUIDs in grub.cfg fixed this, and boot-rescue got things to the grub boot menu.  Meanwhile, the
old disk died completely, and I have had to unplug it.  

I am trying hard to avoid reinstalling, not because the reinstall itself is so bad, but because of all the
post-install configuration and additional package installation required.

---

### Post by oldfred on 2014-03-11
If you used a dd type copy you have duplicate UUIDs. Best to disconnect old drive.

Otherwise you have to change all UUIDs, change fstab & reinstall grub. Their may be several other places.

But 10.04 is only still supported for servers not desktops. Better to install newer version.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---


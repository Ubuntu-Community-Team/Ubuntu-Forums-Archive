---
title: "Setting mount label in 11.04 install."
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by lewisskinner on 2011-05-03
OK, so I attempted to upgrade to Natty from Maverick.  It got all the way through (VERY slowly) but then hung with 1 minute to go.  When I woke up in the morning, we'd had a powercut and so the upgrade did not complete, leaving me unable to boot into Ubuntu.

So, I used my Maverick liveCD, and then downloaded and burned the Natty image and booted into it.  However, when I try to install I keep getting errors if I use the 'upgrade' option, indicating that my partitions are mounted and need unmounting.  If I unmount (with gparted, sudo umount or nautilus GUI - it doesn't seem to matter) I lose the 'upgrade' option entirely, with only option to delete all partitions, overwrite my current Ubuntu install or 'something else' (ie specify manually).  As I set my partition table before my original install, I choose this latter option.

I then get the problem that I cannot set labels for my partitions on the install screen.  My previous situation was as follows:

/dev/sda - 500GB
sda1 - ntfs - /Windoze - 244.14GB
sda2 - ext3 - / - 221.62GB

/dev/sdb - 1.5TB
sdb1 - FAT32 - /windowsswap - 10GB
sdb2 - swap - /swap - 10GB
sdb3 - ntfs - /data - 1TB
sdb4 - ext3 - /home - 377.27GB

but I am now longer allowed to type my own mount points - /data, /Windoze etc.  Do I now need to do this afterwards, and if so, how?

tbh, this is a good excuse to make the update of the partition table I've been planning, with a single shared ntfs partition on the 1.5TB (also with swap for Linux and Virista) and then a triple-boot scenario on the 500GB drive with a small /home for user settings.

incidentally, do compiz and and AWN work with Unity?

---

### Post by lewisskinner on 2011-05-04
anyone?

---

### Post by kansasnoob on 2011-05-04
That's a known bug:

[https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes#Boot,%20installation%20and%20post-install](https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes#Boot,%20installation%20and%20post-install)

> The manual mount point entry box in the desktop installer's partitioner does not accept keyboard input. The drop-down still works, so various standard mount points may be selected, and copying and pasting within the entry box also works. This was noticed too late to be corrected for 11.04. In the meantime, you can mount partitions manually later, use copy-and-paste, or use the alternate install CD.

You can find somewhat more detailed work-arounds at the bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043)

---


---
title: "Upgrade from 13.10 to 14.04 failed with grub_term_highlight_color on raid,lvm,btrfs"
date: 2014-08-16
forum: Installation &amp; Upgrades
---

### Post by dodtsair on 2014-08-16
I tried to upgrade my current system from 13.10 to 14.04.  At this point in time I get the grub_term_highlight_color error on boot.  Then I am dropped to grub console.  

I have attempted to reinstall grub per the bug found: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977) but when I run dpkg-reconfigure grub-pc it fails with /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

I have googled around for this grub-probe problem, it seems it was prevalent a year or two ago but at this time all bugs I look at are resolved.  Is there a work around I can use to get my system up and running again?


/dev/sdb,/dev/sdc (/dev/sda is the usb recovery device right now) are both members of a raid 1 using mdadm /dev/md127
/dev/md127 is a full lvm the volume group is called ds or /dev/ds, ubuntu didn't support swap on btrfs at the time
The lvm is split into two logical volumes one for swap, and one for root
The root lvm /dev/ds/root has the entire section given to a btrfs filesystem 
The btrfs filesystem has four "labels" @, @apt-snapshot....release-upgrade-raring, @...release-upgrade-saucy, @...release-upgrade-trusty, @home

Is there a work around I can employ for the grub-probe error and install a working grub onto my disks.

---


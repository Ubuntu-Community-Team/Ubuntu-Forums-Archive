---
title: "lvm not automatically active on heron"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by robwicks on 2008-01-16
I have an 8.04 install and moved a couple of drives from another system into my current system. These drives were set up using LVM. I can manually vgchange and activate the volume groups, and then mount the logical volumes with no problem. Udev does not do this automatically on boot, however. I had to add the vgchange and mount commands in /etc/rc.local to get my filesystems to automatically mount. Am I missing something, or is this a bug?

---


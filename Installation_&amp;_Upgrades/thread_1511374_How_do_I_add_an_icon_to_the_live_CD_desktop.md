---
title: "How do I add an icon to the live CD desktop?"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by andrewkk on 2010-06-16
When I [customize]("https://help.ubuntu.com/community/LiveCDCustomization") the Ubuntu 10.04 LTS live CD, what files do I need to change in order to add another launcher to the live user's desktop?

---

### Post by andrewkk on 2010-06-21
Found it.

Within /casper/filesystem.squashfs, copy the custom launcher into /usr/share/applications/, then edit /usr/share/initramfs-tools/scripts/casper-bottom/10adduser to include the new launcher in the same line that installs ubiquity-gtkui.desktop.

---


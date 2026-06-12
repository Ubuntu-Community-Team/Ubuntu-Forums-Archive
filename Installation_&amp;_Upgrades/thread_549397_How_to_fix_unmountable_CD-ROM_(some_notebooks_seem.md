---
title: "How to fix unmountable CD-ROM (some notebooks seem to have this issue)"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by dgtldaydrmr on 2007-09-12
I thought I should share in case anyone else needs this information.
I have a new Qosmio F40 Toshiba notebook.
After install I could not access my CD-ROM drive and it would not mount saying it did not exist.
lshw didn't show my CD-ROM as well...

Apparently this is a fix for some dell notebooks that have a similar issue.

gksudo gedit /etc/initramfs-tools/modules
append piix

sudo update-initramfs -u


Sorry if this has been mentioned I'm only trying to help others like me.

---


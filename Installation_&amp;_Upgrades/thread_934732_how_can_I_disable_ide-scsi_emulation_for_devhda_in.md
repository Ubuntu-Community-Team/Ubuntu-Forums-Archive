---
title: "how can I disable ide-scsi emulation for /dev/hda in Feisty?"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by wfdudley on 2008-09-30
Hello,

I've got Feisty installed on about 10 machines, and only this latest upgrade
from Edgy is giving me trouble.  The system insists on having scsi
emulation running on the main (only) hard disk.

Partitioning is simple:
/dev/hda1         /
/dev/hda2         swap

but when I boot, I find that / is /dev/sda1, and I had no swap until
I edited /etc/fstab to change /dev/hda2 to /dev/sda2.

I'm using grub as per usual Kubuntu practice.
I've googled hi and lo and searched this forum and found no mention of
this at all.

The reason this is bothering me is that xine cannot find the dvd drive
anymore.  Yes, the symbolic link from /dev/dvd points to a scsi device
now, but xine still cannot find the dvd drive.

Thanks in advance,
Bill Dudley
longtime Kubuntu/Linux user

---


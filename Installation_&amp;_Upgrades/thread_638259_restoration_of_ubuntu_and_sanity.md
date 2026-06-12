---
title: "restoration of ubuntu and sanity"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by MEGAMANULTIMATE on 2007-12-11
In a panic I had to reinstall ubuntu (or maybe not, I'm thinking) after all that showed up one time after a forced fsck was a black terminal screen. After installing it, I saw that my comp prompted me to either start the old busted linux or the new one I had installed (I discovered I have like, five partitions now). Is there a way that I can change my home folder back to its old location without fear, also while getting rid of the dual boot prompt and the excess partition garbage? I think it's something with fstab, but here's what came up when I opened the file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=a7c9dd05-0d86-4b2e-8998-72b1f0eac898 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=b445dff8-13ce-49b6-a2e2-30ccf80dbbff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

I'm completely lost. What do I do? Any help at all would be appreciated.

---


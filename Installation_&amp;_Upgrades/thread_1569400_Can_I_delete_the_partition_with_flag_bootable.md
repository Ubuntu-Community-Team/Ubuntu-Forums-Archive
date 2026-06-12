---
title: "Can I delete the partition with flag bootable?"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by arcelivez on 2010-09-06
Well I currently have a windows partition currently formatted as ext3 which has the partition flag bootable (It previously had Windows Vista on it). I also have a windows partition with NTFS filesystem with Windows 7 on it which is not bootable because the previously mentioned partition became formatted by me. And I also have more partitions for Ubuntu, which is currently the only OS working.

To show it visually:
[http://img688.imageshack.us/img688/192/screenshot320gbharddisk.png](http://img688.imageshack.us/img688/192/screenshot320gbharddisk.png)

So my question is can I delete the partition called "Inter" and recreate a new partition and format it again with ext3? It has the partition flag bootable, won't I loose all of the partitions this way? It's also the primary partition? Is there a big risk?

---

### Post by arcelivez on 2010-09-06
Does anyone know anything about it? Is it risky or not? :S

---

### Post by oldfred on 2010-09-06
Grub/Ubuntu do not use boot flag, but some BIOS expect to see a boot flag on a primary partition or else they will not let you boot. 

You probably cannot boot your win7 if it is in an extended partition as windows only boots from primary partitions. It combined its boot files into your Vista install in the primary so it is also missing its boot files. If it was in a primary you could set boot flag on the win7 partition and repair, but windows will not repair a logical partiiton.

---


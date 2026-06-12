---
title: "[SOLVED] Grub Location"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by Milt888 on 2008-03-14
I have Vista on hd0 and XP on hd1.
If I install Ubuntu on an hd1 partition, (next to XP),
in a normal install won't grub be written to the mbr in Vista, hd0 ?

---

### Post by Rocket2DMn on 2008-03-14
Yes, it's OK to overwrite the windows bootloader as it can be restored if you decide to get rid of Ubuntu.

---

### Post by Pumalite on 2008-03-14
You can install Grub to it-s own partition and later boot it with Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
It installs to (hd0) by default. You can change this in step 8 (Advanced Tab)

---

### Post by Rocket2DMn on 2008-03-14
> **Pumalite said:**
> You can install Grub to it-s own partition and later boot it with Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
It installa to (hd0) by default. You can change this in step 8 (Advanced Tab)

+1
Also see here if you're serious about wanting to preserve the windows bootloader: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-144e274a5aeaa50ba6c93dcc4cc233626caf8ef0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-144e274a5aeaa50ba6c93dcc4cc233626caf8ef0)

---

### Post by Milt888 on 2008-03-14
Thanks everybody.
I just needed to confirm that.
I've already used Super Grub. It's a great tool.
Saved my bacon a few times.
 Milt

---


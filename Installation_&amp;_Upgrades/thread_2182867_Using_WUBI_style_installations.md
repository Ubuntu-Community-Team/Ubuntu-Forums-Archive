---
title: "Using WUBI style installations"
date: 2013-10-22
forum: Installation &amp; Upgrades
---

### Post by noorez on 2013-10-22
I was wondering if it was possible to do what wubi does in the sense that I could have a partition on my computer which contains the installer stuff and use that if I ever needed to reinstall the OS.

If I am not mistaken, WUBI copies the ISO image to a portion of the virtual disk and runs the installer from there after which ubuntu runs from that loop mounted disk. Is there anyway to emulate this behaviour for a more normal type of ubuntu installation?

---

### Post by TheFu on 2013-10-22
Very interesting idea!  We all use the multi-boot flash drives as quick installers - I like **yumi** as the building tool.  I would think that making a fat32 partition and pointing Yumi (or some other multi-boot tool) at that partition would work, but it would probably toggle the boot flag on the HDD to that partition - plus it would eat a primary partition, which most laptops don't have to spare.

For me, I'll stay with a 4G flash drive that has 10 different distros/tools installed. Feels safer and doesn't leave my system easily hackable if someone gets a hold of it. Everyone thought I was overly paranoid until the NSA stuff was released. Now I don't think that I'm paranoid enough.

Still, very interesting idea. I bet someone will post a solution.  It won't be wubi - at least I hope not.

---

### Post by Frogs Hair on 2013-10-22
There is a project named Lubi , but I don't if it is still actively updated. [http://lubi.sourceforge.net/lubi.html](http://lubi.sourceforge.net/lubi.html)

---


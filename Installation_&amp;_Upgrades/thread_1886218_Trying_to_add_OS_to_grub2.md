---
title: "Trying to add OS to grub2"
date: 2011-11-24
forum: Installation &amp; Upgrades
---

### Post by Camgaertner on 2011-11-24
I'm trying to add my windows 7 installation on to Grub 2. The OS is located on dev/sda1 on the primary hard drive. How should I format this code that I am adding to /etc/grub.d/40_custom?

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
[B]menuentry "Windows 7" {
insmod chain
set root=(hd1,1)
drivemap -s hd0 hd1
chainloader +1
}[/B]
```

---

### Post by darkod on 2011-11-24
Why don't you simply use the automatic discovery of os-prober?

Even if you don't want to use it permanently, to get the exact entry, you can enable os-prober once, run update-grub to create the entry in grub.cfg, and then copy that entry to 40_custom.

After that you can disable os-prober again and run update-grub to create new grub.cfg.

---


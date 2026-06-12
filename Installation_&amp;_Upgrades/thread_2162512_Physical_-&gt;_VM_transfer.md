---
title: "Physical -&gt; VM transfer"
date: 2013-07-14
forum: Installation &amp; Upgrades
---

### Post by Vl4dim1r on 2013-07-14
I had a hard disk die in my database server. I managed to keep it alive long enough to get a backup image, and I have since restored that image onto a VM. Now, the database originally had 2 hard disk drives. "sda" was my fileshare drive, mounted to /home/FTPuser and "sdb" contained the root filesystem. After all those years of it just working, I have no idea why I installed that way. Anyways, "sdb" is now "sda" in the VM, I chose not to convert the second hard drive to the VM. The OS tries to boot, but results in this kernel panic:

```
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

What/how do I need to edit in order for ubuntu to boot?

---


---
title: "mountall: unable to write pid file: read-only filesystem"
date: 2009-09-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by morryis on 2009-09-14
After downgrading libc6  because of the nvidia/x error I now get the following error when booting: ```
mountall: unable to write pid file: read-only filesystem
```
At that point the system startup stops and I have to use the magic keys to reboot. The same when I try to boot into recovery mode. I did a fsck from a live-cd with no errors on my root-partition. Any ideas?

EDIT: After rebooting several times the system now starts again.

---


---
title: "[SOLVED] recovering from apt failure"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by CAsurfer on 2008-07-27
Error message:
"Sub-process /usr/bin/dpkg returned an error code (1)"

For some period of time, my server had a corrupted filesystem. After a number of crashes, I realized what was happening and ran fsck to resolve the problem.

Unfortunately, the file corruption made it into apt (the package management system). Perhaps apt was run and programs were installed, while the system relied on corrupted configuration files, exacerbating the problem. The end result: even after fsck had repaired my files, I was left with a very confused package management system.

How I fixed it:
1) I ran "apt-get purge" on every package apt complained about. Running "apt-get remove" was insufficient.
2) I ran "apt-get clean" to delete all (possibly corrupted) installation files on my computer.
3) I ran "apt-get install" for everything that had been removed.

Hope this helps someone!

---

### Post by Fanless_Puppy_Fan on 2008-07-27
Great post. Thanks. This the exact kind of post that makes this forum one of the best.

---


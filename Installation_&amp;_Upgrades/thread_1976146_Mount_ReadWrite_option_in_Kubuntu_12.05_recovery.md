---
title: "Mount ReadWrite option in Kubuntu 12.05 recovery"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by dzchimp on 2012-05-08
After upgrading to Kubuntu, I was rather surprised to find that after landing in recovery, only the root file system was mounted, and was read only. At the root shell prompt, a mount command showed that /dev/sdb2 (which was /) was mounted rw, however file system could not be written to.

Fortunately I could turn it to read write by choose to run an fsck from the recovery menu. 11.10 used to have a "mount all file systems in rw" mode or something similiar in menu. It seems to have been removed? Is there a way to readd the command into the recovery menu? I'm guessing that it was a script. I can mount in rw by doing an fsck first, but this is a bit of a bother.

---


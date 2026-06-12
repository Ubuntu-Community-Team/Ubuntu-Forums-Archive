---
title: "Linux 3.11 breaks NFS"
date: 2014-02-19
forum: Installation &amp; Upgrades
---

### Post by sombrancelha on 2014-02-19
Hello,

I have a machine running precise and the home partition is mounted with NFS. I just upgraded to kernel 3.11.0-15-generic and rebooted the computer. Now, when I log in (ssh), I get the following error:

```

Could not chdir to home directory /home/USER: No such file or directory

```

If I revert to an older kernel (3.8), it works. So it's probably some configuration that changed between these kernel releases. I need the newer kernel because of some support it added to perf.

---


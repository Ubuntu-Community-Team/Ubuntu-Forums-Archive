---
title: "Not getting kernel updates"
date: 2022-01-20
forum: Installation &amp; Upgrades
---

### Post by philld2 on 2022-01-20
I have three virtual machines running Kubuntu handling different media servers.  All three machines are running 20.04.  Two of these machines are updated to kernel 5.13.0.27 however the third machine is only at 5.4.0.94 and even though I run an update on the machine, there is no retrevial / update of the kernel happening.  I have tried to do the update via both CLI and the Discover application but both do not locate a new kernel update.  I don't think I have configured anything to prevent the kernel from upgrading (although it might be possible as I'm still learning Ubuntu).  What is needed to be able to upgrade to the latest available kernel for this version?

---

### Post by deadflowr on 2022-01-20
The 5.4.0-94 kernel is reasonably up-to-date.
(There is a new updated kernel 5.4.0-96 that has been rolled out recently; (recent as in the last 24 hours or so)
so I would check and see if a new 5.4 comes out for you soon or not.

In terms of running different kernels for the same release see: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")
5.4 is the original kernel used by 20.04, so it's the GA kernel.

---

### Post by philld2 on 2022-01-20
Thanks deadflowr - didn't realize the kernel didn't get most current versions of the kernel by default but was 'static' at version 5.4.0.x.  I'll watch for 5.4.0.96!

---


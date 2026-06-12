---
title: "Useful patch for Kernel 2.6.18"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by originof on 2006-11-18
Write here all useful patches (kernel 2.6.18) that you know ;) 

I know only the ck patch : [http://members.optusnet.com.au/ckolivas/kernel/]("http://members.optusnet.com.au/ckolivas/kernel/")

[SIZE="1"]Excuse me for the bad english[/SIZE]

---

### Post by Matt Yun on 2006-11-18
The evms patch is necessary if you have a system with more than one hard drive.  You need it to [mount your local filesystems]("http://ubuntuforums.org/showthread.php?t=103900"):

apt-get install kernel-patch-evms

BTW, I had a problem with the [Ubuntu smp kernels locking up my dual-PIII box]("http://ubuntuforums.org/showthread.php?t=262735").  I fixed it by compiling my own smp kernel from kernel.org, with only the evms patch applied.  It's been working perfectly.

I suspect that since the ck patch is applied to the default Ubuntu kernels, it may be related to the smp problems.  However, I haven't had time to confirm this with any experimentation.

---

### Post by originof on 2006-11-19
i also know the bd-claim patch....for mount local hd

---


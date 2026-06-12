---
title: "GRUB error 16 after upgrade"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by mlykke on 2010-06-20
I'm running Ubuntu 9.10 and did an upgrade yesterday via the Update Manager. Just installed all proposed upgrades. After rebooting, my newest kernel throws an **error 16: inconsistent filesystem structure**. When I select my previous kernel from the GRUB, no problems. How do I debug this error? Or better yet, how do I fix it? Please help!

---

### Post by technocp on 2010-06-20
boot with live cd and install grub again may be the grub packages loaded in previous install were not correctly installed

---

### Post by mlykke on 2010-06-20
> **technocp said:**
> boot with live cd and install grub again may be the grub packages loaded in previous install were not correctly installed
Unfortunately, that didn't solve the problem.

Also, it seems, that GRUB is loading fine. The problem occurs when trying to boot from the default (latest) kernel.
I get:
```
Error 16: inconsistent filesystem structure
Press any key to continue

```When I press the any key :p I get to the GRUB menu where I can select 4 different builds. Latest is 2.6.26-22 which isn't working
If I select 2.6.26-21 - no problems.
Again - this happened after upgrading via the Update Manager. Could be a bug?

---

### Post by mlykke on 2010-06-20
Hi again

Well, I think I solved this one. My laptop is quite old and I've been experiencing file system problems with its HD before and this time it seems that the file **initrd.img-2.6.31-22-generic** is situated on some bad blocks because trying to copy the file gives I/O-error - error while reading from source...

Now thinking about upgrading to 10.04...

Thanks for your help, technocp!

---


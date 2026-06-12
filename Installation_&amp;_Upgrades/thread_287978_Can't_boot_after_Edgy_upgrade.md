---
title: "Can't boot after Edgy upgrade"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by Mirko on 2006-10-29
Upgraded to Edgy from a very functional Dapper.  Edgy will not boot.  The kernel oopses while loading the sata_promise module.  I am not using software or hardware RAID, and this motherboard worked great with Dapper.

Then I tried booting from the Edgy Desktop and Alternate Install CDs-- exact same problem.

My motherboard (and in fact, no disk controllers or motherboards) is not listed in [https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues).

---

### Post by timgood on 2006-10-29
I have this problem too - good Dapper, lousy Edgy. I can't even boot from the Edgy install CDs. It seems as if my hard drive is not being recognised by the new Edgy kernel (it is a SATA drive). I can boot into 2.6.15-26-amd64-k8 which gives me a working (after a fashion) system, but the new kernel fails to boot either from the hard drive or from install CD.

Help please?

---


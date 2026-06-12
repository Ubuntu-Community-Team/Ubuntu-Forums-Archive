---
title: "uptrack misdetecting Ubuntu version"
date: 2015-09-22
forum: Installation &amp; Upgrades
---

### Post by Keiran230 on 2015-09-22
**The system is clearly running 14.04.x Trusty**
```
$ lsb_release --codename --release --description
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty

```
```

$ uname -v
#65~14.04.1-Ubuntu SMP Wed Sep 9 10:03:23 UTC 2015

```
```
$ dpkg -l uptrack
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                     Version           Architecture      Description
+++-========================-=================-=================-======================================================
ii  uptrack                  1.2.28-1~ubuntu14 all               Client for the Ksplice Uptrack service
```

**However, uptrack thinks I'm running 14.10 Utopic.**
```

$ uptrack-upgrade
You are running a kernel from Ubuntu 14.10 Utopic.  Ubuntu 14.10
Utopic reached end of life on August 1, 2015 and is no longer
supported by the vendor.  As a result, Ksplice Uptrack no longer
supports Ubuntu 14.10 Utopic and no new updates will be made available
via Uptrack.  We recommend that all users of Ubuntu 14.10 Utopic
upgrade to a newer version of Ubuntu that is still supported by the
vendor.
Nothing to be done.
Your kernel is fully up to date.
Effective kernel version is 3.16.0-49.65
```

Note: It shouldn't affect anything, but this is on a QEMU/KVM guest on a host machine also running Ubuntu 14.04.3.

Has anyone seen this behavior before, and if so how did you get around it?

---

### Post by grahammechanical on 2015-09-22
My guess is that 14.04 has been upgraded to 14.04.3 but without the hardware enablement stack which I think has to be upgraded to separately. A new install of 14.04.3 from an ISO downloaded from Ubuntu.com will have the hardware enablement stack that came with Ubuntu 15.04. 

> In an effort to support a wider variety of hardware on an existing LTS  release, the 14.04.3 point release will ship with an updated kernel and X  stack by default. This newer hardware enablement stack will be  comprised of the kernel and X stack from the Vivid 15.04 release.

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes)

If you look at the charts in the wiki about the hardware enablement stack you will see that Ubuntu 14.10 was released with Linux 3.16 kernel and that Ubuntu 14.04 got that kernel with the 14.04.2 upgrade in February 2015 but it is given 18 months support. So, you are fine as regards kernel support. Indeed if you upgrade to the 15.04 hardware enablement stack you will get the 15.04 kernel (3.19) but support for it will end the same time as support for kernel 3.16.

So, if Uptrack is misreporting things is it something to worry about?

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Regards

---

### Post by Keiran230 on 2015-09-23
You were correct. This fixed it:
```

apt-get install --install-recommends linux-generic-lts-vivid

```

I couldn't care less about feature updates, etc, but if ksplice doesn't support the kernel, I'm forced to reboot the box constantly to apply security updates.

Marked solved.

---


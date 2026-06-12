---
title: "Ubuntu 20.04 upgraded to kernel 5.8"
date: 2021-01-12
forum: Installation &amp; Upgrades
---

### Post by Mantzas on 2021-01-12
Hi,

something strange happened which i cannot explain.
AFAIK Ubuntu 20.04.1 LTS shipps with kernel 5.4.
For whatever reason performing and update with `sudo apt upgrade` i got the 5.8 kernel.

```
Linux prometheus 5.8.0-36-generic #40~20.04.1-Ubuntu SMP Wed Jan 6 10:15:55 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```

and 

```

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.1 LTS
Release:	20.04
Codename:	focal

```

Any idea why?

---

### Post by grahammechanical on 2021-01-12
Could it be that we are 2 weeks away from the second point release of 20.04 (20.04.2)? Could it be that you have enabled the proposed updates channel in Software & Updates>Developer Options tab. If we do that then it could be that we get kernel upgrades a little bit sooner than other people. It gives us an opportunity to find out if there are any bugs.

I do believe that some users have experienced problems with the 5.8 kernel but we would need to be running 20.10 or 21.04 development version or taken special steps to install the 5.8 kernel to have it.

[https://wiki.ubuntu.com/FocalFossa/ReleaseSchedule](https://wiki.ubuntu.com/FocalFossa/ReleaseSchedule)

> Linux 5.8 is already available for testing in [Ubuntu 20.10]("https://www.omgubuntu.co.uk/2020/05/ubuntu-20-10-release-features") daily builds. While it&#8217;s not yet clear which Linux kernel version the final stable release of the *Groovy Gorilla*  will ship with come October (**and thus get back-ported to Ubuntu 20.04  LTS via 20.04.2 LTS**) there&#8217;s a good chance it will be this release.

[https://www.omgubuntu.co.uk/2020/08/linux-5-8-kernel-features](https://www.omgubuntu.co.uk/2020/08/linux-5-8-kernel-features)

Regards

---

### Post by Mantzas on 2021-01-12
I have not enabled anything in the Developers options. For me it seems to be working so far good enough.
I was under the impression that in order to upgrade to newer kernel you have to either manually install them or upgrade to a never version e.g. 20.10.
My impression was that for the lifetime of 20.04 the kernel will be 5.4, but i might be mistaken.

---

### Post by Impavidus on 2021-01-12
If you have the linux-generic package pulling in new kernel versions, you stay on the 5.4 kernel series. If you have linux-generic-hwe-20.04 pulling in new kernel versions, you upgrade to 5.8 and later to whatever kernel will be used by 21.04, 21.10 and 22.04. It used to be that you would get linux-generic-hwe-* if you installed from the *.2 point release or later, but it seems this was changed for Ubuntu 20.04. You can change it back. If you don't need the newer kernels and want to avoid the risk of major kernel upgrades, install linux-generic, reboot using the 5.4 kernel, remove linux-generic-hwe-20.04 and (auto)remove the packages pulled in by linux-generic-hwe-20.04.

---

### Post by Mantzas on 2021-01-12
The initial post shows that i use the generic one, correct (Linux prometheus 5.8.0-36-generic #40~20.04.1-Ubuntu SMP Wed Jan 6 10:15:55 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux)?
It seems that the package `linux-generic-hwe-20.04` is installed in my system.

---

### Post by ajgreeny on 2021-01-12
There appears to have been a change in the timing of the inclusion of the hwe kernel stack in 20.04.

It has always been a default package only from the point 2 release version but for some reason it has started in the point 1 release this time, and it is causing some problems, the 5.8.0-36 apparently not being quite "up to scratch" as we say in UK.

If you have hardware that works with the 5.4 kernel do what Impavidus says above just to be sure, or if your system works with the 5.8 kernel, leave it as is; you can always boot to the 5.4 kernel from grub if necessary.

---

### Post by ajgreeny on 2021-01-14
It looks as if there has been another 5.8.0-38 kernel released today, so try that and you may find that all is well again; this kernel version has arrived only a few days after the "broken" 5.8.0-36.

With luck this one will work as expected rather than give so many users difficulties of many kinds.

---

### Post by ping-wu on 2021-01-14
I have four machines all are Ryzen based.  Did not notice any problem with the 5.8.0-36 kernel.  But will still upgrade to 5.8.0-38.

---


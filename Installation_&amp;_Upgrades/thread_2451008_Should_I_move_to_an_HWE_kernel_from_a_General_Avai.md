---
title: "Should I move to an HWE kernel from a General Availability kernel?"
date: 2020-09-24
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2020-09-24
I'm running Ubuntu 18.04.4, and I appear to have both the "General Availability" kernel *(5.4.0-48.52~18.04.1)* and the HWE kernel *(5.4.0.48.52~18.04.42) *installed.

***uname -a*** tells me that the kernel I am actually using is the general kernel:

```
Linux mybox 5.4.0-48-generic #52~18.04.1-Ubuntu SMP Thu Sep 10 12:50:22 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

So, I have three questions about this:

(1)  Should I be using the HWE kernel?  I have no new hardware, I'm using the same old desktop workstation that I've had for several years.

(2)  If it is in some way better for me to use the HWE kernel, how do I change over from the general kernel?

(3)  If there is no reason to use the HWE kernel, is  there some reason I  should not delete it?  My thinking is that if it's sitting around unused, then I should remove it.

*Thanks  for any  tips.*

Here is what displays when I run ***dpkg -l linux-image-\* && dpkg -l linux-headers-\****

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
un  linux-image-5.3.0-51-generic                  <none>                      <none>                      (no description available)
un  linux-image-5.3.0-53-generic                  <none>                      <none>                      (no description available)
un  linux-image-5.3.0-62-generic                  <none>                      <none>                      (no description available)
un  linux-image-5.4.0-45-generic                  <none>                      <none>                      (no description available)
un  linux-image-5.4.0-47-generic                  <none>                      <none>                      (no description available)
ii  linux-image-5.4.0-48-generic                  5.4.0-48.52~18.04.1         amd64                       Signed kernel image generic
ii  linux-image-generic-hwe-18.04                 5.4.0.48.52~18.04.42        amd64                       Generic Linux kernel image
un  linux-image-unsigned-5.3.0-51-generic         <none>                      <none>                      (no description available)
un  linux-image-unsigned-5.3.0-53-generic         <none>                      <none>                      (no description available)
un  linux-image-unsigned-5.3.0-62-generic         <none>                      <none>                      (no description available)
un  linux-image-unsigned-5.4.0-45-generic         <none>                      <none>                      (no description available)
un  linux-image-unsigned-5.4.0-47-generic         <none>                      <none>                      (no description available)
un  linux-image-unsigned-5.4.0-48-generic         <none>                      <none>                      (no description available)
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
un  linux-headers-3.0                             <none>                      <none>                      (no description available)
ii  linux-headers-5.4.0-48-generic                5.4.0-48.52~18.04.1         amd64                       Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
un  linux-headers-686-pae                         <none>                      <none>                      (no description available)
un  linux-headers-amd64                           <none>                      <none>                      (no description available)
un  linux-headers-generic                         <none>                      <none>                      (no description available)
ii  linux-headers-generic-hwe-18.04               5.4.0.48.52~18.04.42        amd64                       Generic Linux kernel headers
```

---

### Post by CatKiller on 2020-09-24
The non-HWE kernel, from when 18.04 was released, is 4.15. The HWE kernel is 5.4; new installs from 18.04.2 onwards were put on the HWE kernel by default.

The default, when a new kernel package is installed, is to keep the old one in case the new one goes all pear-shaped, so that you can still boot your computer to fix things. After you've built up a few old versions, the oldest get marked for autoremoval.

So, yes, you should probably stick with the HWE kernel, and no, you don't need to do anything.

---

### Post by watchpocket on 2020-09-24
> **CatKiller said:**
> The non-HWE kernel, from when 18.04 was released, is 4.15. The HWE kernel is 5.4; new installs from 18.04.2 onwards were put on the HWE kernel by default.

If that's the case, shouldn't* uname -a* be telling me that I'm using *5.4.0.48.52~18.04.**42** *instead of[I] 5.4.0-48.52~18.04.**1**  ??  
(See my previous post where the installed kernel images and headers are listed.)[/I]

> The default, when a new kernel package is installed, is to keep the old one in case the new one goes all pear-shaped, so that you can still boot your computer to fix things. After you've built up a few old versions, the oldest get marked for autoremoval.

I used to keep several old kernels installed (because I didn't know that I was doing that) until I learned to delete them.  Generally I have the current (which right now is 5.4.0-48) and the most recent (5.4.0.7-47), and remove anything older than that.  (At the moment, it just so happens that I have only the current kernel installed.  I've never had to roll back to a previous kernel.)

> So, yes, you should probably stick with the HWE kernel, and no, you don't need to do anything.

So I ***am*** using the HWE kernel after all?  I didn't realize it was being used, I just thought it was installed but not active (given wha*t uname -a* returns, which I thought meant that I'm using the non-HWE kernel).

---

### Post by deadflowr on 2020-09-24
> If that's the case, shouldn't uname -a be telling me that I'm using 5.4.0.48.52~18.04.42 instead of 5.4.0-48.52~18.04.1 ??
5.4.0.48.52~18.04.42 is the version of the linux-image-generic-hwe-18.04 package. Not the actual kernel package.
linux-image-generic-hwe-18.04 is like a meta package, all new kernels are linked to that so when a new kernel comes through you can actually get the updated kernel.
*apt show linux-image-generic-hwe-18.04* shows this as the package description:
> Description-en: Generic Linux kernel image
 This package will always depend on the latest generic kernel image
 available.
Looking at the package dependencies you'll see
```
Depends: **linux-image-5.4.0-48-generic**, linux-modules-extra-5.4.0-48-generic, linux-firmware, intel-microcode, amd64-microcode
```
and the next kernel update the dependency will change to another version like linux-image-5.4.0-49-generic,
and so on and so on.

---


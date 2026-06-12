---
title: "unable to boot - please use kernel appropriate for your CPU"
date: 2013-02-02
forum: Installation &amp; Upgrades
---

### Post by gdoug on 2013-02-02
Hi I am trying to install on a Dell notebook with a Pentium M (Centrino) recognized as an i686 processor. I have tried both the 32bit and 64bit versions and neither will boot. I read another post about a BIOS setting related to the processor, but I didn't see that option. I would really like to try Ubuntu. Any ideas? Thanks.

---

### Post by AnoPoli on 2013-02-02
Have you tried any other distros?
what are the results if you did?

---

### Post by steeldriver on 2013-02-02
Was the message about 'PAE' by any chance?

> The Ubuntu 12.04 installation image does not include support for old  computers that do not support PAE. If your computer is affected, you can  either first install Ubuntu 10.04 or 11.10 and upgrade to 12.04 or you  can use the Lubuntu or Xubuntu images. The non-PAE version of the Linux  kernel will be dropped completely following the 12.04 release. see [https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#System_Requirements](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#System_Requirements)

---

### Post by gdoug on 2013-02-02
steeldriver, looks like it doesn't support "PAE". However I did try lubuntu with the same result. Thanks.

---

### Post by steeldriver on 2013-02-02
which release of lubuntu did you try? iirc 12.04 should support non-pae cpus but not 12.10

there *are* ways to get non-pae kernels installed with ubuntu 12.04+ but tbh if the machine is old enough to not support pae, chances are it will be too cpu / ram limited to run the unity desktop decently

---

### Post by sudodus on 2013-02-02
> **steeldriver said:**
> which release of lubuntu did you try? iirc 12.04 should support non-pae cpus but not 12.10

there *are* ways to get non-pae kernels installed with ubuntu 12.04+ but tbh if the machine is old enough to not support pae, chances are it will be too cpu / ram limited to run the unity desktop decently
+1
Lubuntu 12.04 and Xubuntu 12.04 LTS have a non-pae kernel. I run Lubuntu 12.04 on an IBM Thinkpad T41 with a pentium m cpu.

---

### Post by gdoug on 2013-02-02
It was 12.10 lubuntu I was trying to install (just learning about the "PAE" requirement). I will try experimenting with older versions. Thanks!

---


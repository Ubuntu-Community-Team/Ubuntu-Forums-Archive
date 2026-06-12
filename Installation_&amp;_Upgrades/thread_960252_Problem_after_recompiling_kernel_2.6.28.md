---
title: "Problem after recompiling kernel 2.6.28"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by alex88 on 2008-10-27
Hi, i've compiled the 2.6.28-rc1 kernel with no errors. But when i install the image with dkpg the output is this
```

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms

run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28-rc1-extreme.postinst line 1181

dpkg: linux-image-2.6.28-rc1-extreme (--install):
subprocess post-installation script returned error exit status 2
```

the kernel works, but the nvidia drivers not... If i do

```
dkms build -m nvidia -v 177.80 -k $(uname -r)

Kernel preparation unnecessary for this kernel. Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.28-rc1-extreme module KERNDIR=/lib/modules/2.6.28-rc1-extreme IGNORE_XEN_PRESENCE=1 IGNORE_CC_MISMATCH=1 SYSSRC=/lib/modules/2.6.28-rc1-extreme/build.... (bad exit status:2)
```

and the make.log file ends with

*** Unable to determine the target kernel version. ***

make: ***[select_makefile] Error 1


The link to the kernel source path is correct.

What should I do?

---

### Post by MighMoS on 2008-10-28
This always happens to me when I recompile my kernel. I'd also be interested to know what the fix is.

---

### Post by blazemore on 2008-11-11
*bump* I can't figure out what this is!
I KNOW it's a problem with the Nvidia drivers.
I tried compiling the kernel before installing the drivers, but then the drivers wouldn't install!

---

### Post by Tiftof on 2008-11-19
same problem here, any solution yet?

---

### Post by blazemore on 2008-11-20
Surely this is a common problem?

---

### Post by tannalv on 2008-11-22
> **blazemore said:**
> Surely this is a common problem?

apt-get purge nvidia-common

Google is your friend...

---

### Post by PmDematagoda on 2008-11-22
I don't think you can compile the Nvidia drivers, not without a patch atleast since in my experience, whenever you want to use an -rc kernel, you will almost always need to patch the nvidia driver file since Nvidia doesn't add support for -rc kernels until after they come out.

---

### Post by seangg on 2008-11-24
It seems to have some problem with nvidia drivers.

possible solution:

first remove nvidia drivers
     apt-get purge nvidia-common

then install kernel package
     dpkg -i .....


it works for me perfect (kernel 2.6.27.4 kubuntu 8.10).

---

### Post by m4cph1sto on 2008-11-27
After I do --purge, how do I get the nvidia drivers back?

---

### Post by PmDematagoda on 2008-11-27
> **m4cph1sto said:**
> After I do --purge, how do I get the nvidia drivers back?

If you have a working GUI, go to System>Administration>Hardware Drivers, that should allow you to reinstall the Nvidia driver.

---


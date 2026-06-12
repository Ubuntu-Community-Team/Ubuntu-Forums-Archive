---
title: "nvidia driver rabbithole - 'kernel configuration is invalid'"
date: 2016-02-08
forum: Installation &amp; Upgrades
---

### Post by jeremy-spagnet on 2016-02-08
I have been having some trouble installing an nvidia driver for a K80 gpu on an ubuntu 14.04 headless machine.
I tried several install methods (local .deb, local runfile, remote .deb,&nbsp; apt-get install of nvidia packages, and adding a ppa) and none succesfully allow communication with the gpu.
All give errors like the following (from the remote .deb attempt)

```

root@brain2:~# uname -a
Linux brain2 3.13.0-74-generic #118-Ubuntu SMP Thu Dec 17 22:52:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

root@brain2:~# lspci|grep -i nvidia
83:00.0 3D controller: NVIDIA Corporation Device 102d (rev a1)
84:00.0 3D controller: NVIDIA Corporation Device 102d (rev a1)

root@brain2:~# sudo apt-get install linux-headers-$(uname -r)
...0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@brain2:~#  more /var/lib/dkms/nvidia/352.79/build/make.log
DKMS make.log for nvidia-352.79 for kernel 3.13.0-74-generic (x86_64)
Mon Feb  8 06:31:43 CST 2016
NVIDIA: calling KBUILD...
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-74-generic'
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
    echo >&2;                            \
    echo >&2 "  ERROR: Kernel configuration is invalid.";        \
    echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
    echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo >&2 ;                            \
    /bin/false)

```

Can anyone give me a clue?  I don't know what 'make oldconfig make prepare' is supposed to do and am wary of running random commands not knowing what they do , where it should be run etc.
Thanks

---

### Post by Vladlenin5000 on 2016-02-08
Why do you think you need special drivers for a headless machine"?

---

### Post by jeremy-spagnet on 2016-02-09
I don't think I need special drivers, but I do need a working driver to actually use the device, I believe.
I am attempting to use the gpu with cuda , for computation purposes.  By 'headless' I mean remote, no screen.

---

### Post by jeremy-spagnet on 2016-02-11
I have tried the following: 
local runfile install
local .deb install
local apt-get install
remote .deb install
each time removing the results of the previous install.
Crossposting on the nvidia forum is less than helpful since they are autohiding  my posts (marked as spam by their system).
Anyway does anyone how to diagnose the 'kernel configuration invalid' error?

---

### Post by jeremy-spagnet on 2016-02-12
i gave up and reinstalled ubuntu, nvidia install was ok subsequently

---


---
title: "Nvidia DKMS module is not being built into newer kernel"
date: 2013-01-20
forum: Installation &amp; Upgrades
---

### Post by ryanvade on 2013-01-20
Hello.  I am using Ubuntu 12.10, Nvidia driver 313.09, and am trying to build kernel 3.7.3.

I am using the old config.  During the make modules_install install phase the Nvidia driver DKMS module is not being found.
```
sh /usr/src/kernel/linux-3.7.3/arch/x86/boot/install.sh 3.7.3 arch/x86/boot/bzImage \
        System.map "/boot"
run-parts: executing /etc/kernel/postinst.d/dkms 3.7.3 /boot/vmlinuz-3.7.3
ERROR (dkms apport): binary package for nvidia: 313.09 not found
Error! Bad return status for module build on kernel: 3.7.3 (x86_64)
Consult /var/lib/dkms/nvidia/313.09/build/make.log for more information.
```That last log file says```
KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(asm_offsets)"  -D"KBUILD_MODNAME=KBUILD_STR(asm_offsets)" -fverbose-asm -S -o arch/x86/kernel/asm-offsets.s arch/x86/kernel/asm-offsets.c
mv: cannot stat `arch/x86/kernel/.asm-offsets.s.tmp': No such file or directory
make[5]: *** [arch/x86/kernel/asm-offsets.s] Error 1
make[4]: *** [prepare0] Error 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[3]: *** [module] Error 1
make[2]: *** [module] Error 2

```Does anyone have any suggestions?

---

### Post by Bobhuber on 2013-01-20
> **ryanvade said:**
> Hello.  I am using Ubuntu 12.10, Nvidia driver 313.09, and am trying to build kernel 3.7.3.

I am using the old config.  During the make modules_install install phase the Nvidia driver DKMS module is not being found.
```
sh /usr/src/kernel/linux-3.7.3/arch/x86/boot/install.sh 3.7.3 arch/x86/boot/bzImage \
        System.map "/boot"
run-parts: executing /etc/kernel/postinst.d/dkms 3.7.3 /boot/vmlinuz-3.7.3
ERROR (dkms apport): binary package for nvidia: 313.09 not found
Error! Bad return status for module build on kernel: 3.7.3 (x86_64)
Consult /var/lib/dkms/nvidia/313.09/build/make.log for more information.
```That last log file says```
KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(asm_offsets)"  -D"KBUILD_MODNAME=KBUILD_STR(asm_offsets)" -fverbose-asm -S -o arch/x86/kernel/asm-offsets.s arch/x86/kernel/asm-offsets.c
mv: cannot stat `arch/x86/kernel/.asm-offsets.s.tmp': No such file or directory
make[5]: *** [arch/x86/kernel/asm-offsets.s] Error 1
make[4]: *** [prepare0] Error 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[3]: *** [module] Error 1
make[2]: *** [module] Error 2

```Does anyone have any suggestions?
Try installing the newest 313.18  drivers ( [ftp://download.nvidia.com/XFree86/Linux-x86_64/](ftp://download.nvidia.com/XFree86/Linux-x86_64/)  ) before building the new kernel. I just installed them on the 3.7.3 kernel with no problems and no patches necessary. I am however running 12.04 .

---


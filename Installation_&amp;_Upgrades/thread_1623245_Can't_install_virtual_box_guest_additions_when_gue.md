---
title: "Can't install virtual box guest additions when guets is 10.10"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by Colin@oxford on 2010-11-16
I have installed 10.10 as a virtual machine under my 10.04 host installation.  I have then attempted to install the guest additions to make it more integrated with the host.  When I start the autorun of the guest additions, it tries to compile some programs.   This seems to be a feature of the VBox in 10.04 and worked with 10.04 was also the guest. However, with 10.10 as the guest, I get a compile error, specifically this at the end of vboxadd-install.log:

```

  gcc -Wp,-MD,/tmp/vbox.0/.regops.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include  -I/usr/src/linux-headers-2.6.35-22-generic/arch/x86/include -Iinclude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -fshort-wchar -I/lib/modules/2.6.35-22-generic/build/include -I/tmp/vbox.0/ -I/tmp/vbox.0/include -I/tmp/vbox.0/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DVBOX_WITH_HGCM -DIN_MODULE -DIN_GUEST_R0 -DRT_NO_EXPORT_SYMBOL -DRT_ARCH_X86  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(regops)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxvfs)"  -c -o /tmp/vbox.0/.tmp_regops.o /tmp/vbox.0/regops.c
/tmp/vbox.0/regops.c:511: error: ‘simple_sync_file’ undeclared here (not in a function)
make[2]: *** [/tmp/vbox.0/regops.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxvfs] Error 2

```


What am I missing?

---

### Post by adrian.nistor on 2010-12-01
I've got the same issue too.
Is there anything to workaround this? Thanks!

---


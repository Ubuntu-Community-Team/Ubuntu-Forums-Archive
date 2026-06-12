---
title: "Kernel recompile error.....Please help"
date: 2005-12-02
forum: Installation &amp; Upgrades
---

### Post by test006 on 2005-12-02
Hi,
I am trying to compile my 5.10 kernel to enable sctp (Stream Control Transfer Protocol). This is for my own testing.
I followed all the steps as per Howto. On the last step i.e. when you type the following commnd line:
make-kpkg --initrd --append-to-version=-sctp kernel_image kernel_headers

After a while i get following error:

Inconsistent kallsyms data
Try setting CONFIG_KALLSYMS_EXTRA_PASS
make[1]: *** [vmlinux] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [stamp-build] Error 2

can someone please help.


thanks in advance...

---


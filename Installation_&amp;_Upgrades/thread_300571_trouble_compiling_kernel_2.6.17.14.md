---
title: "trouble compiling kernel 2.6.17.14"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by whomever21 on 2006-11-15
presuming it wouldn't be any different, i used the instructions from [this thread]("http://www.ubuntuforums.org/showthread.php?t=217657") to try my hand at compiling the kernel. it seemed to be going along fine until this:
```

  AR      lib/lib.a
  LD      arch/i386/lib/built-in.o
  CC      arch/i386/lib/bitops.o
  AS      arch/i386/lib/checksum.o
  CC      arch/i386/lib/delay.o
  AS      arch/i386/lib/getuser.o
  CC      arch/i386/lib/memcpy.o
  AS      arch/i386/lib/putuser.o
  CC      arch/i386/lib/strstr.o
  CC      arch/i386/lib/usercopy.o
  AR      arch/i386/lib/lib.a
  GEN     .version
  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
init/built-in.o: In function `try_name':
do_mounts.c:(.text+0x4b8): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `name_to_dev_t':
(.text+0x77f): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `change_floppy':
(.init.text+0x8ea): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `mount_block_root':
(.init.text+0xb75): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `do_header':
initramfs.c:(.init.text+0x4113): undefined reference to `__stack_chk_fail'
arch/i386/kernel/built-in.o:(.text+0x46e6): more undefined references to `__stack_chk_fail' follow
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.17.14'
make: *** [debian/stamp-build-kernel] Error 2

```

any thoughts?

---


---
title: "gcc 4.4.2-1ubuntu3 busted?"
date: 2009-11-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by TerminX on 2009-11-07
```
  CC      kernel/sys.o
  CC      kernel/kmod.o
  CC      kernel/workqueue.o
  CC      kernel/pid.o
kernel/pid.c: In function &#8216;find_pid_ns&#8217;:
kernel/pid.c:299: internal compiler error: in int_cst_value, at tree.c:8305
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.4/README.Bugs> for instructions.
make[2]: *** [kernel/pid.o] Error 1
make[1]: *** [kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.31.5-bfs'
make: *** [debian/stamp/build/kernel] Error 2
```

Previous (karmic) toolchain worked fine.  ICE continues to occur in same location on further executions:

```
make[1]: Entering directory `/usr/src/linux-2.6.31.5-bfs'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
  CALL    scripts/checksyscalls.sh
  CHK     include/linux/compile.h
  VDSOSYM arch/x86/vdso/vdso32-int80-syms.lds
  VDSOSYM arch/x86/vdso/vdso32-sysenter-syms.lds
  VDSOSYM arch/x86/vdso/vdso32-syms.lds
  LD      arch/x86/vdso/built-in.o
  LD      arch/x86/built-in.o
  CC      kernel/pid.o
kernel/pid.c: In function &#8216;find_pid_ns&#8217;:
kernel/pid.c:299: internal compiler error: in int_cst_value, at tree.c:8305
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.4/README.Bugs> for instructions.
make[2]: *** [kernel/pid.o] Error 1
make[1]: *** [kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.31.5-bfs'
make: *** [debian/stamp/build/kernel] Error 2
```

Anyone else running into anything like this?

Edit: just installed the gcc 4.4 packages from Debian unstable and the ICE is no more.  Looks like something in the toolchain in the lucid repos is broken for sure.

---

### Post by rednus on 2009-11-07
I have gcc-4:4.4.1-Ubuntu2 and i get segmentation errors. Looks like this is a known issues and I think I saw a bug reported in LP for this.

---

### Post by jppr on 2009-11-07
> **rednus said:**
> I have gcc-4:4.4.1-Ubuntu2 and i get segmentation errors. Looks like this is a known issues and I think I saw a bug reported in LP for this.

i have gcc-4.4.2-1ubuntu3 without any errors  = )

O Ou... yes i have also gcc-4:4.4.1-Ubuntu2 but no errors...

---

### Post by jhair.tocancipa on 2009-11-14
Same here...

jtocancipa@dell-desktop:~/local/src/linux$ make
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
  CALL    scripts/checksyscalls.sh
  CHK     include/linux/compile.h
  CC [M]  fs/ocfs2/aops.o
  CC [M]  fs/ocfs2/blockcheck.o
  CC [M]  fs/ocfs2/buffer_head_io.o
  CC [M]  fs/ocfs2/dcache.o
  CC [M]  fs/ocfs2/dir.o
fs/ocfs2/dir.c: In function ‘ocfs2_find_dir_space_dx’:
fs/ocfs2/dir.c:4083: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.4/README.Bugs> for instructions.
make[2]: *** [fs/ocfs2/dir.o] Error 1
make[1]: *** [fs/ocfs2] Error 2
make: *** [fs] Error 2

---


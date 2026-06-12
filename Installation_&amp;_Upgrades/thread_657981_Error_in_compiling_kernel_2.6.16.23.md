---
title: "Error in compiling kernel 2.6.16.23"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by snitinbharadwaj on 2008-01-04
Each time when I compile my kernel downloaded from kernel.org I get similar error message in the command **make bzImage**

init/built-in.o: In function `try_name':
/usr/src/linux-2.6.16.23/init/do_mounts.c:116: undefined reference to `__stack_chk_fail'
init/built-in.o: In function `name_to_dev_t':
/usr/src/linux-2.6.16.23/init/do_mounts.c:207: undefined reference to `__stack_chk_fail'
init/built-in.o: In function `change_floppy':
/usr/src/linux-2.6.16.23/init/do_mounts.c:359: undefined reference to `__stack_chk_fail'
init/built-in.o: In function `mount_block_root':
/usr/src/linux-2.6.16.23/init/do_mounts.c:317: undefined reference to `__stack_chk_fail'
init/built-in.o: In function `do_header':
/usr/src/linux-2.6.16.23/init/initramfs.c:206: undefined reference to `__stack_chk_fail'
arch/i386/kernel/built-in.o:/usr/src/linux-2.6.16.23/arch/i386/kernel/ptrace.c:634: more undefined references to `__stack_chk_fail' follow
make: *** [.tmp_vmlinux1] Error 1

its the final step ...
plz ..... help me ...

can any1 tell me whats all going on here ... and please tell me ...
the solution of the problem ....

---

### Post by gaurish on 2008-06-15
Hey I am a newbie and tried to install the 2.6.15 kernel.
I applied a patch of MPLS to this kernel and tried compiling it.

I am also getting the same error .

---


---
title: "Kernel downgrade"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by undefined1_ on 2007-11-10
hi, i'm trying to downgrade install an older kernel on ubuntu 7.04 because i need to test a LKM.

when i try to compile the 2.6.0 kernel i get, this is what i get:

```
# make menuconfig
... everything's ok ...
# make
  HOSTCC  scripts/genksyms/genksyms.o
  SHIPPED scripts/genksyms/lex.c
  SHIPPED scripts/genksyms/parse.h
  SHIPPED scripts/genksyms/keywords.c
  HOSTCC  scripts/genksyms/lex.o
  SHIPPED scripts/genksyms/parse.c
  HOSTCC  scripts/genksyms/parse.o
  HOSTLD  scripts/genksyms/genksyms
  HOSTCC  scripts/split-include
  HOSTCC  scripts/conmakehash
  HOSTCC  scripts/docproc
  HOSTCC  scripts/kallsyms
  CC      scripts/empty.o
  HOSTCC  scripts/mk_elfconfig
  MKELF   scripts/elfconfig.h
  HOSTCC  scripts/file2alias.o
  HOSTCC  scripts/modpost.o
  HOSTLD  scripts/modpost
  HOSTCC  scripts/pnmtologo
  HOSTCC  scripts/bin2c
  SPLIT   include/linux/autoconf.h -> include/config/*
  CC      arch/i386/kernel/asm-offsets.s
  CHK     include/asm-i386/asm_offsets.h
  UPD     include/asm-i386/asm_offsets.h
  CC      init/main.o
  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
  CC      init/do_mounts.o
  CC      init/do_mounts_rd.o
  CC      init/do_mounts_initrd.o
  LD      init/mounts.o
  CC      init/initramfs.o
  LD      init/built-in.o
  HOSTCC  usr/gen_init_cpio
  CPIO    usr/initramfs_data.cpio
  GZIP    usr/initramfs_data.cpio.gz
  AS      usr/initramfs_data.o
  LD      usr/built-in.o
  CC      arch/i386/kernel/process.o
{standard input}: Assembler messages:
{standard input}:1341: Error: suffix or operands invalid for `mov'
{standard input}:1343: Error: suffix or operands invalid for `mov'
{standard input}:1722: Error: suffix or operands invalid for `mov'
{standard input}:1724: Error: suffix or operands invalid for `mov'
{standard input}:1832: Error: suffix or operands invalid for `mov'
{standard input}:1833: Error: suffix or operands invalid for `mov'
{standard input}:1977: Error: suffix or operands invalid for `mov'
{standard input}:1979: Error: suffix or operands invalid for `mov'
{standard input}:2087: Error: suffix or operands invalid for `mov'
{standard input}:2100: Error: suffix or operands invalid for `mov'
make[1]: *** [arch/i386/kernel/process.o] Error 1
make: *** [arch/i386/kernel] Error 2
# 
```

any ideas?
thanks

---


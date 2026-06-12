---
title: "problems with a kernel..."
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by Buio81 on 2007-03-28
I'm installing NCUns ([http://nsl10.csie.nctu.edu.tw/](http://nsl10.csie.nctu.edu.tw/) )on Ubuntu but I have problems with the kernel 
installation.
that's the output when I try to create the deb file for installing the 
kernel:
```
  CHK     usr/initramfs_list
  UPD     usr/initramfs_list
  CPIO    usr/initramfs_data.cpio
  GZIP    usr/initramfs_data.cpio.gz
  AS      usr/initramfs_data.o
  LD      usr/built-in.o
  CC      arch/i386/kernel/process.o
{standard input}: Assembler messages:
{standard input}:787: Error: suffix or operands invalid for `mov'
{standard input}:788: Error: suffix or operands invalid for `mov'
{standard input}:987: Error: suffix or operands invalid for `mov'
{standard input}:988: Error: suffix or operands invalid for `mov'
{standard input}:1061: Error: suffix or operands invalid for `mov'
{standard input}:1062: Error: suffix or operands invalid for `mov'
{standard input}:1134: Error: suffix or operands invalid for `mov'
{standard input}:1135: Error: suffix or operands invalid for `mov'
{standard input}:1224: Error: suffix or operands invalid for `mov'
{standard input}:1236: Error: suffix or operands invalid for `mov'
make[2]: *** [arch/i386/kernel/process.o] Error 1
make[1]: *** [arch/i386/kernel] Error 2
make[1]: Leaving directory `/usr/src/nctuns-kernel-2.6.11'
make: *** [debian/stamp-build-kernel] Error 2
```

---


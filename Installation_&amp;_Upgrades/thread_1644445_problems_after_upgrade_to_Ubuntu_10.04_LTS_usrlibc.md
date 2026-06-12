---
title: "problems after upgrade to Ubuntu 10.04 LTS: /usr/lib/crt1.o: file not recognized"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by marlboroguy58 on 2010-12-13
Hi,
     I have upgraded my ubuntu linux from 8.10 (32bit) to 10.04 LTS(64bit), after which i am unable to compile a 32bit binary, i have installed all the 32 bit dev packages. I get the below error
     
```
bnru01:/data/xrizqur/linux/ramdisk> make all
gcc -Wall -g -O2 -m32  -Iext2fs/include -lext2fs -Lext2fs/lib -I . dumpext2fs.c -o dumpext2fs
/usr/lib/crt1.o: file not recognized: File format not recognized
collect2: ld returned 1 exit status
make: *** [dumpext2fs] Error 1

```
I use a gcc version 4.1.2
```

bnru01:/data/xrizqur/linux/ramdisk> which nm
/sw/st/gnu_compil/gnu/Linux-RH-WS-3/gcc/gcc-4.1.2/bin/nm
bnru01:/data/xrizqur/linux/ramdisk> which gcc
/sw/st/gnu_compil/gnu/Linux-RH-WS-3/gcc/gcc-4.1.2/bin/gcc
bnru01:/data/xrizqur/linux/ramdisk> nm /usr/lib/crt1.o
nm: /usr/lib/crt1.o: File format not recognized
bnru01:/data/xrizqur/linux/ramdisk> nm /usr/lib32/crt1.o
00000000 D __data_start
00000000 W data_start
00000000 R _fp_hw
00000000 R _IO_stdin_used
         U __libc_csu_fini
         U __libc_csu_init
         U __libc_start_main
         U main
00000000 T _start
bnru01:/data/xrizqur/linux/ramdisk> file /usr/lib/crt1.o
/usr/lib/crt1.o: ELF 64-bit LSB relocatable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.15, not stripped
bnru01:/data/xrizqur/linux/ramdisk> file /usr/lib32/crt1.o
/usr/lib32/crt1.o: ELF 32-bit LSB relocatable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.15, not stripped
```]

What do i do to get the 32 bit binary generated?

---


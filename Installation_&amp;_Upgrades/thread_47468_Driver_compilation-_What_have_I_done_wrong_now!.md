---
title: "Driver compilation- What have I done wrong now?!"
date: 2005-07-08
forum: Installation &amp; Upgrades
---

### Post by leezer3 on 2005-07-08
Hi guys,
Anyway, I seem to have sorted out the major problems I was having concerning kernel source for the compilation of drivers, but I still need an idiotproof guide on where I'm going wrong. 
Here's a little of the output from when I try to compile ipw2100 and slmdm (The two drivers I need :rolleyes: )

_SLMDM:_
root@ubuntu:~/slmdm-2.7.10 # make
gcc -Wall -O3 -fomit-frame-pointer -D__KERNEL__ -DMODULE -DEXPORT_SYMTAB -I. -I/ usr/src/linux/include  -DMODVERSIONS --include /usr/src/linux/include/linux/modv ersions.h -o amrmo_init.o -c amrmo_init.c
<command line>:138477907:408: /usr/src/linux/include/linux/modversions.h: No suc h file or directory
In file included from /usr/include/asm/system.h:5,
                 from /usr/include/asm/processor.h:18,
                 from /usr/include/asm/thread_info.h:13,
                 from /usr/src/linux/include/linux/thread_info.h:21,
                 from /usr/src/linux/include/linux/spinlock.h:12,
                 from /usr/src/linux/include/linux/capability.h:45,
                 from /usr/src/linux/include/linux/sched.h:7,
                 from /usr/src/linux/include/linux/module.h:10,
                 from amrmo_init.c:47:
/usr/src/linux/include/linux/kernel.h:72: error: syntax error before "void"
In file included from /usr/src/linux/include/linux/capability.h:45,
                 from /usr/src/linux/include/linux/sched.h:7,
                 from /usr/src/linux/include/linux/module.h:10,
                 from amrmo_init.c:47:
/usr/src/linux/include/linux/spinlock.h:43: error: syntax error before "_spin_tr ylock"
/usr/src/linux/include/linux/spinlock.h:44: error: syntax error before "_write_t rylock"
/usr/src/linux/include/linux/spinlock.h:46: error: conflicting types for `fastca ll'
/usr/src/linux/include/linux/spinlock.h:44: error: previous declaration of `fast call'
/usr/src/linux/include/linux/spinlock.h:46: error: syntax error before "_spin_lo ck"
/usr/src/linux/include/linux/spinlock.h:47: error: syntax error before "_read_lo ck"
/usr/src/linux/include/linux/spinlock.h:48: error: syntax error before "_write_l ock"
/usr/src/linux/include/linux/spinlock.h:50: error: syntax error before "_spin_un lock"
/usr/src/linux/include/linux/spinlock.h:51: error: syntax error before "_read_un lock"
/usr/src/linux/include/linux/spinlock.h:52: error: syntax error before "_write_u nlock"
/usr/src/linux/include/linux/spinlock.h:54: error: conflicting types for `fastca ll'
/usr/src/linux/include/linux/spinlock.h:52: error: previous declaration of `fast call'
/usr/src/linux/include/linux/spinlock.h:54: error: syntax error before "_spin_lo ck_irqsave"
/usr/src/linux/include/linux/spinlock.h:55: error: syntax error before "_read_lo ck_irqsave"
/usr/src/linux/include/linux/spinlock.h:56: error: syntax error before "_write_l ock_irqsave"
/usr/src/linux/include/linux/spinlock.h:58: error: conflicting types for `fastca ll'
/usr/src/linux/include/linux/spinlock.h:56: error: previous declaration of `fast call'
/usr/src/linux/include/linux/spinlock.h:58: error: syntax error before "_spin_lo ck_irq"
/usr/src/linux/include/linux/spinlock.h:59: error: syntax error before "_spin_lo ck_bh"
/usr/src/linux/include/linux/spinlock.h:60: error: syntax error before "_read_lo ck_irq"
/usr/src/linux/include/linux/spinlock.h:61: error: syntax error before "_read_lo ck_bh"
/usr/src/linux/include/linux/spinlock.h:62: error: syntax error before "_write_l ock_irq"
/usr/src/linux/include/linux/spinlock.h:63: error: syntax error before "_write_l ock_bh"
/usr/src/linux/include/linux/spinlock.h:65: error: syntax error before "_spin_un lock_irqrestore"
/usr/src/linux/include/linux/spinlock.h:66: error: syntax error before "_spin_un lock_irq"
/usr/src/linux/include/linux/spinlock.h:67: error: syntax error before "_spin_un lock_bh"
/usr/src/linux/include/linux/spinlock.h:68: error: syntax error before "_read_un lock_irqrestore"
/usr/src/linux/include/linux/spinlock.h:69: error: syntax error before "_read_un lock_irq"
/usr/src/linux/include/linux/spinlock.h:70: error: syntax error before "_read_un lock_bh"
/usr/src/linux/include/linux/spinlock.h:71: error: syntax error before "_write_u nlock_irqrestore"
/usr/src/linux/include/linux/spinlock.h:72: error: syntax error before "_write_u nlock_irq"
/usr/src/linux/include/linux/spinlock.h:73: error: syntax error before "_write_u nlock_bh"
/usr/src/linux/include/linux/spinlock.h:75: error: conflicting types for `fastca ll'
/usr/src/linux/include/linux/spinlock.h:73: error: previous declaration of `fast call'
/usr/src/linux/include/linux/spinlock.h:75: error: syntax error before "_spin_tr ylock_bh"
In file included from /usr/src/linux/include/linux/time.h:7,
                 from /usr/src/linux/include/linux/timex.h:58,
                 from /usr/src/linux/include/linux/sched.h:11,
                 from /usr/src/linux/include/linux/module.h:10,
                 from amrmo_init.c:47:
/usr/src/linux/include/linux/seqlock.h: In function `write_seqlock':
/usr/src/linux/include/linux/seqlock.h:52: warning: implicit declaration of func tion `_spin_lock'
/usr/src/linux/include/linux/seqlock.h: In function `write_sequnlock':
/usr/src/linux/include/linux/seqlock.h:61: warning: implicit declaration of func tion `_spin_unlock'
/usr/src/linux/include/linux/seqlock.h: In function `write_tryseqlock':
/usr/src/linux/include/linux/seqlock.h:66: warning: implicit declaration of func tion `_spin_trylock'
In file included from /usr/include/asm/smp.h:18,
                 from /usr/src/linux/include/linux/smp.h:17,
                 from /usr/src/linux/include/linux/sched.h:23,
                 from /usr/src/linux/include/linux/module.h:10,
                 from amrmo_init.c:47:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/src/linux/include/linux/smp.h:17,
                 from /usr/src/linux/include/linux/sched.h:23,
                 from /usr/src/linux/include/linux/module.h:10,
                 from amrmo_init.c:47:
/usr/include/asm/mpspec.h: At top level:
/usr/include/asm/mpspec.h:8: error: `MAX_MP_BUSSES' undeclared here (not in a fu nction)
/usr/include/asm/mpspec.h:9: error: `MAX_MP_BUSSES' undeclared here (not in a fu nction)
/usr/include/asm/mpspec.h:10: error: `MAX_MP_BUSSES' undeclared here (not in a f unction)
/usr/include/asm/mpspec.h:12: error: `MAX_MP_BUSSES' undeclared here (not in a f unction)
/usr/include/asm/mpspec.h:19: error: `MAX_APICS' undeclared here (not in a funct ion)
/usr/include/asm/mpspec.h:20: error: `MAX_MP_BUSSES' undeclared here (not in a f unction)

_IPW2100_
/home/christopher/ipw2100-1.1.0/ipw2100.c:416: error: invalid lvalue in assignment
/home/christopher/ipw2100-1.1.0/ipw2100.c:416: error: invalid lvalue in assignment
/home/christopher/ipw2100-1.1.0/ipw2100.c:416: warning: left-hand operand of comma expression has no effect
/home/christopher/ipw2100-1.1.0/ipw2100.c:416: warning: left-hand operand of comma expression has no effect
/home/christopher/ipw2100-1.1.0/ipw2100.c:418: error: `dev' has an incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c:418: warning: passing arg 2 of `write_register' makes pointer from integer without a cast
/home/christopher/ipw2100-1.1.0/ipw2100.c:421: error: invalid operands to binary -
/home/christopher/ipw2100-1.1.0/ipw2100.c:422: error: `dev' has an incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c:422: warning: passing arg 2 of `write_register' makes pointer from integer without a cast
/home/christopher/ipw2100-1.1.0/ipw2100.c:423: error: invalid lvalue in assignment
/home/christopher/ipw2100-1.1.0/ipw2100.c:423: error: wrong type argument to increment
/home/christopher/ipw2100-1.1.0/ipw2100.c:423: warning: left-hand operand of comma expression has no effect
/home/christopher/ipw2100-1.1.0/ipw2100.c:425: error: `dev' has an incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c: At top level:
/home/christopher/ipw2100-1.1.0/ipw2100.c:429: error: syntax error before "u8"
/home/christopher/ipw2100-1.1.0/ipw2100.c:430: warning: function declaration isn't a prototype
/home/christopher/ipw2100-1.1.0/ipw2100.c: In function `read_nic_memory':
/home/christopher/ipw2100-1.1.0/ipw2100.c:434: error: `i' redeclared as different kind of symbol
include/linux/wireless.h:497: error: previous declaration of `i'
/home/christopher/ipw2100-1.1.0/ipw2100.c:437: error: invalid operands to binary &
/home/christopher/ipw2100-1.1.0/ipw2100.c:438: error: invalid operands to binary -
/home/christopher/ipw2100-1.1.0/ipw2100.c:442: error: `dev' has an incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c:442: warning: passing arg 2 of `write_register' makes pointer from integer without a cast
/home/christopher/ipw2100-1.1.0/ipw2100.c:443: error: invalid lvalue in assignment
/home/christopher/ipw2100-1.1.0/ipw2100.c:443: warning: comparison between pointer and integer
/home/christopher/ipw2100-1.1.0/ipw2100.c:443: error: wrong type argument to increment
/home/christopher/ipw2100-1.1.0/ipw2100.c:443: error: `buf' undeclared (first use in this function)
/home/christopher/ipw2100-1.1.0/ipw2100.c:443: warning: left-hand operand of comma expression has no effect
/home/christopher/ipw2100-1.1.0/ipw2100.c:445: error: `dev' has an incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c:447: error: invalid operands to binary -
/home/christopher/ipw2100-1.1.0/ipw2100.c:448: error: invalid lvalue in assignment
/home/christopher/ipw2100-1.1.0/ipw2100.c:453: error: `dev' has an incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c:453: warning: passing arg 2 of `write_register' makes pointer from integer without a cast
/home/christopher/ipw2100-1.1.0/ipw2100.c:454: error: invalid lvalue in assignment
/home/christopher/ipw2100-1.1.0/ipw2100.c:455: error: invalid lvalue in assignment
/home/christopher/ipw2100-1.1.0/ipw2100.c:455: error: invalid lvalue in assignment
/home/christopher/ipw2100-1.1.0/ipw2100.c:455: error: invalid lvalue in assignment
/home/christopher/ipw2100-1.1.0/ipw2100.c:455: warning: left-hand operand of comma expression has no effect
/home/christopher/ipw2100-1.1.0/ipw2100.c:455: warning: left-hand operand of comma expression has no effect
/home/christopher/ipw2100-1.1.0/ipw2100.c:457: error: `dev' has an incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c:457: warning: passing arg 2 of `read_register' makes pointer from integer without a cast
/home/christopher/ipw2100-1.1.0/ipw2100.c:460: error: invalid operands to binary -
/home/christopher/ipw2100-1.1.0/ipw2100.c:462: error: `dev' has an incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c:462: warning: passing arg 2 of `write_register' makes pointer from integer without a cast
/home/christopher/ipw2100-1.1.0/ipw2100.c:463: error: invalid lvalue in assignment
/home/christopher/ipw2100-1.1.0/ipw2100.c:463: error: wrong type argument to increment
/home/christopher/ipw2100-1.1.0/ipw2100.c:463: warning: left-hand operand of comma expression has no effect
/home/christopher/ipw2100-1.1.0/ipw2100.c:465: error: `dev' has an incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c: In function `ipw2100_hw_is_adapter_in_system':
/home/christopher/ipw2100-1.1.0/ipw2100.c:470: error: dereferencing pointer to incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c:471: error: dereferencing pointer to incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c: In function `ipw2100_get_ordinal':
/home/christopher/ipw2100-1.1.0/ipw2100.c:478: error: dereferencing pointer to incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c:479: error: `addr' redeclared as different kind of symbol
include/linux/wireless.h:601: error: previous declaration of `addr'
/home/christopher/ipw2100-1.1.0/ipw2100.c:481: error: `u16' undeclared (first use in this function)
/home/christopher/ipw2100-1.1.0/ipw2100.c:481: error: syntax error before "field_len"
/home/christopher/ipw2100-1.1.0/ipw2100.c:488: error: `EINVAL' undeclared (first use in this function)
/home/christopher/ipw2100-1.1.0/ipw2100.c:491: warning: comparison between pointer and integer
/home/christopher/ipw2100-1.1.0/ipw2100.c:492: warning: comparison between pointer and integer
/home/christopher/ipw2100-1.1.0/ipw2100.c:493: error: invalid lvalue in assignment
/home/christopher/ipw2100-1.1.0/ipw2100.c:502: error: dereferencing pointer to incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c:502: error: invalid operands to binary <<
/home/christopher/ipw2100-1.1.0/ipw2100.c:504: error: dereferencing pointer to incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c:506: error: invalid lvalue in assignment
/home/christopher/ipw2100-1.1.0/ipw2100.c:511: warning: comparison between pointer and integer
/home/christopher/ipw2100-1.1.0/ipw2100.c:516: error: dereferencing pointer to incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c:516: error: invalid operands to binary <<
/home/christopher/ipw2100-1.1.0/ipw2100.c:521: error: dereferencing pointer to incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c:522: error: invalid operands to binary <<
/home/christopher/ipw2100-1.1.0/ipw2100.c:526: error: `field_len' undeclared (first use in this function)
/home/christopher/ipw2100-1.1.0/ipw2100.c:526: error: syntax error before ')' token
/home/christopher/ipw2100-1.1.0/ipw2100.c:529: error: syntax error before ')' token
/home/christopher/ipw2100-1.1.0/ipw2100.c:534: error: invalid lvalue in assignment
/home/christopher/ipw2100-1.1.0/ipw2100.c:538: error: invalid lvalue in assignment
/home/christopher/ipw2100-1.1.0/ipw2100.c:543: error: dereferencing pointer to incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c:548: warning: int format, pointer arg (arg 2)
/home/christopher/ipw2100-1.1.0/ipw2100.c: In function `ipw2100_set_ordinal':
/home/christopher/ipw2100-1.1.0/ipw2100.c:557: error: dereferencing pointer to incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c:558: error: `addr' redeclared as different kind of symbol
include/linux/wireless.h:601: error: previous declaration of `addr'
/home/christopher/ipw2100-1.1.0/ipw2100.c:560: warning: comparison between pointer and integer
/home/christopher/ipw2100-1.1.0/ipw2100.c:561: warning: comparison between pointer and integer
/home/christopher/ipw2100-1.1.0/ipw2100.c:562: error: invalid lvalue in assignment
/home/christopher/ipw2100-1.1.0/ipw2100.c:563: error: invalid operands to binary &
/home/christopher/ipw2100-1.1.0/ipw2100.c:563: error: invalid type argument of `->'
/home/christopher/ipw2100-1.1.0/ipw2100.c:564: error: `EINVAL' undeclared (first use in this function)
/home/christopher/ipw2100-1.1.0/ipw2100.c:567: error: dereferencing pointer to incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c:567: error: invalid operands to binary <<
/home/christopher/ipw2100-1.1.0/ipw2100.c:570: error: dereferencing pointer to incomplete type
/home/christopher/ipw2100-1.1.0/ipw2100.c:572: error: invalid lvalue in assignment
/home/christopher/ipw2100-1.1.0/ipw2100.c:577: error: invalid operands to binary &
/home/christopher/ipw2100-1.1.0/ipw2100.c:577: error: invalid type argument of `->'
/home/christopher/ipw2100-1.1.0/ipw2100.c:578: warning: comparison between pointer and integer
/home/christopher/ipw2100-1.1.0/ipw2100.c: At top level:
/home/christopher/ipw2100-1.1.0/ipw2100.c:584: error: syntax error before "size_t"
/home/christopher/ipw2100-1.1.0/ipw2100.c:586: warning: function declaration isn't a prototype
/home/christopher/ipw2100-1.1.0/ipw2100.c: In function `snprint_line':
/home/christopher/ipw2100-1.1.0/ipw2100.c:590: error: `buf' undeclared (first use in this function)
/home/christopher/ipw2100-1.1.0/ipw2100.c:590: error: `ofs' undeclared (first use in this function)
/home/christopher/ipw2100-1.1.0/ipw2100.c: At top level:
/home/christopher/ipw2100-1.1.0/ipw2100.c:619: warning: type defaults to `int' in declaration of `u8'
/home/christopher/ipw2100-1.1.0/ipw2100.c:619: error: syntax error before '*' token
/home/christopher/ipw2100-1.1.0/ipw2100.c:620: warning: function declaration isn't a prototype
/home/christopher/ipw2100-1.1.0/ipw2100.c: In function `printk_buf':
/home/christopher/ipw2100-1.1.0/ipw2100.c:622: error: function `ofs' is initialized like a variable
/home/christopher/ipw2100-1.1.0/ipw2100.c:622: error: `ofs' used prior to declaration
/home/christopher/ipw2100-1.1.0/ipw2100.c:623: error: invalid operands to binary &
/home/christopher/ipw2100-1.1.0/ipw2100.c:628: error: array subscript is not an integer
/home/christopher/ipw2100-1.1.0/ipw2100.c:629: warning: comparison of distinct pointer types lacks a cast
/home/christopher/ipw2100-1.1.0/ipw2100.c:630: error: invalid lvalue in assignment


Thanks in advance.

-Leezer-

---

### Post by Soulfly on 2005-07-08
Looks like you dont have the kernel-headers or maybe a link that should point there is missing

```

$ dlocate modversions.h
linux-headers-2.6.11-1: /usr/src/linux-headers-2.6.11-1/include/config/modversions.h

```

You might want another package than me depending on your kernel version.

Other things you might try to get past these problems is to use "auto-apt run ./make" / "auto-apt install <file>" [tries to find/install paackages that provides a certain file] and/or "apt-get build-dep <package>" [install all build-dependancies to a package]

---


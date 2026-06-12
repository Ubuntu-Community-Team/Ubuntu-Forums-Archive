---
title: "Kernel Compiler error! Ubuntu sources"
date: 2006-05-16
forum: Installation &amp; Upgrades
---

### Post by dmb on 2006-05-16
Hey, i'm using the default linux-sources that ubuntu provides in the repositories, and iv had no problem compiling the stock kernel, but when i compile a customized kernel where i changed a bunch of options, this is what happens: 

```
drivers/built-in.o:(.bss+0x13874): multiple definition of `debug'
arch/i386/kernel/built-in.o:: first defined here
drivers/built-in.o: In function `dump_stack':
: multiple definition of `dump_stack'
arch/i386/kernel/built-in.o:: first defined here
ld: Warning: size of symbol `dump_stack' changed from 22 in arch/i386/kernel/built-in.o to 37 in drivers/built-in.o
fs/built-in.o: In function `id_test_and_set':
group.c:(.text+0x1da8a3): undefined reference to `dlm_debug_dump'

```
And the rest is just more linking errors, not important. The config file is here: [http://dmb.hey.nu/projects/temp/config.txt](http://dmb.hey.nu/projects/temp/config.txt) . Please help! What did I do wrong?

---


---
title: "how to install kernel module of asm ?"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by krzys1825 on 2008-01-25
Is any of you succeeded to install asm functionality of oracle 10g server ? I have been trying to do it for a few weeks but without any results. There is complete instruction on unbreakable linux webpage how to do it but for redhat - it does not work on ubuntu. I was able to convert it to debian package but kernel module from that package cannot be loaded because of "incorrect format"
There are also sources of that module avaliable on UL. So I tried to compile it manually but after "make"  it returns such errors:
(...)
/home/oracle/Pulpit/asm/source/oracleasm-2.0.4/kernel/oracleasm.c: In function ‘init_asmdisk_once’:
/home/oracle/Pulpit/asm/source/oracleasm-2.0.4/kernel/oracleasm.c:315: error: ‘SLAB_CTOR_VERIFY’ undeclared (first use in this function)
/home/oracle/Pulpit/asm/source/oracleasm-2.0.4/kernel/oracleasm.c:315: error: (Each undeclared identifier is reported only once
/home/oracle/Pulpit/asm/source/oracleasm-2.0.4/kernel/oracleasm.c:315: error: for each function it appears in.)
/home/oracle/Pulpit/asm/source/oracleasm-2.0.4/kernel/oracleasm.c:315: error: ‘SLAB_CTOR_CONSTRUCTOR’ undeclared (first use in this function)
/home/oracle/Pulpit/asm/source/oracleasm-2.0.4/kernel/oracleasm.c: At top level:
/home/oracle/Pulpit/asm/source/oracleasm-2.0.4/kernel/oracleasm.c:474: warning: ‘kmem_cache_t’ is deprecated
/home/oracle/Pulpit/asm/source/oracleasm-2.0.4/kernel/oracleasm.c: In function ‘init_once’:
/home/oracle/Pulpit/asm/source/oracleasm-2.0.4/kernel/oracleasm.c:478: error: ‘SLAB_CTOR_VERIFY’ undeclared (first use in this function)
/home/oracle/Pulpit/asm/source/oracleasm-2.0.4/kernel/oracleasm.c:478: error: ‘SLAB_CTOR_CONSTRUCTOR’ undeclared (first use in this function)
(...)

have you got any ideas how to creat/load/use this module ?




my configuration: ubuntu7.10 x64  and oracle 10.2 64bit

---

### Post by Mikecore on 2008-01-27
Here is a link that might be able to help you. once there there are links to other pages that may also help. 

```

https://help.ubuntu.com/community/Oracle10g?highlight=%28oracle%29

```

---


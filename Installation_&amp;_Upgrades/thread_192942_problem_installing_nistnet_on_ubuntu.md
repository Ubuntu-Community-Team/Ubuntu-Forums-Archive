---
title: "problem installing nistnet on ubuntu"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by rahulsurya on 2006-06-09
i installed kernel 2.6.16.20 using HOW_TO guide from this forum.

It was success.

Now i'm trying to install nistnet and when i type make command i get following errors:

when i type make command i get following error:

gcc -m32 -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -O2 -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -march=i486 -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -D__KERNEL__ -fno-common -I. -I../include -DDEVHITBOX=\"/dev/hitbox\" -DHITMAJOR=62 -DHITMINOR=0 -DDEVNISTNET=\"/dev/nistnet\" -DNISTNETMAJOR=62 -DNISTNETMINOR=1 -DDEVMUNGEBOX=\"/dev/mungebox\" -DMUNGEMAJOR=63 -DDEVSPYBOX=\"/dev/spybox\" -DSPYMAJOR=64 -DCONFIG_ECN -DCONFIG_COS -DCONFIG_DELAYSTART -DCONFIG_RTC_AGGRESSIVE -fno-common -I. -I../include -DDEVHITBOX=\"/dev/hitbox\" -DHITMAJOR=62 -DHITMINOR=0 -DDEVNISTNET=\"/dev/nistnet\" -DNISTNETMAJOR=62 -DNISTNETMINOR=1 -DDEVMUNGEBOX=\"/dev/mungebox\" -DMUNGEMAJOR=63 -DDEVSPYBOX=\"/dev/spybox\" -DSPYMAJOR=64 -DCONFIG_ECN -DCONFIG_COS -DCONFIG_DELAYSTART -DCONFIG_RTC_AGGRESSIVE -fno-common -I/lib/modules/2.6.16.20rahul/build/include -I/home/rahul/Desktop/nistnet-3.0a/kernel -I/home/rahul/Desktop/nistnet-3.0a/kernel/../include -DDEVHITBOX=\"/dev/hitbox\" -DHITMAJOR=62 -DHITMINOR=0 -DDEVNISTNET=\"/dev/nistnet\" -DNISTNETMAJOR=62 -DNISTNETMINOR=1 -DDEVMUNGEBOX=\"/dev/mungebox\" -DMUNGEMAJOR=63 -DDEVSPYBOX=\"/dev/spybox\" -DSPYMAJOR=64 -DCONFIG_ECN -DCONFIG_COS -DCONFIG_DELAYSTART -DCONFIG_RTC_AGGRESSIVE -fno-common -DUSE_EXPERIMENTAL -DDISTRIBUTION_NAME="\"experimental\"" -c -o /home/rahul/Desktop/nistnet-3.0a/kernel/tabledist.o /home/rahul/Desktop/nistnet-3.0a/kernel/../math/tabledist.c
In file included from /lib/modules/2.6.16.20rahul/build/include/linux/rwsem.h:27,
from /lib/modules/2.6.16.20rahul/build/include/asm/semaphore.h:42,
from /lib/modules/2.6.16.20rahul/build/include/linux/sched.h:20,
from /lib/modules/2.6.16.20rahul/build/include/asm/irq.h:14,
from /home/rahul/Desktop/nistnet-3.0a/kernel/../include/kincludes.h:126,
from /home/rahul/Desktop/nistnet-3.0a/kernel/../math/tabledist.c:10:
/lib/modules/2.6.16.20rahul/build/include/asm/rwsem.h: In function ‘__down_read’:
/lib/modules/2.6.16.20rahul/build/include/asm/rwsem.h:105: error: syntax error before ‘KBUILD_BASENAME’
/lib/modules/2.6.16.20rahul/build/include/asm/rwsem.h: In function ‘__down_write’:
/lib/modules/2.6.16.20rahul/build/include/asm/rwsem.h:157: error: syntax error before ‘KBUILD_BASENAME’
/lib/modules/2.6.16.20rahul/build/include/asm/rwsem.h: In function ‘__up_read’:
/lib/modules/2.6.16.20rahul/build/include/asm/rwsem.h:194: error: syntax error before ‘KBUILD_BASENAME’
/lib/modules/2.6.16.20rahul/build/include/asm/rwsem.h:188: warning: unused variable ‘tmp’
/lib/modules/2.6.16.20rahul/build/include/asm/rwsem.h: In function ‘__up_write’:/lib/modules/2.6.16.20rahul/build/include/asm/rwsem.h:220: error: syntax error before ‘KBUILD_BASENAME’
/lib/modules/2.6.16.20rahul/build/include/asm/rwsem.h: In function ‘__downgrade_write’:
/lib/modules/2.6.16.20rahul/build/include/asm/rwsem.h:245: error: syntax error before ‘KBUILD_BASENAME’
In file included from /lib/modules/2.6.16.20rahul/build/include/linux/sched.h:20,
from /lib/modules/2.6.16.20rahul/build/include/asm/irq.h:14,
from /home/rahul/Desktop/nistnet-3.0a/kernel/../include/kincludes.h:126,
from /home/rahul/Desktop/nistnet-3.0a/kernel/../math/tabledist.c:10:
/lib/modules/2.6.16.20rahul/build/include/asm/semaphore.h: In function ‘down’:
/lib/modules/2.6.16.20rahul/build/include/asm/semaphore.h:105: error: syntax error before ‘KBUILD_BASENAME’
/lib/modules/2.6.16.20rahul/build/include/asm/semaphore.h: In function ‘down_interruptible’:
/lib/modules/2.6.16.20rahul/build/include/asm/semaphore.h:130: error: syntax error before ‘KBUILD_BASENAME’
/lib/modules/2.6.16.20rahul/build/include/asm/semaphore.h: In function ‘down_trylock’:
/lib/modules/2.6.16.20rahul/build/include/asm/semaphore.h:155: error: syntax error before ‘KBUILD_BASENAME’
/lib/modules/2.6.16.20rahul/build/include/asm/semaphore.h: In function ‘up’:
/lib/modules/2.6.16.20rahul/build/include/asm/semaphore.h:179: error: syntax error before ‘KBUILD_BASENAME’
make[3]: *** [/home/rahul/Desktop/nistnet-3.0a/kernel/tabledist.o] Error 1
make[2]: *** [_module_/home/rahul/Desktop/nistnet-3.0a/kernel] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.16.20'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/rahul/Desktop/nistnet-3.0a/kernel'
make: *** [sub_dirs] Error 2



can anyone help me solving this error. I went through semaphore.h bt cldnt get any solution.

---

### Post by ltshfwjt on 2006-09-19
Change nistnet/Config: EXTRA_CFLAGS += $(OURINCS) $(DEVDEFS) -fno-common
to
EXTRA_CFLAGS += $(OURINCS) $(DEVDEFS) -fno-common -DKBUILD_MODNAME=\"nistnet\" -DKBUILD_BASENAME=\"nistnet\"

Enjoy it!

---


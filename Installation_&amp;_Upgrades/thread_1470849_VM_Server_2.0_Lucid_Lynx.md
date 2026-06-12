---
title: "VM Server 2.0 Lucid Lynx"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by lynwode on 2010-05-03
Hi,
I have just upgraded to 10.04 and VM Server 2.0 has stopped working. I have followed the install guide here: [http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html ]("http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html")that I used for karmic but it does not work - unsuprisigly.

The following errors:


In file included from /usr/lib/vmware/modules/source/vmci-only/./include/vmware.h:38,
                 from /usr/lib/vmware/modules/source/vmci-only/linux/driver.c:58:
/usr/lib/vmware/modules/source/vmci-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /usr/lib/vmware/modules/source/vmci-only/./common/vmciCommonInt.h:34,
                 from /usr/lib/vmware/modules/source/vmci-only/linux/driver.c:65:
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:460:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:551:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:640:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:729:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:816:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:903:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:986:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:1069:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:1313:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:1796:7: warning: "_MSC_VER" is not defined
  CC [M]  /usr/lib/vmware/modules/source/vmci-only/linux/driverLog.o
In file included from /usr/lib/vmware/modules/source/vmci-only/./include/vm_assert.h:45,
                 from /usr/lib/vmware/modules/source/vmci-only/linux/driverLog.h:33,
                 from /usr/lib/vmware/modules/source/vmci-only/linux/driverLog.c:31:
/usr/lib/vmware/modules/source/vmci-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
  CC [M]  /usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.o
In file included from /usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c:47:
/usr/lib/vmware/modules/source/vmci-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c:48:
/usr/lib/vmware/modules/source/vmci-only/./include/pgtbl.h: In function ‘PgtblVa2MPN’:
/usr/lib/vmware/modules/source/vmci-only/./include/pgtbl.h:301: error: dereferencing pointer to incomplete type
/usr/lib/vmware/modules/source/vmci-only/./include/pgtbl.h: In function ‘PgtblVa2Page’:
/usr/lib/vmware/modules/source/vmci-only/./include/pgtbl.h:373: error: dereferencing pointer to incomplete type
In file included from /usr/lib/vmware/modules/source/vmci-only/./include/vmci_queue_pair.h:36,
                 from /usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c:56:
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:460:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:551:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:640:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:729:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:816:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:903:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:986:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:1069:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:1313:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/./include/vm_atomic.h:1796:7: warning: "_MSC_VER" is not defined
/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c: In function ‘VMCIHost_SignalCall’:
/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c:320: error: ‘TASK_NORMAL’ undeclared (first use in this function)
/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c:320: error: (Each undeclared identifier is reported only once
/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c:320: error: for each function it appears in.)
/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c: In function ‘VMCIHost_WaitForCallLocked’:
/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c:362: error: dereferencing pointer to incomplete type
/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c:362: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c:370: error: implicit declaration of function ‘schedule’
/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c:378: error: dereferencing pointer to incomplete type
/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c:378: error: ‘TASK_RUNNING’ undeclared (first use in this function)
/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c:382: error: implicit declaration of function ‘signal_pending’
/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c: In function ‘VMCI_SignalEvent’:
/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c:674: error: ‘TASK_NORMAL’ undeclared (first use in this function)
/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c: In function ‘VMCI_WaitOnEvent’:
/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c:704: error: dereferencing pointer to incomplete type
/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c:704: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c:716: error: dereferencing pointer to incomplete type
/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.c:716: error: ‘TASK_RUNNING’ undeclared (first use in this function)
make[2]: *** [/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.o] Error 1
make[1]: *** [_module_/usr/lib/vmware/modules/source/vmci-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-server'
make: *** [vmci.ko] Error 2
Sorry, problem compiling the vmci module after it was patched
You must restore from this backup directory:
/usr/lib/vmware/modules/source-backup


Help - has anyone got this working yet or any ideas on what I need to do

Cheers,
Tim.

---

### Post by uberlinuxnerd on 2010-05-03
> **lynwode said:**
> Hi,
---> SNIP
make[2]: *** [/usr/lib/vmware/modules/source/vmci-only/linux/vmciKernelIf.o] Error 1
make[1]: *** [_module_/usr/lib/vmware/modules/source/vmci-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-server'
make: *** [vmci.ko] Error 2
Sorry, problem compiling the vmci module after it was patched
You must restore from this backup directory:
/usr/lib/vmware/modules/source-backup
---> SNIP


Reinstall the VMWare Tools and recompile the modules!

---

### Post by lynwode on 2010-05-03
Resolved by this guide:

[http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/]("http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/")

---


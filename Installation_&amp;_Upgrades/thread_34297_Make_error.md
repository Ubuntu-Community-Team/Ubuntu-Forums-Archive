---
title: "Make error"
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by derkins1 on 2005-05-14
The saga to get online via my Sagem Fast 800 adsl modem continues. (Fast8x0_3-0-6.tgz from Sagem) Can anyone understand and help with the following? It is quite long! (*,) 

root@ubuntu:/tmp/eagle-usb/eagle-usb-src # make
make -C driver && \
make -C pppoa && \
make -C utils/scripts && \
make -C utils/eagleconnect && \
make -C doc
make[1]: Entering directory `/tmp/eagle-usb/eagle-usb-src/driver'
if test ! -f .depend ; then make dep ; exit 0 ; fi
make[2]: Entering directory `/tmp/eagle-usb/eagle-usb-src/driver'
cc -DLINUX -D__KERNEL__ -DMODULE -I/usr/src/linux/include '-DEAGLEUSBVERSION="1.9.9"' -Wall -Wstrict-prototypes -fomit-frame-pointer -fno-strict-aliasing -pipe  -mpreferred-stack-boundary=2 -O2 -M *.c > .depend
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from Dsp.c:28:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from Dsp.c:28:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
In file included from /usr/include/linux/irq.h:20,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/usb.h:14,
                 from Adiutil.h:53,
                 from Dsp.c:28:
/usr/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from eu_boot_sm.h:32,
                 from eu_boot_sm.c:31:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from eu_boot_sm.h:32,
                 from eu_boot_sm.c:31:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
In file included from /usr/include/linux/irq.h:20,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/usb.h:14,
                 from Adiutil.h:53,
                 from eu_boot_sm.h:32,
                 from eu_boot_sm.c:31:
/usr/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from eu_eth.c:26:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from eu_eth.c:26:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
In file included from /usr/include/linux/irq.h:20,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/usb.h:14,
                 from Adiutil.h:53,
                 from eu_eth.c:26:
/usr/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from eu_main.c:34:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from eu_main.c:34:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
In file included from /usr/include/linux/irq.h:20,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/usb.h:14,
                 from Adiutil.h:53,
                 from eu_main.c:34:
/usr/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from eu_msg.c:27:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from eu_msg.c:27:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
In file included from /usr/include/linux/irq.h:20,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/usb.h:14,
                 from Adiutil.h:53,
                 from eu_msg.c:27:
/usr/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from eu_utils.c:27:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from eu_utils.c:27:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
In file included from /usr/include/linux/irq.h:20,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/usb.h:14,
                 from Adiutil.h:53,
                 from eu_utils.c:27:
/usr/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzo e.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from Me.c:119:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from Me.c:119:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
In file included from /usr/include/linux/irq.h:20,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/usb.h:14,
                 from Adiutil.h:53,
                 from Me.c:119:
/usr/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from Mpoa.c:34:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from Mpoa.c:34:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
In file included from /usr/include/linux/irq.h:20,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/usb.h:14,
                 from Adiutil.h:53,
                 from Mpoa.c:34:
/usr/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from Oam.c:20:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from Oam.c:20:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
In file included from /usr/include/linux/irq.h:20,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/usb.h:14,
                 from Adiutil.h:53,
                 from Oam.c:20:
/usr/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from Pipes.c:30:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from Pipes.c:30:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
In file included from /usr/include/linux/irq.h:20,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/usb.h:14,
                 from Adiutil.h:53,
                 from Pipes.c:30:
/usr/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from Sar.c:27:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from Sar.c:27:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
In file included from /usr/include/linux/irq.h:20,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/usb.h:14,
                 from Adiutil.h:53,
                 from Sar.c:27:
/usr/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from Sm.c:27:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from Sm.c:27:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
In file included from /usr/include/linux/irq.h:20,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/usb.h:14,
                 from Adiutil.h:53,
                 from Sm.c:27:
/usr/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from Uni.c:27:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from Uni.c:27:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
In file included from /usr/include/linux/irq.h:20,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/usb.h:14,
                 from Adiutil.h:53,
                 from Uni.c:27 
/usr/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
make[2]: *** [dep] Error 1
make[2]: Leaving directory `/tmp/eagle-usb/eagle-usb-src/driver'
cc -DLINUX -D__KERNEL__ -DMODULE -I/usr/src/linux/include '-DEAGLEUSBVERSION="1.9.9"' -Wall -Wstrict-prototypes -fomit-frame-pointer -fno-strict-aliasing -pipe  -mpreferred-stack-boundary=2 -O2   -c -o eu_main.o eu_main.c
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from eu_main.c:34:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from eu_main.c:34:
/usr/include/asm/mpspec.h:8: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:9: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:10: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:12: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:19: error: `MAX_APICS' undeclared here (not in a function)
/usr/include/asm/mpspec.h:20: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:20: error: conflicting types for `mp_bus_id_to_type'
/usr/include/asm/mpspec.h:8: error: previous declaration of `mp_bus_id_to_type'
/usr/include/asm/mpspec.h:22: error: `MAX_IRQ_SOURCES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:24: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:24: error: conflicting types for `mp_bus_id_to_pci_bus'
/usr/include/asm/mpspec.h:12: error: previous declaration of `mp_bus_id_to_pci_bus'
/usr/include/asm/mpspec.h:54: error: `MAX_APICS' undeclared here (not in a function)
In file included from /usr/include/asm/smp.h:20,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from eu_main.c:34:
/usr/include/asm/io_apic.h:120: error: `MAX_IRQ_SOURCES' undeclared here (not in a function)
/usr/include/asm/io_apic.h:120: error: conflicting types for `mp_irqs'
/usr/include/asm/mpspec.h:22: error: previous declaration of `mp_irqs'
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/topology.h:33,
                 from /usr/include/linux/mmzone.h:296,
                 from /usr/include/linux/gfp.h:4,
                 from /usr/include/linux/slab.h:15,
                 from Adiutil.h:51,
                 from eu_main.c:34:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
In file included from /usr/include/linux/irq.h:20,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/usb.h:14,
                 from Adiutil.h:53,
                 from eu_main.c:34:
/usr/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/usb.h:14,
                 from Adiutil.h:53,
                 from eu_main.c:34:
/usr/include/linux/irq.h:70: error: `NR_IRQS' undeclared here (not in a function)
In file included from /usr/include/linux/irq.h:72,                  from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/usb.h:14,
                 from Adiutil.h:53,
                 from eu_main.c:34:
/usr/include/asm/hw_irq.h:28: error: `NR_IRQS' undeclared here (not in a function)
/usr/include/asm/hw_irq.h:31: error: `NR_IRQS' undeclared here (not in a function)
make[1]: *** [eu_main.o] Error 1
make[1]: Leaving directory `/tmp/eagle-usb/eagle-usb-src/driver'
make: *** [build] Error 2
root@ubuntu:/tmp/eagle-usb/eagle-usb-src # ]

---

### Post by alastair on 2005-05-14
Do you have the file "mach_mpspec.h"?

I have it installed as part of the linux headers package - on my system :

linux-headers-2.6.10-5

Similarly with the other missing headers.

Do you have this package? Check :

dpkg -l "*linux-headers*"

---

### Post by derkins1 on 2005-05-14
Thanks. I guess not, What next? please consider I am a n00b.

stuart@ubuntu:~$ cd /
stuart@ubuntu:/$ dpkg -l "*linux-headers*"
No packages found matching *linux-headers*.
stuart@ubuntu:/$ cd /
stuart@ubuntu:/$ su root
Password:
root@ubuntu:/ # dpkg -l "*linux-headers*"
No packages found matching *linux-headers*.
root@ubuntu:/ #
root@ubuntu:/ #

---

### Post by Maestro23 on 2005-05-14
[QUOTE=derkins1]Thanks. I guess not, What next? please consider I am a n00b.

stuart@ubuntu:~$ cd /
stuart@ubuntu:/$ dpkg -l "*linux-headers*"
No packages found matching *linux-headers*.
stuart@ubuntu:/$ cd /
stuart@ubuntu:/$ su root
Password:
root@ubuntu:/ # dpkg -l "*linux-headers*"
No packages found matching *linux-headers*.
root@ubuntu:/ #
root@ubuntu:/ #[/QUOTE]

If you followed the Ubuntu Guide(link in my sig), and enabled the extras repositories, you will find the linux headers.  I just did a search via Synaptic and they were there.  Try following the steps in the guide first, and see what happens.

---

### Post by derkins1 on 2005-05-14
Thanks. To be sure, I'm checking 'Q: How to add extra repositories?'

It looks like it will use the apt-get command which I understand gets stuff via the web. The issues I'm having are connected with installing my adsl modem so I can't get online with Ubuntu yet.

I have mounted my windows HD so if I can download the necessary files and install from there it would be great.

---

### Post by Maestro23 on 2005-05-14
[QUOTE=derkins1]Thanks. To be sure, I'm checking 'Q: How to add extra repositories?'

It looks like it will use the apt-get command which I understand gets stuff via the web. The issues I'm having are connected with installing my adsl modem so I can't get online with Ubuntu yet.

I have mounted my windows HD so if I can download the necessary files and install from there it would be great.[/QUOTE]

I did a quick forum search of **ADSL modem install** and it brought up some threads dealing with setting up a ADSL modem.  Run that quick search and see if any of those threads can help you.  Sorry I can't be more help with the modem, I'm  running Comcast broadband myself. Good luck man...

---


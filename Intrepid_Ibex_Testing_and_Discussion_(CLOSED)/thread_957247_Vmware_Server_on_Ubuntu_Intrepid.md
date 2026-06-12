---
title: "Vmware Server on Ubuntu Intrepid"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Gwrtheyrn on 2008-10-24
hey

i tried to install vmware-server on ubuntu 8.10. first of all, i saw that vmware-server used to be in the cannonical commercial repos. as far as i heard, those were replaced with the partner repos. but i couldn't find the vmware-server package there... is it still contained in any ubuntu repo?

well, as i couldn't find it anywhere in the repos, i downloaded the tar.gz from vmware.com and installed it, but when i try to build the kernel modules it gave me some error messages.

```
Building the vmmon module.

Using 2.6.x kernel build system.
make: Gehe in Verzeichnis '/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/paravirt.h:7,
                 from include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from include/asm/system.h:11,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:12:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:71:
/tmp/vmware-config0/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config0/vmmon-only/linux/driver.c:146: Fehler: unbekanntes Feld »nopage« in Initialisierung angegeben
/tmp/vmware-config0/vmmon-only/linux/driver.c:147: Warnung: Initialisierung von inkompatiblem Zeigertyp
/tmp/vmware-config0/vmmon-only/linux/driver.c:150: Fehler: unbekanntes Feld »nopage« in Initialisierung angegeben
/tmp/vmware-config0/vmmon-only/linux/driver.c:151: Warnung: Initialisierung von inkompatiblem Zeigertyp
/tmp/vmware-config0/vmmon-only/linux/driver.c: In Funktion »LinuxDriver_Ioctl«:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1670: Fehler: zu viele Argumente für Funktion »smp_call_function«
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Fehler 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vmmon.ko] Fehler 2
make: Verlasse Verzeichnis '/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

(sorry, german os)

anyone got this running on intrepid?

---

### Post by Gwrtheyrn on 2008-10-24
fyi, i tried vmware server 2.0, which worked except for the vsock module. i guess that's why i could start the virtual machines, but had no console to look at them. so i removed it and installed vmware server 1.0.7, which didn't work at first. i got it to run with a patch, but then the arrow keys didn't work... finally i found the vmware player 2.5 working at first glance... but still the same problem, many arrow keys weren't mapped correctly.

i guess i'll wait until there's a newer version of vmware, or is there anything else i could do?

---

### Post by fjgaude on 2008-10-24
I've tried to bet VMware server and 8.10 to work without success... post this here about a week ago with no replies... so we can just wait and see what happens... from the errors it looks like gcc issues along with vmware being compiled with a different one.

We wait, with patience!

---


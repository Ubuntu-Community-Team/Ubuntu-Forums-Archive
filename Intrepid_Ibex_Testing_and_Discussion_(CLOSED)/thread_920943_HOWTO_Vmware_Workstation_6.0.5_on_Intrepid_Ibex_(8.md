---
title: "HOWTO: Vmware Workstation 6.0.5 on Intrepid Ibex (8.10)"
date: 2008-09-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by [Neurotic] on 2008-09-15
I think this came out yesterday, but I ran around everywhere looking for it today, and figured I would share.

This was originally posted [here]("http://groups.google.com/group/vmkernelnewbies/browse_thread/thread/449f5d7d0dbc2e4a")
Steps to install.

[LIST=1]
[*]Install Vmware workstation normally, vmware-config.pl will fail.
[*]Download the [vmmon.tar]("http://forum.ubuntu.org.cn/download.php?id=42579&sid=d3e2a53288e88443a3a513ec85e99ba0"), [vmnet.tar]("http://forum.ubuntu.org.cn/download.php?id=42577&sid=d3e2a53288e88443a3a513ec85e99ba0") and [vmblock.tar]("http://forum.ubuntu.org.cn/download.php?id=42578&sid=d3e2a53288e88443a3a513ec85e99ba0") to /usr/lib/vmware/modules/source 
[*]run sudo ./vmware-config.pl
[/LIST]

Seems to be pretty much it so far.

Enjoy.

---

### Post by moremix on 2008-09-20
Hello,

I am having problems installing VMWare 6.0.4 or 6.0.5 in Intrepid because the vmmon module won't compile.  I have read that it may be due to the recent change in the kernel (2.6.26 to 2.7.27).  Can you tell me what kernel you used ?  The patches don't seem to make a difference either...

---

### Post by [Neurotic] on 2008-09-21
I'm using Kernel 2.6.27-3, and it works.

---

### Post by moremix on 2008-09-25
I just upgraded everything on my laptop and it still doesn't function.  I get the following error; any ideas of what's going wrong or in which way to start searching for the answer?  Thx

---------------

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.27-4-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-4-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/x86.h:24,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:84:
/tmp/vmware-config0/vmmon-only/./include/x86paging.h:61:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/pda.h:8,
                 from include/asm/current.h:19,
                 from include/asm/processor.h:15,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:12:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:115:
/tmp/vmware-config0/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-4-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

---

### Post by [Neurotic] on 2008-09-25
moremix - looks like you haven't applied the patches.

---

### Post by chefweb on 2008-09-25
VMware 6.5 is out, try this! .. it's faster then 6.05

---

### Post by [Neurotic] on 2008-09-25
@chefweb, I looked at 6.5, but don't the same issue with the .27 kernel still apply?

I'm also curious, do the still have debugging turned on with 6.5? I tried a beta a while back, and with debugging enabled, vm's just craaaawled.

---

### Post by [Neurotic] on 2008-09-25
--accidentally double posted. Please ignore.

---

### Post by rbmorse on 2008-09-25
VMWare workstation 6.5 works fine on 2.6.27-4 here (IA-32)

---

### Post by chefweb on 2008-09-26
debugging is now disabled in the final version

---

### Post by [Neurotic] on 2008-09-26
Oh! I didn't realise it had been released! Thanks for that.

---

### Post by MoonPhoenix on 2008-10-09
Since the latest round of updates yesterday I am now unable to compile the modules again. Due to the installer segfaulting

Console output
--------------
Stopping VMware services:
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Blocking file system                                                done
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make -C /lib/modules/2.6.27-rc9-tpc3/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-source-2.6.27'
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/hashFunc.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-root/modules/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-root/modules/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-root/modules/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-source-2.6.27'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
VMWARE_LD_LIBRARY_PATH is already set, but it will be overridden.
VMWARE_LD_PRELOAD is already set, but it will be overridden.
VMWARE_PANGO_RC_FILE is already set, but it will be overridden.
VMWARE_GDK_PIXBUF_MODULE_FILE is already set, but it will be overridden.
VMWARE_GTK_IM_MODULE_FILE is already set, but it will be overridden.
VMWARE_FONTCONFIG_PATH is already set, but it will be overridden.
VMWARE_GTK2_RC_FILES is already set, but it will be overridden.
VMWARE_GTK_PATH is already set, but it will be overridden.
/usr/lib/vmware/installer/vmware-installer: line 27: 17578 Segmentation fault      (core dumped) "$PYTHON" "$VMWARE_INSTALLER"/vmware-installer.py "$@"

Logfile Output
--------------
Oct 09 10:40:36.519: app| Log for VMware Workstation pid=16531 version=6.5.0 build=build-118166 option=Release
Oct 09 10:40:36.520: app| Host codepage=UTF-8 encoding=UTF-8
Oct 09 10:40:36.520: app| Logging to /tmp/vmware-root/setup-16531.log
Oct 09 10:40:45.394: app| Extracting the sources of the vmmon module.
Oct 09 10:40:45.412: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.27-rc9-tpc3/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.3.2
Oct 09 10:40:49.860: app| The vmmon module loads perfectly in the running kernel.
Oct 09 10:40:49.860: app| 
Oct 09 10:40:49.867: app| Registering file: /usr/lib/vmware/installer/vmware-installer --register-file vmware-player regular /lib/modules/2.6.27-rc9-tpc3/misc/vmmon.o
Oct 09 10:40:50.345: app| Failed to install the module /tmp/vmware-root/modules/vmmon.o to /lib/modules/2.6.27-rc9-tpc3/misc/vmmon.o.
Oct 09 10:41:36.593: app| Extracting the sources of the vmmon module.
Oct 09 10:41:36.613: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.27-rc9-tpc3/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.3.2
Oct 09 10:41:37.705: app| The vmmon module loads perfectly in the running kernel.
Oct 09 10:41:37.705: app| 
Oct 09 10:41:37.724: app| Registering file: /usr/lib/vmware/installer/vmware-installer --register-file vmware-player regular /lib/modules/2.6.27-rc9-tpc3/misc/vmmon.o
Oct 09 10:41:38.220: app| Failed to install the module /tmp/vmware-root/modules/vmmon.o to /lib/modules/2.6.27-rc9-tpc3/misc/vmmon.o.



Any Ideas?

---

### Post by MoonPhoenix on 2008-10-09
OK. I've fixed it.
On a whim I tried blanket --reinstall'ing everything I could figure it was using as there was no trace of this issue anywhere else.

Afterwards, it builds like it should!

Must have been a bit of curruption or self-flagulation going on there somewhere :lolflag:

---

### Post by rbmorse on 2008-10-09
It's an election year here.  Lots of that going around.

---

### Post by pwn2king on 2008-10-28
> **'[Neurotic] said:**
> I think this came out yesterday, but I ran around everywhere looking for it today, and figured I would share.

This was originally posted [here]("http://groups.google.com/group/vmkernelnewbies/browse_thread/thread/449f5d7d0dbc2e4a")
Steps to install.

[LIST=1]
[*]Install Vmware workstation normally, vmware-config.pl will fail.
[*]Download the [vmmon.tar]("http://forum.ubuntu.org.cn/download.php?id=42579&sid=d3e2a53288e88443a3a513ec85e99ba0"), [vmnet.tar]("http://forum.ubuntu.org.cn/download.php?id=42577&sid=d3e2a53288e88443a3a513ec85e99ba0") and [vmblock.tar]("http://forum.ubuntu.org.cn/download.php?id=42578&sid=d3e2a53288e88443a3a513ec85e99ba0") to /usr/lib/vmware/modules/source 
[*]run sudo ./vmware-config.pl
[/LIST]

Seems to be pretty much it so far.

Enjoy.


Thanks Neurotic, thought I'd have to plagiarize your name, downloading the virtual box was not happening neither, but the workstation 6 is great. Thanks again.

---

### Post by RagingAardvark on 2008-10-29
Does anyone have any non 404 links to these files?

txs

---


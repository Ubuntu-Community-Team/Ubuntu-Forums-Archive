---
title: "Ubuntu 12.10 - kernel 3.7.5 - nvidia-current drivers doesn't work"
date: 2013-01-31
forum: Installation &amp; Upgrades
---

### Post by cmoud94 on 2013-01-31
Hello everyone, I have a problem with nvidia-current drivers after upgrading to kernel 3.7.5.
This is the terminal output when I installed the nvidia drivers  that I downloaded from ubuntu-x-swat ppa.
> *******@*********:~$ cd Desktop
*******@*********:~/Desktop$ sudo dpkg -i nvidia-current*.deb
[sudo] password for *******: 
(Reading database ... 200903 files and directories currently installed.)
Preparing to replace nvidia-current 304.64-0ubuntu1~quantal~xup1 (using nvidia-current_304.64-0ubuntu1~quantal~xup1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-current ...
Setting up nvidia-current (304.64-0ubuntu1~quantal~xup1) ...
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match Acer with LENOVO
DEBUG:Quirk doesn't match
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match Acer with Dell Inc.
DEBUG:Quirk doesn't match
Loading new nvidia-current-304.64 DKMS files...
Building only for 3.7.5-030705-generic
Building for architecture x86_64
Building initial module for 3.7.5-030705-generic
ERROR (dkms apport): kernel package linux-headers-3.7.5-030705-generic is not supported
Error! Bad return status for module build on kernel: 3.7.5-030705-generic (x86_64)
Consult /var/lib/dkms/nvidia-current/304.64/build/make.log for more information.
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
*******@*********:~/Desktop$ And there is the make.log file content:
> DKMS make.log for nvidia-current-304.64 for kernel 3.7.5-030705-generic (x86_64)
Thu Jan 31 21:53:33 CET 2013
NVIDIA: calling KBUILD...
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
    echo >&2;                            \
    echo >&2 "  ERROR: Kernel configuration is invalid.";        \
    echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
    echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo >&2 ;                            \
    /bin/false)
mkdir -p /var/lib/dkms/nvidia-current/304.64/build/.tmp_versions ; rm -f /var/lib/dkms/nvidia-current/304.64/build/.tmp_versions/*
make -f scripts/Makefile.build obj=/var/lib/dkms/nvidia-current/304.64/build
  cc -Wp,-MD,/var/lib/dkms/nvidia-current/304.64/build/.nv.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.7/include -I/usr/src/linux-headers-3.7.5-030705-generic/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.7.5-030705-generic/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.7.5-030705-generic/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.7.5-030705-generic/include/linux/kconfig.h -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/var/lib/dkms/nvidia-current/304.64/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"304.64\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia-current/304.64/build/.tmp_nv.o /var/lib/dkms/nvidia-current/304.64/build/nv.c
In file included from /var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:15:0,
                 from /var/lib/dkms/nvidia-current/304.64/build/nv.c:13:
/var/lib/dkms/nvidia-current/304.64/build/conftest.h:8:2: error: #error remap_page_range() conftest failed!
/var/lib/dkms/nvidia-current/304.64/build/conftest.h:10:2: error: #error vmap() conftest failed!
/var/lib/dkms/nvidia-current/304.64/build/conftest.h:11:2: error: #error agp_backend_acquire() conftest failed!
/var/lib/dkms/nvidia-current/304.64/build/conftest.h:27:2: error: #error kmem_cache_create() conftest failed!
/var/lib/dkms/nvidia-current/304.64/build/conftest.h:28:2: error: #error on_each_cpu() conftest failed!
/var/lib/dkms/nvidia-current/304.64/build/conftest.h:29:2: error: #error smp_call_function() conftest failed!
/var/lib/dkms/nvidia-current/304.64/build/conftest.h:36:2: error: #error INIT_WORK() conftest failed!
/var/lib/dkms/nvidia-current/304.64/build/conftest.h:37:2: error: #error acpi_walk_namespace() conftest failed!
/var/lib/dkms/nvidia-current/304.64/build/conftest.h:38:2: error: #error acpi_os_wait_events_complete() conftest failed!
/var/lib/dkms/nvidia-current/304.64/build/conftest.h:42:2: error: #error pci_dma_mapping_error() conftest failed!
In file included from include/linux/kernel.h:10:0,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:40,
                 from /var/lib/dkms/nvidia-current/304.64/build/nv.c:13:
include/linux/bitops.h: In function ‘hweight_long’:
include/linux/bitops.h:66:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
In file included from /usr/src/linux-headers-3.7.5-030705-generic/arch/x86/include/asm/uaccess.h:594:0,
                 from include/linux/poll.h:11,
                 from /var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:99,
                 from /var/lib/dkms/nvidia-current/304.64/build/nv.c:13:
/usr/src/linux-headers-3.7.5-030705-generic/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
/usr/src/linux-headers-3.7.5-030705-generic/arch/x86/include/asm/uaccess_64.h:62:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
In file included from /var/lib/dkms/nvidia-current/304.64/build/nv.c:13:0:
/var/lib/dkms/nvidia-current/304.64/build/nv-linux.h: At top level:
/var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:135:2: error: #error "struct file_operations compile test likely failed!"
In file included from /var/lib/dkms/nvidia-current/304.64/build/nv.c:13:0:
/var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:294:2: error: #error "NV_PCI_DMA_MAPPING_ERROR() undefined!"
/var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:299:4: warning: "NV_ACPI_WALK_NAMESPACE_ARGUMENT_COUNT" is not defined [-Wundef]
/var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:301:8: warning: "NV_ACPI_WALK_NAMESPACE_ARGUMENT_COUNT" is not defined [-Wundef]
/var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:307:2: error: #error "NV_ACPI_WALK_NAMESPACE_ARGUMENT_COUNT value unrecognized!"
/var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:313:4: warning: "NV_ACPI_OS_WAIT_EVENTS_COMPLETE_ARGUMENT_COUNT" is not defined [-Wundef]
/var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:316:8: warning: "NV_ACPI_OS_WAIT_EVENTS_COMPLETE_ARGUMENT_COUNT" is not defined [-Wundef]
/var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:815:2: error: #error "NV_KMEM_CACHE_CREATE() undefined (kmem_cache_create() unavailable)!"
/var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:874:2: error: #error "NV_VMAP() undefined (vmap() unavailable)!"
/var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:946:2: error: #error "NV_SMP_CALL_FUNCTION() undefined (smp_call_function() unavailable)!"
/var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:966:2: error: #error "NV_ON_EACH_CPU() undefined (on_each_cpu() unavailable)!"
/var/lib/dkms/nvidia-current/304.64/build/nv-linux.h: In function ‘nv_execute_on_all_cpus’:
/var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:984:5: error: implicit declaration of function ‘NV_ON_EACH_CPU’ [-Werror=implicit-function-declaration]
/var/lib/dkms/nvidia-current/304.64/build/nv-linux.h: At top level:
/var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:1243:13: error: conflicting types for ‘pm_message_t’
In file included from /usr/src/linux-headers-3.7.5-030705-generic/arch/x86/include/asm/apic.h:5:0,
                 from /usr/src/linux-headers-3.7.5-030705-generic/arch/x86/include/asm/smp.h:13,
                 from include/linux/smp.h:38,
                 from include/linux/sched.h:30,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:40,
                 from /var/lib/dkms/nvidia-current/304.64/build/nv.c:13:
include/linux/pm.h:52:3: note: previous declaration of ‘pm_message_t’ was here
In file included from /var/lib/dkms/nvidia-current/304.64/build/nv.c:13:0:
/var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:1541:6: warning: "NV_INIT_WORK_ARGUMENT_COUNT" is not defined [-Wundef]
/var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:1551:8: warning: "NV_INIT_WORK_ARGUMENT_COUNT" is not defined [-Wundef]
/var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:1561:2: error: #error "NV_INIT_WORK_ARGUMENT_COUNT value unrecognized!"
In file included from /var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:1763:0,
                 from /var/lib/dkms/nvidia-current/304.64/build/nv.c:13:
/var/lib/dkms/nvidia-current/304.64/build/nv-proto.h:25:29: warning: "NV_INIT_WORK_ARGUMENT_COUNT" is not defined [-Wundef]
/var/lib/dkms/nvidia-current/304.64/build/nv.c:368:5: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/nvidia-current/304.64/build/nv.c:368:5: warning: (near initialization for ‘nv_pci_driver.suspend’) [enabled by default]
/var/lib/dkms/nvidia-current/304.64/build/nv.c: In function ‘nvidia_init_module’:
/var/lib/dkms/nvidia-current/304.64/build/nv.c:869:5: error: implicit declaration of function ‘NV_KMEM_CACHE_CREATE’ [-Werror=implicit-function-declaration]
/var/lib/dkms/nvidia-current/304.64/build/nv.c:869:58: error: expected expression before ‘nv_stack_t’
/var/lib/dkms/nvidia-current/304.64/build/nv.c:879:9: error: implicit declaration of function ‘NV_KMEM_CACHE_DESTROY’ [-Werror=implicit-function-declaration]
/var/lib/dkms/nvidia-current/304.64/build/nv.c:984:54: error: expected expression before ‘nv_pte_t’
/var/lib/dkms/nvidia-current/304.64/build/nv.c:993:13: error: expected expression before ‘nvidia_p2p_page_t’
/var/lib/dkms/nvidia-current/304.64/build/nv.c: In function ‘nv_kern_open’:
/var/lib/dkms/nvidia-current/304.64/build/nv.c:1535:30: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type [enabled by default]
In file included from /var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:112:0,
                 from /var/lib/dkms/nvidia-current/304.64/build/nv.c:13:
include/linux/interrupt.h:130:1: note: expected ‘irq_handler_t’ but argument is of type ‘enum irqreturn_t (*)(int,  void *, struct pt_regs *)’
/var/lib/dkms/nvidia-current/304.64/build/nv.c:1539:17: error: implicit declaration of function ‘NV_TASKQUEUE_INIT’ [-Werror=implicit-function-declaration]
/var/lib/dkms/nvidia-current/304.64/build/nv.c:1551:25: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type [enabled by default]
In file included from /var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:112:0,
                 from /var/lib/dkms/nvidia-current/304.64/build/nv.c:13:
include/linux/interrupt.h:130:1: note: expected ‘irq_handler_t’ but argument is of type ‘enum irqreturn_t (*)(int,  void *, struct pt_regs *)’
/var/lib/dkms/nvidia-current/304.64/build/nv.c: In function ‘nv_agp_init’:
/var/lib/dkms/nvidia-current/304.64/build/nv.c:2911:6: warning: "NV_AGP_BACKEND_ACQUIRE_ARGUMENT_COUNT" is not defined [-Wundef]
/var/lib/dkms/nvidia-current/304.64/build/nv.c:2928:9: error: too few arguments to function ‘agp_backend_acquire’
In file included from /var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:249:0,
                 from /var/lib/dkms/nvidia-current/304.64/build/nv.c:13:
include/linux/agp_backend.h:106:32: note: declared here
/var/lib/dkms/nvidia-current/304.64/build/nv.c:2930:13: error: too few arguments to function ‘agp_backend_release’
In file included from /var/lib/dkms/nvidia-current/304.64/build/nv-linux.h:249:0,
                 from /var/lib/dkms/nvidia-current/304.64/build/nv.c:13:
include/linux/agp_backend.h:107:13: note: declared here
cc1: some warnings being treated as errors
make[3]: *** [/var/lib/dkms/nvidia-current/304.64/build/nv.o] Error 1
make[2]: *** [_module_/var/lib/dkms/nvidia-current/304.64/build] Error 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] Error 1
make: *** [module] Error 2Can anyone help me please? Or should I go back to older kernel? Thanks.

PS: Sorry if my english isn't good enough. :)

---

### Post by monkeybrain2012 on 2013-01-31
Looks like you did it the wrong way. If you want to install something from a ppa, you should add the ppa to your sources list  (as instructed on their web page )and then install it with apt-get or the package manager (synaptic, software center, muon etc) this will pull in the dependencies and upgarde all the relevant packages.  If you just plug a .deb out of its archive and install it manually  it most likely will fail because dependencies may be missing or out of sync.

Open a terminal

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade


```I installed the kernel 3.7.5 and Nvidia 313.18 from xorg-edgers. No problem at all.

---

### Post by cmoud94 on 2013-01-31
Of course... I have their ppa in my sources list, and it doesn't work. That's the reason why I downloaded this package and tried to install it manualy (no effect).

But thanks for your help.

---

### Post by monkeybrain2012 on 2013-02-01
> **cmoud94 said:**
> Of course... I have their ppa in my sources list, and it doesn't work. That's the reason why I downloaded this package and tried to install it manualy (no effect).

But thanks for your help.

How doesn't it work? How did you install the kernel, from which kernel version did you upgrade from?  Did it work if you log into the previous kernel (kernel version number)?

---

### Post by cmoud94 on 2013-02-01
My previous kernel version is 3.6.3 and the drivers works good there. I downloaded the kernel from ([http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)) like many times before. But on kernel 3.7.x my nvidia-drivers gives these errors. I tried to add **xorg-edgers** ppa that you wrote about in previous post, installed nvidia driver from there and it's working perfectly now.

So thank you so much. ;):D

---

### Post by monkeybrain2012 on 2013-02-01
> **cmoud94 said:**
> My previous kernel version is 3.6.3 and the drivers works good there. I downloaded the kernel from ([http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)) like many times before. But on kernel 3.7.x my nvidia-drivers gives these errors. I tried to add **xorg-edgers** ppa that you wrote about in previous post, installed nvidia driver from there and it's working perfectly now.

So thank you so much. ;):D

Glad that it works out for you. Now it is working perfectly you should disable the xorg-edgers ppa until you want to upgrade your driver. There is certain risk that comes with bleeding edge, updating often with xorg-edgers may not be a good idea.

---

### Post by cmoud94 on 2013-02-01
Ok, I disabled it. Again, thank you for all your help. :)

---


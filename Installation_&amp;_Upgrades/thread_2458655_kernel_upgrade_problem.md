---
title: "kernel upgrade problem"
date: 2021-03-01
forum: Installation &amp; Upgrades
---

### Post by mwmast on 2021-03-01
I'm also having this problem while trying to install drivers for my AMD Radeon RX 580 GPU after a new install of my OS (20.04.1)

I joined this thread after following the instructions of the second link included below. When I run the kernel update script, as the link advises
```
**~$ sudo ubuntu-mainline-kernel.sh -i**
Finding latest version available on kernel.ubuntu.com
Latest version is: v5.11.2, continue? (y/N) 
Abort, the amd64 build has not succeeded
```

Following the last two instructions from Impadivus:
```
** ~$ dpkg --list 'linux-*' | grep -v '^rc\|^un'**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                  Version              Architecture Description
+++-=====================================-====================-============-==============================================================
ii  linux-base                            4.5ubuntu3.1         all          Linux image base package
ii  linux-firmware                        1.187.9              all          Firmware for Linux kernel drivers
ii  linux-generic-hwe-20.04               5.8.0.44.50~20.04.30 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.4.0-26                5.4.0-26.30          all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-26-generic        5.4.0-26.30          amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.8.0-44-generic        5.8.0-44.50~20.04.1  amd64        Linux kernel headers for version 5.8.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-20.04       5.8.0.44.50~20.04.30 amd64        Generic Linux kernel headers
ii  linux-hwe-5.8-headers-5.8.0-44        5.8.0-44.50~20.04.1  all          Header files related to Linux kernel version 5.8.0
ii  linux-image-5.4.0-26-generic          5.4.0-26.30          amd64        Signed kernel image generic
ii  linux-image-5.8.0-44-generic          5.8.0-44.50~20.04.1  amd64        Signed kernel image generic
ii  linux-image-generic-hwe-20.04         5.8.0.44.50~20.04.30 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                  5.4.0-66.74          amd64        Linux Kernel Headers for development
ii  linux-modules-5.4.0-26-generic        5.4.0-26.30          amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.8.0-44-generic        5.8.0-44.50~20.04.1  amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-26-generic  5.4.0-26.30          amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.8.0-44-generic  5.8.0-44.50~20.04.1  amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
ii  linux-sound-base                      1.0.25+dfsg-0ubuntu5 all          base package for ALSA and OSS sound systems

```
```
**~$ sudo apt-get install -f --simulate**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Conf amdgpu (20.45-1188099 localhost [amd64])
Conf amdgpu-pro-lib32 (20.45-1188099 localhost [amd64])
Conf amdgpu-dkms (1:5.6.20.906316-1188099 localhost [all])
Conf amdgpu-pro (20.45-1188099 localhost [amd64])
```

But now, when I attempt the command without --simulate, I get the following error: 

```
** ~$ sudo apt-get install -f**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfprint-2-tod1 libllvm9
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up amdgpu-dkms (1:5.6.20.906316-1188099) ...
Removing old amdgpu-5.6.20.906316-1188099 DKMS files...

------------------------------
Deleting module version: 5.6.20.906316-1188099
completely from the DKMS tree.
------------------------------
Done.
Loading new amdgpu-5.6.20.906316-1188099 DKMS files...
Building for 5.8.0-44-generic
Building for architecture x86_64
Building initial module for 5.8.0-44-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/amdgpu-dkms-firmware.0.crash'
Error! Bad return status for module build on kernel: 5.8.0-44-generic (x86_64)
Consult /var/lib/dkms/amdgpu/5.6.20.906316-1188099/build/make.log for more information.
dpkg: error processing package amdgpu-dkms (--configure):
 installed amdgpu-dkms package post-installation script subprocess returned error exit status 10
dpkg: dependency problems prevent configuration of amdgpu:
 amdgpu depends on amdgpu-dkms (= 1:5.6.20.906316-1188099); however:
  Package amdgpu-dkms is not configured yet.

dpkg: error processing package amdgpu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of amdgpu-pro:
 amdgpu-pro depends on amdgpu (= 20.45-1188099); however:
  Package amdgpu is not configured yet.

dpkg: error processing package amdgpu-pro (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of amdgpu-pro-lib32:
 amdgpu-pro-lib32 depends on amdgpu (= 20.45-1188099) | amdgpu-hwe (= 20.45-1188099); however:
  Package amdgpu is not configured yet.
  Package amdgpu-hwe is not installed.
 amdgpu-pro-lib32 depends on amdgpu-pro (= 20.45-1188099) | amdgpu-pro-hwe (= 20.45-1188099); however:
  Package amdgpu-pro is not configured yet.
  Package amdgpu-pro-hwe is not installed.

dpkg: error processing package amdgpNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                              No apport report written because the error message indicates its a followup error from a previous failure.
                                                         No apport report written because MaxReports is reached already
                                                                                                                       u-pro-lib32 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amdgpu-dkms
 amdgpu
 amdgpu-pro
 amdgpu-pro-lib32
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have found some coverage of the error here: [URL="https://community.amd.com/t5/drivers-software/can-t-install-amdgpu-drivers-on-ubuntu-20-04-1-5-4-0-56-generic/td-p/426676"]https://community.amd.com/t5/drivers-software/can-t-install-amdgpu-drivers-on-ubuntu-20-04-1-5-4-0-56-generic/td-p/426676
[/URL]Also, here: [https://askubuntu.com/questions/1275339/ubuntu-20-04-amd-gpu-with-intel-process-stuck-on-1024x76843-resolution](https://askubuntu.com/questions/1275339/ubuntu-20-04-amd-gpu-with-intel-process-stuck-on-1024x76843-resolution)

I'm unsure how to proceed, but feel this may aid the next few steps of troubleshooting dathi_dearg's problem as well as my own.

Thanks!

---

### Post by mwmast on 2021-03-02
I spent the rest of the day yesterday chasing this problem, and found a few more resources which suggest that [linux kernels >5.2 have trouble with building amd64]("http://forums.debian.net/viewtopic.php?f=6&t=146677") (x86-64), and that seems to be due to missing amdgpu firmware in the navi10, navi12, and arcturus families. [Link.]("https://itectec.com/ubuntu/ubuntu-missing-firmware-for-amdgpu/") [Bug Report.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1873325")
In the second link (the one titled Link), a link is provided to the linux-firmware git repo, where you can copy some, but not all, of the missing firmware (arcturus is important to the current high end of the AMD GPU product line, and at least one navi10 file is missing).

I've found [another resource]("https://community.amd.com/t5/drivers-software/can-t-install-amdgpu-drivers-on-ubuntu-20-04-1-5-4-0-56-generic/td-p/426676") where changing linux kernels solved the problem, at least in the context of installing AMD GPU drivers. Could someone with a little more experience check my idea before I act on it?

---

### Post by mwmast on 2021-03-02
for completeness, here is the result of "cat /var/lib/dkms/amdgpu/5.6.20.906316-1188099/build/make.log"

```
DKMS make.log for amdgpu-4.0-23 for kernel 5.8.0-44-generic (x86_64)
Tue 02 Mar 2021 10:39:56 AM CST
make: Entering directory '/usr/src/linux-headers-5.8.0-44-generic'
/var/lib/dkms/amdgpu/4.0-23/build/Makefile:20: "Local GCC version 90303 does not match kernel compiler GCC version 90300"
/var/lib/dkms/amdgpu/4.0-23/build/Makefile:21: "This may cause unexpected and hard-to-isolate compiler-related issues"
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/scheduler/sched_main.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/ttm/ttm_memory.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/main.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdgpu/amdgpu_drv.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/symbols.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_memory.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_ioctl.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/ttm/ttm_tt.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/scheduler/sched_fence.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdgpu/amdgpu_device.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_device_cgroup.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/scheduler/sched_entity.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_drm_cache.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/ttm/ttm_bo.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_drm.o
  LD [M]  /var/lib/dkms/amdgpu/4.0-23/build/scheduler/amd-sched.o
  AR      /var/lib/dkms/amdgpu/4.0-23/build/built-in.a
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_fence_array.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_fence.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_io.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/ttm/ttm_bo_util.o
/var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_fence.c:30:1: warning: ‘dma_fence_test_signaled_any’ defined but not used [-Wunused-function]
   30 | dma_fence_test_signaled_any(struct dma_fence **fences, uint32_t count,
      | ^~~~~~~~~~~~~~~~~~~~~~~~~~~
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_kthread.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_mm.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdgpu/amdgpu_kms.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_pci.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/ttm/ttm_bo_vm.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_perf_event.o
/var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_pci.c: In function ‘amdkcl_pci_init’:
/var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_pci.c:103:84: warning: passing argument 2 of ‘amdkcl_fp_setup’ discards ‘const’ qualifier from pointer target type [-Wdiscarded-qualifiers]
  103 |  _kcl_pcie_link_speed = (const unsigned char *) amdkcl_fp_setup("pcie_link_speed", _kcl_pcie_link_speed_stub);
      |                                                                                    ^~~~~~~~~~~~~~~~~~~~~~~~~
In file included from /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_pci.c:4:
/var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_common.h:12:63: note: expected ‘void *’ but argument is of type ‘const unsigned char *’
   12 | static inline void *amdkcl_fp_setup(const char *symbol, void *fp_stup)
      |                                                         ~~~~~~^~~~~~~
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_reservation.o
/var/lib/dkms/amdgpu/4.0-23/build/ttm/ttm_bo_vm.c: In function ‘ttm_bo_vm_fault_idle’:
/var/lib/dkms/amdgpu/4.0-23/build/ttm/ttm_bo_vm.c:76:24: error: ‘struct mm_struct’ has no member named ‘mmap_sem’; did you mean ‘mmap_base’?
   76 |   up_read(&vma->vm_mm->mmap_sem);
      |                        ^~~~~~~~
      |                        mmap_base
/var/lib/dkms/amdgpu/4.0-23/build/ttm/ttm_bo_vm.c: In function ‘amdttm_bo_vm_reserve’:
/var/lib/dkms/amdgpu/4.0-23/build/ttm/ttm_bo_vm.c:155:26: error: ‘struct mm_struct’ has no member named ‘mmap_sem’; did you mean ‘mmap_base’?
  155 |     up_read(&vma->vm_mm->mmap_sem);
      |                          ^~~~~~~~
      |                          mmap_base
/var/lib/dkms/amdgpu/4.0-23/build/amd/amdgpu/amdgpu_kms.c: In function ‘amdgpu_driver_load_kms’:
/var/lib/dkms/amdgpu/4.0-23/build/amd/amdgpu/amdgpu_kms.c:202:38: error: ‘DPM_FLAG_NEVER_SKIP’ undeclared (first use in this function)
  202 |    dev_pm_set_driver_flags(dev->dev, DPM_FLAG_NEVER_SKIP);
      |                                      ^~~~~~~~~~~~~~~~~~~
/var/lib/dkms/amdgpu/4.0-23/build/amd/amdgpu/amdgpu_kms.c:202:38: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [scripts/Makefile.build:286: /var/lib/dkms/amdgpu/4.0-23/build/ttm/ttm_bo_vm.o] Error 1
make[1]: *** [scripts/Makefile.build:515: /var/lib/dkms/amdgpu/4.0-23/build/ttm] Error 2
make[1]: *** Waiting for unfinished jobs....
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_suspend.o
make[2]: *** [scripts/Makefile.build:286: /var/lib/dkms/amdgpu/4.0-23/build/amd/amdgpu/amdgpu_kms.o] Error 1
make[1]: *** [scripts/Makefile.build:515: /var/lib/dkms/amdgpu/4.0-23/build/amd/amdgpu] Error 2
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_workqueue.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_seq_file.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_connector.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_backlight.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_drm_atomic_helper.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_drm_crtc.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_drm_fb.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_drm_modeset_lock.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_drm_modes.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_time.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/kcl_mn.o
  CC [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/dma-buf/dma-resv.o
  LD [M]  /var/lib/dkms/amdgpu/4.0-23/build/amd/amdkcl/amdkcl.o
make: *** [Makefile:1783: /var/lib/dkms/amdgpu/4.0-23/build] Error 2
make: Leaving directory '/usr/src/linux-headers-5.8.0-44-generic'
```

---


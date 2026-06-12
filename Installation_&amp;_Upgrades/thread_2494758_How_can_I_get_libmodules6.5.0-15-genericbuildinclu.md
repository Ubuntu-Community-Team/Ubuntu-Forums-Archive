---
title: "How can I get /lib/modules/6.5.0-15-generic/build/include/linux/version.h"
date: 2024-01-25
forum: Installation &amp; Upgrades
---

### Post by foxsquirrel on 2024-01-25
I am still trying to get the broken netbeans running after the 6.5 kernel update, from the log this might be the problem. This is the free player version, same issue with the Workstation Pro 17

Here is a the exact message from the log:

```
Failed to find /lib/modules/6.5.0-15-generic/build/include/linux/version.h
2024-01-26T00:26:18.194Z In(05) host-4705 /lib/modules/6.5.0-15-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2024-01-26T00:26:18.194Z In(05) host-4705 using /usr/bin/gcc-12 for preprocess check
```

also tried this:

```
sudo apt install linux-headers-$(uname -r)
```
Entire log:

Update: Just looked in the 5.19 kernel files and it is not present. Is it safe to assume that file does not exist and VMware has made a mistake?

```
2024-01-26T00:26:18.101Z In(05) host-4705 Log for VMware Workstation pid=4705 version=17.0.0 build=build-20800274 option=Release
2024-01-26T00:26:18.101Z In(05) host-4705 The host is x86_64.
2024-01-26T00:26:18.101Z In(05) host-4705 Host codepage=UTF-8 encoding=UTF-8
2024-01-26T00:26:18.101Z In(05) host-4705 Host is Linux 6.5.0-15-generic Ubuntu 22.04.3 LTS Ubuntu 22.04.3 LTS 22.04
2024-01-26T00:26:18.101Z In(05) host-4705 Host offset from UTC is -05:00.
2024-01-26T00:26:18.100Z In(05) host-4705 DictionaryLoad: Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2024-01-26T00:26:18.100Z In(05) host-4705 [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2024-01-26T00:26:18.100Z In(05) host-4705 PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2024-01-26T00:26:18.100Z In(05) host-4705 DictionaryLoad: Cannot open file "/home/fred/.vmware/config": No such file or directory.
2024-01-26T00:26:18.100Z In(05) host-4705 [msg.dictionary.load.openFailed] Cannot open file "/home/fred/.vmware/config": No such file or directory.
2024-01-26T00:26:18.100Z In(05) host-4705 PREF Optional preferences file not found at /home/fred/.vmware/config. Using default values.
2024-01-26T00:26:18.184Z Wa(03) host-4705 Logging to /tmp/vmware-fred/vmware-4705.log
2024-01-26T00:26:18.192Z In(05) host-4705 Obtaining info using the running kernel.
2024-01-26T00:26:18.192Z In(05) host-4705 Created new pathsHash.
2024-01-26T00:26:18.192Z In(05) host-4705 Setting header path for 6.5.0-15-generic to "/lib/modules/6.5.0-15-generic/build/include".
2024-01-26T00:26:18.192Z In(05) host-4705 Validating path "/lib/modules/6.5.0-15-generic/build/include" for kernel release "6.5.0-15-generic".
2024-01-26T00:26:18.194Z In(05) host-4705 Failed to find /lib/modules/6.5.0-15-generic/build/include/linux/version.h
2024-01-26T00:26:18.194Z In(05) host-4705 /lib/modules/6.5.0-15-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2024-01-26T00:26:18.194Z In(05) host-4705 using /usr/bin/gcc-12 for preprocess check
2024-01-26T00:26:18.245Z In(05) host-4705 Preprocessed UTS_RELEASE, got value "6.5.0-15-generic".
2024-01-26T00:26:18.245Z In(05) host-4705 The header path "/lib/modules/6.5.0-15-generic/build/include" for the kernel "6.5.0-15-generic" is valid.  Whoohoo!
2024-01-26T00:26:18.503Z In(05) host-4705 found symbol version file /lib/modules/6.5.0-15-generic/build/Module.symvers
2024-01-26T00:26:18.503Z In(05) host-4705 Reading symbol versions from /lib/modules/6.5.0-15-generic/build/Module.symvers.
2024-01-26T00:26:18.524Z In(05) host-4705 Read 28283 symbol versions
2024-01-26T00:26:18.524Z In(05) host-4705 Reading in info for the vmmon module.
2024-01-26T00:26:18.524Z In(05) host-4705 Reading in info for the vmnet module.
2024-01-26T00:26:18.524Z In(05) host-4705 Invoking modinfo on "vmmon".
2024-01-26T00:26:18.527Z In(05) host-4705 "/sbin/modinfo" exited with status 256.
2024-01-26T00:26:18.527Z In(05) host-4705 Invoking modinfo on "vmnet".
2024-01-26T00:26:18.530Z In(05) host-4705 "/sbin/modinfo" exited with status 256.
2024-01-26T00:26:18.545Z In(05) host-4705 to be installed: vmmon status: 0
2024-01-26T00:26:18.545Z In(05) host-4705 to be installed: vmnet status: 0
2024-01-26T00:26:18.560Z In(05) host-4705 Obtaining info using the running kernel.
2024-01-26T00:26:18.560Z In(05) host-4705 Setting header path for 6.5.0-15-generic to "/lib/modules/6.5.0-15-generic/build/include".
2024-01-26T00:26:18.560Z In(05) host-4705 Validating path "/lib/modules/6.5.0-15-generic/build/include" for kernel release "6.5.0-15-generic".
2024-01-26T00:26:18.560Z In(05) host-4705 Failed to find /lib/modules/6.5.0-15-generic/build/include/linux/version.h
2024-01-26T00:26:18.560Z In(05) host-4705 /lib/modules/6.5.0-15-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2024-01-26T00:26:18.560Z In(05) host-4705 using /usr/bin/gcc-12 for preprocess check
2024-01-26T00:26:18.567Z In(05) host-4705 Preprocessed UTS_RELEASE, got value "6.5.0-15-generic".
2024-01-26T00:26:18.567Z In(05) host-4705 The header path "/lib/modules/6.5.0-15-generic/build/include" for the kernel "6.5.0-15-generic" is valid.  Whoohoo!
2024-01-26T00:26:18.795Z In(05) host-4705 found symbol version file /lib/modules/6.5.0-15-generic/build/Module.symvers
2024-01-26T00:26:18.795Z In(05) host-4705 Reading symbol versions from /lib/modules/6.5.0-15-generic/build/Module.symvers.
2024-01-26T00:26:18.814Z In(05) host-4705 Read 28283 symbol versions
2024-01-26T00:26:18.814Z In(05) host-4705 Kernel header path retrieved from FileEntry: /lib/modules/6.5.0-15-generic/build/include
2024-01-26T00:26:18.814Z In(05) host-4705 Update kernel header path to /lib/modules/6.5.0-15-generic/build/include
2024-01-26T00:26:18.814Z In(05) host-4705 Validating path "/lib/modules/6.5.0-15-generic/build/include" for kernel release "6.5.0-15-generic".
2024-01-26T00:26:18.814Z In(05) host-4705 Failed to find /lib/modules/6.5.0-15-generic/build/include/linux/version.h
2024-01-26T00:26:18.814Z In(05) host-4705 /lib/modules/6.5.0-15-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2024-01-26T00:26:18.814Z In(05) host-4705 using /usr/bin/gcc-12 for preprocess check
2024-01-26T00:26:18.821Z In(05) host-4705 Preprocessed UTS_RELEASE, got value "6.5.0-15-generic".
2024-01-26T00:26:18.821Z In(05) host-4705 The header path "/lib/modules/6.5.0-15-generic/build/include" for the kernel "6.5.0-15-generic" is valid.  Whoohoo!
2024-01-26T00:26:18.822Z In(05) host-4705 Found compiler at "/usr/bin/gcc"
2024-01-26T00:26:18.824Z In(05) host-4705 Got gcc version "11".
2024-01-26T00:26:18.824Z In(05) host-4705 GCC major version 11 does not match Kernel GCC major version 12.
2024-01-26T00:26:18.824Z In(05) host-4705 Attempting to use a compiler at location "/usr/bin/gcc-12".
2024-01-26T00:26:18.825Z In(05) host-4705 Got gcc version "12".
2024-01-26T00:26:18.825Z In(05) host-4705 The GCC version matches the kernel GCC minor version like a glove.
2024-01-26T00:26:18.827Z In(05) host-4705 Got gcc version "12".
2024-01-26T00:26:18.827Z In(05) host-4705 The GCC version matches the kernel GCC minor version like a glove.
2024-01-26T00:26:18.828Z In(05) host-4705 Trying to find a suitable PBM set for kernel "6.5.0-15-generic".
2024-01-26T00:26:18.828Z In(05) host-4705 No matching PBM set was found for kernel "6.5.0-15-generic".
2024-01-26T00:26:18.828Z In(05) host-4705 The GCC version matches the kernel GCC minor version like a glove.
2024-01-26T00:26:18.828Z In(05) host-4705 Validating path "/lib/modules/6.5.0-15-generic/build/include" for kernel release "6.5.0-15-generic".
2024-01-26T00:26:18.828Z In(05) host-4705 Failed to find /lib/modules/6.5.0-15-generic/build/include/linux/version.h
2024-01-26T00:26:18.828Z In(05) host-4705 /lib/modules/6.5.0-15-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2024-01-26T00:26:18.828Z In(05) host-4705 using /usr/bin/gcc-12 for preprocess check
2024-01-26T00:26:18.834Z In(05) host-4705 Preprocessed UTS_RELEASE, got value "6.5.0-15-generic".
2024-01-26T00:26:18.834Z In(05) host-4705 The header path "/lib/modules/6.5.0-15-generic/build/include" for the kernel "6.5.0-15-generic" is valid.  Whoohoo!
2024-01-26T00:26:30.164Z In(05) host-4705 The GCC version matches the kernel GCC minor version like a glove.
2024-01-26T00:26:30.164Z In(05) host-4705 Validating path "/lib/modules/6.5.0-15-generic/build/include" for kernel release "6.5.0-15-generic".
2024-01-26T00:26:30.164Z In(05) host-4705 Failed to find /lib/modules/6.5.0-15-generic/build/include/linux/version.h
2024-01-26T00:26:30.164Z In(05) host-4705 /lib/modules/6.5.0-15-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2024-01-26T00:26:30.164Z In(05) host-4705 using /usr/bin/gcc-12 for preprocess check
2024-01-26T00:26:30.171Z In(05) host-4705 Preprocessed UTS_RELEASE, got value "6.5.0-15-generic".
2024-01-26T00:26:30.171Z In(05) host-4705 The header path "/lib/modules/6.5.0-15-generic/build/include" for the kernel "6.5.0-15-generic" is valid.  Whoohoo!
2024-01-26T00:26:30.171Z In(05) host-4705 Using temp dir "/tmp".
2024-01-26T00:26:41.066Z In(05) host-4705 Stopping VMware services:
2024-01-26T00:26:41.066Z In(05) host-4705    VMware Authentication Daemon[71G done
2024-01-26T00:26:41.066Z In(05) host-4705    Virtual machine monitor[71G done
2024-01-26T00:26:41.066Z In(05) host-4705 make: Entering directory '/tmp/modconfig-hJBodB/vmmon-only'
2024-01-26T00:26:41.066Z In(05) host-4705 /usr/bin/make -C /lib/modules/6.5.0-15-generic/build/include/.. M=$PWD SRCROOT=$PWD/. \
2024-01-26T00:26:41.066Z In(05) host-4705   MODULEBUILDDIR= modules
2024-01-26T00:26:41.066Z In(05) host-4705 make[1]: Entering directory '/usr/src/linux-headers-6.5.0-15-generic'
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmmon-only/linux/driver.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmmon-only/linux/driverLog.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmmon-only/linux/hostif.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmmon-only/common/apic.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmmon-only/common/comport.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmmon-only/common/cpuid.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmmon-only/common/crosspage.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmmon-only/common/memtrack.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmmon-only/common/moduleloop.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmmon-only/common/phystrack.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmmon-only/common/sharedAreaVmmon.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmmon-only/common/statVarsVmmon.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmmon-only/common/task.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmmon-only/common/vmx86.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmmon-only/bootstrap/bootstrap.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmmon-only/bootstrap/monLoader.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmmon-only/bootstrap/monLoaderVmmon.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmmon-only/bootstrap/vmmblob.o
2024-01-26T00:26:41.066Z In(05) host-4705   LD [M]  /tmp/modconfig-hJBodB/vmmon-only/vmmon.o
2024-01-26T00:26:41.066Z In(05) host-4705   MODPOST /tmp/modconfig-hJBodB/vmmon-only/Module.symvers
2024-01-26T00:26:41.066Z In(05) host-4705 make[1]: Leaving directory '/usr/src/linux-headers-6.5.0-15-generic'
2024-01-26T00:26:41.066Z In(05) host-4705 make: Leaving directory '/tmp/modconfig-hJBodB/vmmon-only'
2024-01-26T00:26:41.066Z In(05) host-4705 make: Entering directory '/tmp/modconfig-hJBodB/vmnet-only'
2024-01-26T00:26:41.066Z In(05) host-4705 /usr/bin/make -C /lib/modules/6.5.0-15-generic/build/include/.. M=$PWD SRCROOT=$PWD/. \
2024-01-26T00:26:41.066Z In(05) host-4705   MODULEBUILDDIR= modules
2024-01-26T00:26:41.066Z In(05) host-4705 make[1]: Entering directory '/usr/src/linux-headers-6.5.0-15-generic'
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmnet-only/driver.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmnet-only/hub.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmnet-only/userif.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmnet-only/netif.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmnet-only/bridge.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmnet-only/procfs.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmnet-only/smac_compat.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmnet-only/smac.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmnet-only/vnetEvent.o
2024-01-26T00:26:41.066Z In(05) host-4705   CC [M]  /tmp/modconfig-hJBodB/vmnet-only/vnetUserListener.o
2024-01-26T00:26:41.066Z In(05) host-4705 make[1]: Leaving directory '/usr/src/linux-headers-6.5.0-15-generic'
2024-01-26T00:26:41.066Z In(05) host-4705 make: Leaving directory '/tmp/modconfig-hJBodB/vmnet-only'
2024-01-26T00:26:41.066Z In(05) host-4705 [AppLoader] Use shipped Linux kernel AIO access library.
2024-01-26T00:26:41.066Z In(05) host-4705 An up-to-date "libaio" or "libaio1" package from your system is preferred.
2024-01-26T00:26:41.066Z In(05) host-4705 [AppLoader] GLib does not have GSettings support.
2024-01-26T00:26:41.066Z In(05) host-4705 Using kernel build system.
2024-01-26T00:26:41.066Z In(05) host-4705 warning: the compiler differs from the one used to build the kernel
2024-01-26T00:26:41.066Z In(05) host-4705   The kernel was built by: x86_64-linux-gnu-gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0
2024-01-26T00:26:41.066Z In(05) host-4705   You are using:           gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0
2024-01-26T00:26:41.066Z In(05) host-4705 /tmp/modconfig-hJBodB/vmmon-only/common/crosspage.o: warning: objtool: CrossPage_CodePage+0x207: 'naked' return found in RETHUNK build
2024-01-26T00:26:41.066Z In(05) host-4705 In file included from /tmp/modconfig-hJBodB/vmmon-only/./include/cpu_types.h:29,
2024-01-26T00:26:41.066Z In(05) host-4705                  from /tmp/modconfig-hJBodB/vmmon-only/./include/modulecall.h:33,
2024-01-26T00:26:41.066Z In(05) host-4705                  from /tmp/modconfig-hJBodB/vmmon-only/common/moduleloop.c:33:
2024-01-26T00:26:41.066Z In(05) host-4705 /tmp/modconfig-hJBodB/vmmon-only/./include/vm_basic_defs.h:779: warning: "DO_ONCE" redefined
2024-01-26T00:26:41.066Z In(05) host-4705   779 | #define DO_ONCE(code)                                                   \
2024-01-26T00:26:41.066Z In(05) host-4705       | 
2024-01-26T00:26:41.066Z In(05) host-4705 In file included from ./include/linux/prandom.h:12,
2024-01-26T00:26:41.066Z In(05) host-4705                  from ./include/linux/random.h:153,
2024-01-26T00:26:41.066Z In(05) host-4705                  from ./include/linux/nodemask.h:97,
2024-01-26T00:26:41.066Z In(05) host-4705                  from ./include/linux/sched.h:23,
2024-01-26T00:26:41.066Z In(05) host-4705                  from /tmp/modconfig-hJBodB/vmmon-only/common/moduleloop.c:31:
2024-01-26T00:26:41.066Z In(05) host-4705 ./include/linux/once.h:46: note: this is the location of the previous definition
2024-01-26T00:26:41.066Z In(05) host-4705    46 | #define DO_ONCE(func, ...)                                                   \
2024-01-26T00:26:41.066Z In(05) host-4705       | 
2024-01-26T00:26:41.066Z In(05) host-4705 /tmp/modconfig-hJBodB/vmmon-only/common/phystrack.o: warning: objtool: PhysTrack_Add() falls through to next function PhysTrack_Remove()
2024-01-26T00:26:41.066Z In(05) host-4705 /tmp/modconfig-hJBodB/vmmon-only/common/phystrack.o: warning: objtool: PhysTrack_Remove() falls through to next function PhysTrack_Test()
2024-01-26T00:26:41.066Z In(05) host-4705 /tmp/modconfig-hJBodB/vmmon-only/bootstrap/monLoader.c: In function &#8216;MonLoader_Process&#8217;:
2024-01-26T00:26:41.066Z In(05) host-4705 /tmp/modconfig-hJBodB/vmmon-only/bootstrap/monLoader.c:794:24: warning: the comparison will always evaluate as &#8216;false&#8217; for the address of &#8216;entries&#8217; will never be NULL [-Waddress]
2024-01-26T00:26:41.066Z In(05) host-4705   794 |    if (header->entries == 0 || header->count == 0) {
2024-01-26T00:26:41.066Z In(05) host-4705       |                        ^~
2024-01-26T00:26:41.066Z In(05) host-4705 In file included from /tmp/modconfig-hJBodB/vmmon-only/bootstrap/monLoader.c:57:
2024-01-26T00:26:41.066Z In(05) host-4705 /tmp/modconfig-hJBodB/vmmon-only/./include/monLoader.h:239:19: note: &#8216;entries&#8217; declared here
2024-01-26T00:26:41.066Z In(05) host-4705   239 |    MonLoaderEntry entries[];
2024-01-26T00:26:41.066Z In(05) host-4705       |                   ^~~~~~~
2024-01-26T00:26:41.066Z In(05) host-4705 In file included from /tmp/modconfig-hJBodB/vmmon-only/./include/cpu_types.h:29,
2024-01-26T00:26:41.066Z In(05) host-4705                  from /tmp/modconfig-hJBodB/vmmon-only/./include/modulecall.h:33,
2024-01-26T00:26:41.066Z In(05) host-4705                  from /tmp/modconfig-hJBodB/vmmon-only/linux/hostif.c:58:
2024-01-26T00:26:41.066Z In(05) host-4705 /tmp/modconfig-hJBodB/vmmon-only/./include/vm_basic_defs.h:779: warning: "DO_ONCE" redefined
2024-01-26T00:26:41.066Z In(05) host-4705   779 | #define DO_ONCE(code)                                                   \
2024-01-26T00:26:41.066Z In(05) host-4705       | 
2024-01-26T00:26:41.066Z In(05) host-4705 In file included from ./include/linux/prandom.h:12,
2024-01-26T00:26:41.066Z In(05) host-4705                  from ./include/linux/random.h:153,
2024-01-26T00:26:41.066Z In(05) host-4705                  from ./include/linux/nodemask.h:97,
2024-01-26T00:26:41.066Z In(05) host-4705                  from ./include/linux/sched.h:23,
2024-01-26T00:26:41.066Z In(05) host-4705                  from ./include/linux/binfmts.h:5,
2024-01-26T00:26:41.066Z In(05) host-4705                  from /tmp/modconfig-hJBodB/vmmon-only/linux/hostif.c:31:
2024-01-26T00:26:41.066Z In(05) host-4705 ./include/linux/once.h:46: note: this is the location of the previous definition
2024-01-26T00:26:41.066Z In(05) host-4705    46 | #define DO_ONCE(func, ...)                                                   \
2024-01-26T00:26:41.066Z In(05) host-4705       | 
2024-01-26T00:26:41.066Z In(05) host-4705 In file included from /tmp/modconfig-hJBodB/vmmon-only/./include/cpu_types.h:29,
2024-01-26T00:26:41.066Z In(05) host-4705                  from /tmp/modconfig-hJBodB/vmmon-only/./include/modulecall.h:33,
2024-01-26T00:26:41.066Z In(05) host-4705                  from /tmp/modconfig-hJBodB/vmmon-only/./common/vmx86.h:33,
2024-01-26T00:26:41.066Z In(05) host-4705                  from /tmp/modconfig-hJBodB/vmmon-only/linux/driver.h:32,
2024-01-26T00:26:41.066Z In(05) host-4705                  from /tmp/modconfig-hJBodB/vmmon-only/linux/driver.c:47:
2024-01-26T00:26:41.066Z In(05) host-4705 /tmp/modconfig-hJBodB/vmmon-only/./include/vm_basic_defs.h:779: warning: "DO_ONCE" redefined
2024-01-26T00:26:41.066Z In(05) host-4705   779 | #define DO_ONCE(code)                                                   \
2024-01-26T00:26:41.066Z In(05) host-4705       | 
2024-01-26T00:26:41.066Z In(05) host-4705 In file included from ./include/linux/prandom.h:12,
2024-01-26T00:26:41.066Z In(05) host-4705                  from ./include/linux/random.h:153,
2024-01-26T00:26:41.066Z In(05) host-4705                  from ./include/linux/nodemask.h:97,
2024-01-26T00:26:41.066Z In(05) host-4705                  from ./include/linux/list_lru.h:12,
2024-01-26T00:26:41.066Z In(05) host-4705                  from ./include/linux/fs.h:13,
2024-01-26T00:26:41.066Z In(05) host-4705                  from ./include/linux/highmem.h:5,
2024-01-26T00:26:41.066Z In(05) host-4705                  from /tmp/modconfig-hJBodB/vmmon-only/linux/driver.c:25:
2024-01-26T00:26:41.066Z In(05) host-4705 ./include/linux/once.h:46: note: this is the location of the previous definition
2024-01-26T00:26:41.066Z In(05) host-4705    46 | #define DO_ONCE(func, ...)                                                   \
2024-01-26T00:26:41.066Z In(05) host-4705       | 
2024-01-26T00:26:41.066Z In(05) host-4705 In file included from /tmp/modconfig-hJBodB/vmmon-only/./include/cpu_types.h:29,
2024-01-26T00:26:41.066Z In(05) host-4705                  from /tmp/modconfig-hJBodB/vmmon-only/./include/modulecall.h:33,
2024-01-26T00:26:41.066Z In(05) host-4705                  from /tmp/modconfig-hJBodB/vmmon-only/common/vmx86.h:33,
2024-01-26T00:26:41.066Z In(05) host-4705                  from /tmp/modconfig-hJBodB/vmmon-only/common/vmx86.c:38:
2024-01-26T00:26:41.066Z In(05) host-4705 /tmp/modconfig-hJBodB/vmmon-only/./include/vm_basic_defs.h:779: warning: "DO_ONCE" redefined
2024-01-26T00:26:41.066Z In(05) host-4705   779 | #define DO_ONCE(code)                                                   \
2024-01-26T00:26:41.066Z In(05) host-4705       | 
2024-01-26T00:26:41.066Z In(05) host-4705 In file included from ./include/linux/prandom.h:12,
2024-01-26T00:26:41.066Z In(05) host-4705                  from ./include/linux/random.h:153,
2024-01-26T00:26:41.066Z In(05) host-4705                  from ./include/linux/nodemask.h:97,
2024-01-26T00:26:41.066Z In(05) host-4705                  from ./include/linux/sched.h:23,
2024-01-26T00:26:41.066Z In(05) host-4705                  from /tmp/modconfig-hJBodB/vmmon-only/common/vmx86.c:31:
2024-01-26T00:26:41.066Z In(05) host-4705 ./include/linux/once.h:46: note: this is the location of the previous definition
2024-01-26T00:26:41.066Z In(05) host-4705    46 | #define DO_ONCE(func, ...)                                                   \
2024-01-26T00:26:41.066Z In(05) host-4705       | 
2024-01-26T00:26:41.066Z In(05) host-4705 /tmp/modconfig-hJBodB/vmmon-only/common/task.o: warning: objtool: .text: unexpected end of section
2024-01-26T00:26:41.066Z In(05) host-4705 ERROR: modpost: "__pte_offset_map" [/tmp/modconfig-hJBodB/vmmon-only/vmmon.ko] undefined!
2024-01-26T00:26:41.066Z In(05) host-4705 make[3]: *** [scripts/Makefile.modpost:144: /tmp/modconfig-hJBodB/vmmon-only/Module.symvers] Error 1
2024-01-26T00:26:41.066Z In(05) host-4705 make[2]: *** [/usr/src/linux-headers-6.5.0-15-generic/Makefile:1989: modpost] Error 2
2024-01-26T00:26:41.066Z In(05) host-4705 make[1]: *** [Makefile:234: __sub-make] Error 2
2024-01-26T00:26:41.066Z In(05) host-4705 make: *** [Makefile:117: vmmon.ko] Error 2
2024-01-26T00:26:41.066Z In(05) host-4705 Using kernel build system.
2024-01-26T00:26:41.066Z In(05) host-4705 warning: the compiler differs from the one used to build the kernel
2024-01-26T00:26:41.066Z In(05) host-4705   The kernel was built by: x86_64-linux-gnu-gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0
2024-01-26T00:26:41.066Z In(05) host-4705   You are using:           gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0
2024-01-26T00:26:41.066Z In(05) host-4705 /tmp/modconfig-hJBodB/vmnet-only/bridge.c: In function &#8216;VNetBridgeSendLargePacket&#8217;:
2024-01-26T00:26:41.066Z In(05) host-4705 /tmp/modconfig-hJBodB/vmnet-only/bridge.c:1413:11: error: implicit declaration of function &#8216;skb_gso_segment&#8217;; did you mean &#8216;tcp_gso_segment&#8217;? [-Werror=implicit-function-declaration]
2024-01-26T00:26:41.066Z In(05) host-4705  1413 |    segs = skb_gso_segment(skb, 0);
2024-01-26T00:26:41.066Z In(05) host-4705       |           ^~~~~~~~~~~~~~~
2024-01-26T00:26:41.066Z In(05) host-4705       |           tcp_gso_segment
2024-01-26T00:26:41.066Z In(05) host-4705 /tmp/modconfig-hJBodB/vmnet-only/bridge.c:1413:9: warning: assignment to &#8216;struct sk_buff *&#8217; from &#8216;int&#8217; makes pointer from integer without a cast [-Wint-conversion]
2024-01-26T00:26:41.066Z In(05) host-4705  1413 |    segs = skb_gso_segment(skb, 0);
2024-01-26T00:26:41.066Z In(05) host-4705       |         ^
2024-01-26T00:26:41.066Z In(05) host-4705 /tmp/modconfig-hJBodB/vmnet-only/userif.o: warning: objtool: VNetCsumAndCopyToUser+0x2d: call to csum_partial_copy_nocheck() with UACCESS enabled
2024-01-26T00:26:41.066Z In(05) host-4705 cc1: some warnings being treated as errors
2024-01-26T00:26:41.066Z In(05) host-4705 make[3]: *** [scripts/Makefile.build:251: /tmp/modconfig-hJBodB/vmnet-only/bridge.o] Error 1
2024-01-26T00:26:41.066Z In(05) host-4705 make[3]: *** Waiting for unfinished jobs....
2024-01-26T00:26:41.066Z In(05) host-4705 make[2]: *** [/usr/src/linux-headers-6.5.0-15-generic/Makefile:2037: /tmp/modconfig-hJBodB/vmnet-only] Error 2
2024-01-26T00:26:41.066Z In(05) host-4705 make[1]: *** [Makefile:234: __sub-make] Error 2
2024-01-26T00:26:41.066Z In(05) host-4705 make: *** [Makefile:117: vmnet.ko] Error 2
2024-01-26T00:26:41.066Z In(05) host-4705 Unable to install all modules.  See log for details.
2024-01-26T00:26:41.066Z In(05) host-4705 

```

---

### Post by TheFu on 2024-01-26
VMware questions are best asked from VMware.  They are a very proprietary company, so nobody here can look at their code and provide advice.

---

### Post by MAFoElffen on 2024-01-26
If I look in the Kernel source package for 6.5.0 ([https://bugs.launchpad.net/ubuntu/+archive/primary/+sourcefiles/linux/6.5.0-15.15/linux_6.5.0.orig.tar.gz](https://bugs.launchpad.net/ubuntu/+archive/primary/+sourcefiles/linux/6.5.0-15.15/linux_6.5.0.orig.tar.gz)), which that is built from (assuming that is the right place to look), I see 7 instances of version.h files... But none of those are in that path, and they are all different. It all looks kosher to me with that.

I agree with TheFu. I think this is something to ask VMware, and might be a bug on their part.

---

### Post by ubfan1 on 2024-01-26
You "version.h" location info is not an error, just telling you where it looked (first) and where is looked second (and found it).
Google the actual error:ERROR: modpost: "__pte_offset_map" [/tmp/modconfig-hJBodB/vmmon-only/vmmon.ko] undefined
and you see the problem with vmmod and vmnet, with some solutions. like [https://communities.vmware.com/t5/Workstation-2023-Tech-Preview/Linux-Kernel-6-5-rc-vmmon-compile-fails/td-p/2981003](https://communities.vmware.com/t5/Workstation-2023-Tech-Preview/Linux-Kernel-6-5-rc-vmmon-compile-fails/td-p/2981003)    or [https://communities.vmware.com/t5/VMware-Workstation-Pro/Workstation-16-2-1-vmmon-amp-vmnet-not-compiling-on-Pop-OS-21-10/td-p/2884631](https://communities.vmware.com/t5/VMware-Workstation-Pro/Workstation-16-2-1-vmmon-amp-vmnet-not-compiling-on-Pop-OS-21-10/td-p/2884631)

---


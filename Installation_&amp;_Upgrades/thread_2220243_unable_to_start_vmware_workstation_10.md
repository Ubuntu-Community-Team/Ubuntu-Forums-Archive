---
title: "unable to start vmware workstation 10"
date: 2014-04-27
forum: Installation &amp; Upgrades
---

### Post by Tulsi_Rao on 2014-04-27
hi guys..

Recently i'd downloaded and installed ubuntu 14.04 LTS.I'd installed vmware workstation in it.when i'm trying to run vmware workstation i'm getting a popup like 

**"Before you can run vmware several modules must be compiled and loaded into the running kern**al"

then i clicked install the it pormpted for password after that i'm getting a popup alert 

**"unable to start services see logfile /tmp/vmware/vmware-modconfig-5964.log for details" **

here is the log files:

> 2014-04-27T17:53:50.171+05:30| vthread-3| I120: Log for VMware Workstation pid=5964 version=10.0.1 build=build-1379776 option=Release
2014-04-27T17:53:50.171+05:30| vthread-3| I120: The process is 64-bit.
2014-04-27T17:53:50.171+05:30| vthread-3| I120: Host codepage=UTF-8 encoding=UTF-8
2014-04-27T17:53:50.171+05:30| vthread-3| I120: Host is Linux 3.13.0-24-generic Ubuntu 14.04 LTS
2014-04-27T17:53:50.171+05:30| vthread-3| I120: Msg_Reset:
2014-04-27T17:53:50.171+05:30| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2014-04-27T17:53:50.171+05:30| vthread-3| I120: ----------------------------------------
2014-04-27T17:53:50.171+05:30| vthread-3| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2014-04-27T17:53:50.171+05:30| vthread-3| I120: Msg_Reset:
2014-04-27T17:53:50.171+05:30| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/config": No such file or directory.
2014-04-27T17:53:50.171+05:30| vthread-3| I120: ----------------------------------------
2014-04-27T17:53:50.171+05:30| vthread-3| I120: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2014-04-27T17:53:50.171+05:30| vthread-3| I120: PREF Unable to check permissions for preferences file.
2014-04-27T17:53:50.171+05:30| vthread-3| I120: Msg_Reset:
2014-04-27T17:53:50.171+05:30| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/preferences": No such file or directory.
2014-04-27T17:53:50.171+05:30| vthread-3| I120: ----------------------------------------
2014-04-27T17:53:50.171+05:30| vthread-3| I120: PREF Failed to load user preferences.
2014-04-27T17:53:50.171+05:30| vthread-3| W110: Logging to /tmp/vmware-root/vmware-modconfig-5964.log
2014-04-27T17:53:50.178+05:30| vthread-3| I120: Obtaining info using the running kernel.
2014-04-27T17:53:50.178+05:30| vthread-3| I120: Created new pathsHash.
2014-04-27T17:53:50.178+05:30| vthread-3| I120: Setting header path for 3.13.0-24-generic to "/lib/modules/3.13.0-24-generic/build/include".
2014-04-27T17:53:50.178+05:30| vthread-3| I120: Validating path "/lib/modules/3.13.0-24-generic/build/include" for kernel release "3.13.0-24-generic".
2014-04-27T17:53:50.178+05:30| vthread-3| I120: Failed to find /lib/modules/3.13.0-24-generic/build/include/linux/version.h
2014-04-27T17:53:50.178+05:30| vthread-3| I120: /lib/modules/3.13.0-24-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-04-27T17:53:50.178+05:30| vthread-3| I120: using /usr/bin/gcc-4.8 for preprocess check
2014-04-27T17:53:50.184+05:30| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-24-generic".
2014-04-27T17:53:50.184+05:30| vthread-3| I120: The header path "/lib/modules/3.13.0-24-generic/build/include" for the kernel "3.13.0-24-generic" is valid.  Whoohoo!
2014-04-27T17:53:50.310+05:30| vthread-3| I120: Reading in info for the vmmon module.
2014-04-27T17:53:50.310+05:30| vthread-3| I120: Reading in info for the vmnet module.
2014-04-27T17:53:50.310+05:30| vthread-3| I120: Reading in info for the vmblock module.
2014-04-27T17:53:50.310+05:30| vthread-3| I120: Reading in info for the vmci module.
2014-04-27T17:53:50.310+05:30| vthread-3| I120: Reading in info for the vsock module.
2014-04-27T17:53:50.310+05:30| vthread-3| I120: Setting vsock to depend on vmci.
2014-04-27T17:53:50.310+05:30| vthread-3| I120: Invoking modinfo on "vmmon".
2014-04-27T17:53:50.314+05:30| vthread-3| I120: "/sbin/modinfo" exited with status 0.
2014-04-27T17:53:50.314+05:30| vthread-3| I120: Invoking modinfo on "vmnet".
2014-04-27T17:53:50.317+05:30| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-04-27T17:53:50.317+05:30| vthread-3| I120: Invoking modinfo on "vmblock".
2014-04-27T17:53:50.320+05:30| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-04-27T17:53:50.320+05:30| vthread-3| I120: Invoking modinfo on "vmci".
2014-04-27T17:53:50.322+05:30| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-04-27T17:53:50.322+05:30| vthread-3| I120: Invoking modinfo on "vsock".
2014-04-27T17:53:50.324+05:30| vthread-3| I120: "/sbin/modinfo" exited with status 0.
2014-04-27T17:53:50.344+05:30| vthread-3| I120: to be installed: vmnet status: 0
2014-04-27T17:53:50.357+05:30| vthread-3| I120: Obtaining info using the running kernel.
2014-04-27T17:53:50.357+05:30| vthread-3| I120: Setting header path for 3.13.0-24-generic to "/lib/modules/3.13.0-24-generic/build/include".
2014-04-27T17:53:50.357+05:30| vthread-3| I120: Validating path "/lib/modules/3.13.0-24-generic/build/include" for kernel release "3.13.0-24-generic".
2014-04-27T17:53:50.357+05:30| vthread-3| I120: Failed to find /lib/modules/3.13.0-24-generic/build/include/linux/version.h
2014-04-27T17:53:50.357+05:30| vthread-3| I120: /lib/modules/3.13.0-24-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-04-27T17:53:50.357+05:30| vthread-3| I120: using /usr/bin/gcc-4.8 for preprocess check
2014-04-27T17:53:50.371+05:30| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-24-generic".
2014-04-27T17:53:50.372+05:30| vthread-3| I120: The header path "/lib/modules/3.13.0-24-generic/build/include" for the kernel "3.13.0-24-generic" is valid.  Whoohoo!
2014-04-27T17:53:50.494+05:30| vthread-3| I120: Kernel header path retrieved from FileEntry: /lib/modules/3.13.0-24-generic/build/include
2014-04-27T17:53:50.494+05:30| vthread-3| I120: Update kernel header path to /lib/modules/3.13.0-24-generic/build/include
2014-04-27T17:53:50.494+05:30| vthread-3| I120: Validating path "/lib/modules/3.13.0-24-generic/build/include" for kernel release "3.13.0-24-generic".
2014-04-27T17:53:50.494+05:30| vthread-3| I120: Failed to find /lib/modules/3.13.0-24-generic/build/include/linux/version.h
2014-04-27T17:53:50.494+05:30| vthread-3| I120: /lib/modules/3.13.0-24-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-04-27T17:53:50.494+05:30| vthread-3| I120: using /usr/bin/gcc-4.8 for preprocess check
2014-04-27T17:53:50.507+05:30| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-24-generic".
2014-04-27T17:53:50.507+05:30| vthread-3| I120: The header path "/lib/modules/3.13.0-24-generic/build/include" for the kernel "3.13.0-24-generic" is valid.  Whoohoo!
2014-04-27T17:53:50.507+05:30| vthread-3| I120: Found compiler at "/usr/bin/gcc"
2014-04-27T17:53:50.510+05:30| vthread-3| I120: Got gcc version "4.8".
2014-04-27T17:53:50.510+05:30| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-04-27T17:53:50.511+05:30| vthread-3| I120: Using user supplied compiler "/usr/bin/gcc".
2014-04-27T17:53:50.514+05:30| vthread-3| I120: Got gcc version "4.8".
2014-04-27T17:53:50.514+05:30| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-04-27T17:53:50.523+05:30| vthread-3| I120: Trying to find a suitable PBM set for kernel "3.13.0-24-generic".
2014-04-27T17:53:50.523+05:30| vthread-3| I120: No matching PBM set was found for kernel "3.13.0-24-generic".
2014-04-27T17:53:50.523+05:30| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-04-27T17:53:50.523+05:30| vthread-3| I120: Validating path "/lib/modules/3.13.0-24-generic/build/include" for kernel release "3.13.0-24-generic".
2014-04-27T17:53:50.523+05:30| vthread-3| I120: Failed to find /lib/modules/3.13.0-24-generic/build/include/linux/version.h
2014-04-27T17:53:50.523+05:30| vthread-3| I120: /lib/modules/3.13.0-24-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-04-27T17:53:50.523+05:30| vthread-3| I120: using /usr/bin/gcc-4.8 for preprocess check
2014-04-27T17:53:50.534+05:30| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-24-generic".
2014-04-27T17:53:50.534+05:30| vthread-3| I120: The header path "/lib/modules/3.13.0-24-generic/build/include" for the kernel "3.13.0-24-generic" is valid.  Whoohoo!
2014-04-27T17:53:50.537+05:30| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-04-27T17:53:50.537+05:30| vthread-3| I120: Validating path "/lib/modules/3.13.0-24-generic/build/include" for kernel release "3.13.0-24-generic".
2014-04-27T17:53:50.537+05:30| vthread-3| I120: Failed to find /lib/modules/3.13.0-24-generic/build/include/linux/version.h
2014-04-27T17:53:50.537+05:30| vthread-3| I120: /lib/modules/3.13.0-24-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-04-27T17:53:50.537+05:30| vthread-3| I120: using /usr/bin/gcc-4.8 for preprocess check
2014-04-27T17:53:50.548+05:30| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-24-generic".
2014-04-27T17:53:50.548+05:30| vthread-3| I120: The header path "/lib/modules/3.13.0-24-generic/build/include" for the kernel "3.13.0-24-generic" is valid.  Whoohoo!
2014-04-27T17:53:50.548+05:30| vthread-3| I120: Using temp dir "/tmp".
2014-04-27T17:53:50.551+05:30| vthread-3| I120: Obtaining info using the running kernel.
2014-04-27T17:53:50.551+05:30| vthread-3| I120: Setting header path for 3.13.0-24-generic to "/lib/modules/3.13.0-24-generic/build/include".
2014-04-27T17:53:50.551+05:30| vthread-3| I120: Validating path "/lib/modules/3.13.0-24-generic/build/include" for kernel release "3.13.0-24-generic".
2014-04-27T17:53:50.551+05:30| vthread-3| I120: Failed to find /lib/modules/3.13.0-24-generic/build/include/linux/version.h
2014-04-27T17:53:50.551+05:30| vthread-3| I120: /lib/modules/3.13.0-24-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-04-27T17:53:50.551+05:30| vthread-3| I120: using /usr/bin/gcc-4.8 for preprocess check
2014-04-27T17:53:50.557+05:30| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-24-generic".
2014-04-27T17:53:50.557+05:30| vthread-3| I120: The header path "/lib/modules/3.13.0-24-generic/build/include" for the kernel "3.13.0-24-generic" is valid.  Whoohoo!
2014-04-27T17:53:50.680+05:30| vthread-3| I120: Invoking modinfo on "vmnet".
2014-04-27T17:53:50.683+05:30| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-04-27T17:53:51.059+05:30| vthread-3| I120: Setting destination path for vmnet to "/lib/modules/3.13.0-24-generic/misc/vmnet.ko".
2014-04-27T17:53:51.059+05:30| vthread-3| I120: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2014-04-27T17:53:51.072+05:30| vthread-3| I120: Successfully extracted the vmnet source.
2014-04-27T17:53:51.072+05:30| vthread-3| I120: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-tUsQZE/vmnet-only auto-build HEADER_DIR=/lib/modules/3.13.0-24-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2014-04-27T17:53:53.182+05:30| vthread-3| W110: Failed to build vmnet.  Failed to execute the build command.
2014-04-27T17:54:16.220+05:30| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-04-27T17:54:16.220+05:30| vthread-3| I120: Validating path "/lib/modules/3.13.0-24-generic/build/include" for kernel release "3.13.0-24-generic".
2014-04-27T17:54:16.220+05:30| vthread-3| I120: Failed to find /lib/modules/3.13.0-24-generic/build/include/linux/version.h
2014-04-27T17:54:16.220+05:30| vthread-3| I120: /lib/modules/3.13.0-24-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-04-27T17:54:16.220+05:30| vthread-3| I120: using /usr/bin/gcc-4.8 for preprocess check
2014-04-27T17:54:16.227+05:30| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-24-generic".
2014-04-27T17:54:16.227+05:30| vthread-3| I120: The header path "/lib/modules/3.13.0-24-generic/build/include" for the kernel "3.13.0-24-generic" is valid.  Whoohoo!
2014-04-27T17:54:16.228+05:30| vthread-3| I120: Using temp dir "/tmp".
2014-04-27T17:54:16.229+05:30| vthread-3| I120: Obtaining info using the running kernel.
2014-04-27T17:54:16.229+05:30| vthread-3| I120: Setting header path for 3.13.0-24-generic to "/lib/modules/3.13.0-24-generic/build/include".
2014-04-27T17:54:16.229+05:30| vthread-3| I120: Validating path "/lib/modules/3.13.0-24-generic/build/include" for kernel release "3.13.0-24-generic".
2014-04-27T17:54:16.229+05:30| vthread-3| I120: Failed to find /lib/modules/3.13.0-24-generic/build/include/linux/version.h
2014-04-27T17:54:16.229+05:30| vthread-3| I120: /lib/modules/3.13.0-24-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-04-27T17:54:16.230+05:30| vthread-3| I120: using /usr/bin/gcc-4.8 for preprocess check
2014-04-27T17:54:16.243+05:30| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-24-generic".
2014-04-27T17:54:16.243+05:30| vthread-3| I120: The header path "/lib/modules/3.13.0-24-generic/build/include" for the kernel "3.13.0-24-generic" is valid.  Whoohoo!
2014-04-27T17:54:16.363+05:30| vthread-3| I120: Invoking modinfo on "vmnet".
2014-04-27T17:54:16.367+05:30| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-04-27T17:54:16.721+05:30| vthread-3| I120: Setting destination path for vmnet to "/lib/modules/3.13.0-24-generic/misc/vmnet.ko".
2014-04-27T17:54:16.721+05:30| vthread-3| I120: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2014-04-27T17:54:16.726+05:30| vthread-3| I120: Successfully extracted the vmnet source.
2014-04-27T17:54:16.726+05:30| vthread-3| I120: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-43FYYF/vmnet-only auto-build HEADER_DIR=/lib/modules/3.13.0-24-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2014-04-27T17:54:18.821+05:30| vthread-3| W110: Failed to build vmnet.  Failed to execute the build command.
2014-04-27T17:58:00.790+05:30| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-04-27T17:58:00.790+05:30| vthread-3| I120: Validating path "/lib/modules/3.13.0-24-generic/build/include" for kernel release "3.13.0-24-generic".
2014-04-27T17:58:00.790+05:30| vthread-3| I120: Failed to find /lib/modules/3.13.0-24-generic/build/include/linux/version.h
2014-04-27T17:58:00.790+05:30| vthread-3| I120: /lib/modules/3.13.0-24-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-04-27T17:58:00.790+05:30| vthread-3| I120: using /usr/bin/gcc-4.8 for preprocess check
2014-04-27T17:58:00.806+05:30| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-24-generic".
2014-04-27T17:58:00.806+05:30| vthread-3| I120: The header path "/lib/modules/3.13.0-24-generic/build/include" for the kernel "3.13.0-24-generic" is valid.  Whoohoo!
2014-04-27T17:58:00.806+05:30| vthread-3| I120: Using temp dir "/tmp".
2014-04-27T17:58:00.808+05:30| vthread-3| I120: Obtaining info using the running kernel.
2014-04-27T17:58:00.808+05:30| vthread-3| I120: Setting header path for 3.13.0-24-generic to "/lib/modules/3.13.0-24-generic/build/include".
2014-04-27T17:58:00.808+05:30| vthread-3| I120: Validating path "/lib/modules/3.13.0-24-generic/build/include" for kernel release "3.13.0-24-generic".
2014-04-27T17:58:00.808+05:30| vthread-3| I120: Failed to find /lib/modules/3.13.0-24-generic/build/include/linux/version.h
2014-04-27T17:58:00.808+05:30| vthread-3| I120: /lib/modules/3.13.0-24-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-04-27T17:58:00.808+05:30| vthread-3| I120: using /usr/bin/gcc-4.8 for preprocess check
2014-04-27T17:58:00.819+05:30| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-24-generic".
2014-04-27T17:58:00.819+05:30| vthread-3| I120: The header path "/lib/modules/3.13.0-24-generic/build/include" for the kernel "3.13.0-24-generic" is valid.  Whoohoo!
2014-04-27T17:58:00.943+05:30| vthread-3| I120: Invoking modinfo on "vmnet".
2014-04-27T17:58:00.947+05:30| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-04-27T17:58:01.287+05:30| vthread-3| I120: Setting destination path for vmnet to "/lib/modules/3.13.0-24-generic/misc/vmnet.ko".
2014-04-27T17:58:01.287+05:30| vthread-3| I120: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2014-04-27T17:58:01.294+05:30| vthread-3| I120: Successfully extracted the vmnet source.
2014-04-27T17:58:01.294+05:30| vthread-3| I120: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-R7qjqy/vmnet-only auto-build HEADER_DIR=/lib/modules/3.13.0-24-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2014-04-27T17:58:03.331+05:30| vthread-3| W110: Failed to build vmnet.  Failed to execute the build command.

then i searched on google for this i found the patch: in below link

[https://communities.vmware.com/message/1902218#1902218](https://communities.vmware.com/message/1902218#1902218)

when i run the patch i'm getting error message like this:

> ./vmware3.2.0.patch
diff: source802//vmnet-only/filter.c: No such file or directory
diff: source/vmnet-only/filter.c: No such file or directory
./vmware3.2.0.patch: line 2: ---: command not found
./vmware3.2.0.patch: line 3: +++: command not found
./vmware3.2.0.patch: line 4: @@: command not found
./vmware3.2.0.patch: line 8: syntax error near unexpected token `('
./vmware3.2.0.patch: line 8: `+#if LINUX_VERSION_CODE >= KERNEL_VERSION(4, 3, 2, 0)'



plz help me to find a solution.i'd looked for the code though may be i could make some changes it it,but when i opend the code i didnt found anything to be edited.i;m not so good with prog. 

tnx

---

### Post by sef2 on 2014-05-16
> **Tulsi_Rao said:**
> plz help me to find a solution.i'd looked for the code though may be i could make some changes it it,but when i opend the code i didnt found anything to be edited.i;m not so good with prog...
tnx


Hope this helps ..[http://blog.endurancetrails.com/2014/03/vmware-1001-patch-for-linux-313.html](http://blog.endurancetrails.com/2014/03/vmware-1001-patch-for-linux-313.html)

---


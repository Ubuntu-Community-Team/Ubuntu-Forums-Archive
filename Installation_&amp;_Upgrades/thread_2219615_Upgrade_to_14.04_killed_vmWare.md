---
title: "Upgrade to 14.04 killed vmWare"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by tdubois65 on 2014-04-24
After upgrading to Ubuntu 14.04 I tried starting my VMware Workstation instance and received the following notice: "Before you can run vmWare, several modules must be compiled and loaded into the running kernel [Cancel] [Install]" I pressed install and received an error "Unable to start services" with a log file location. Log contents are as follows:
cat vmware-modconfig-14296.log 
2014-04-24T18:13:00.242-05:00| vthread-3| I120: Log for VMware Workstation pid=14296 version=9.0.3 build=build-1410761 option=Release
2014-04-24T18:13:00.242-05:00| vthread-3| I120: The process is 32-bit.
2014-04-24T18:13:00.242-05:00| vthread-3| I120: Host codepage=UTF-8 encoding=UTF-8
2014-04-24T18:13:00.242-05:00| vthread-3| I120: Host is Linux 3.13.0-24-generic Ubuntu 14.04 LTS
2014-04-24T18:13:00.241-05:00| vthread-3| I120: Msg_Reset:
2014-04-24T18:13:00.241-05:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2014-04-24T18:13:00.241-05:00| vthread-3| I120: ----------------------------------------
2014-04-24T18:13:00.241-05:00| vthread-3| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2014-04-24T18:13:00.241-05:00| vthread-3| I120: Msg_Reset:
2014-04-24T18:13:00.241-05:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/config": No such file or directory.
2014-04-24T18:13:00.241-05:00| vthread-3| I120: ----------------------------------------
2014-04-24T18:13:00.241-05:00| vthread-3| I120: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2014-04-24T18:13:00.241-05:00| vthread-3| I120: Msg_Reset:
2014-04-24T18:13:00.241-05:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/preferences": No such file or directory.
2014-04-24T18:13:00.241-05:00| vthread-3| I120: ----------------------------------------
2014-04-24T18:13:00.241-05:00| vthread-3| I120: PREF Failed to load user preferences.
2014-04-24T18:13:00.242-05:00| vthread-3| W110: Logging to /tmp/vmware-root/vmware-modconfig-14296.log
2014-04-24T18:13:00.250-05:00| vthread-3| I120: Obtaining info using the running kernel.
2014-04-24T18:13:00.250-05:00| vthread-3| I120: Setting header path for 3.13.0-24-generic to "/lib/modules/3.13.0-24-generic/build/include".
2014-04-24T18:13:00.250-05:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-24-generic/build/include" for kernel release "3.13.0-24-generic".
2014-04-24T18:13:00.250-05:00| vthread-3| I120: Failed to find /lib/modules/3.13.0-24-generic/build/include/linux/version.h
2014-04-24T18:13:00.250-05:00| vthread-3| I120: /lib/modules/3.13.0-24-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-04-24T18:13:00.250-05:00| vthread-3| I120: Created new pathsHash.
2014-04-24T18:13:00.255-05:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-24-generic".
2014-04-24T18:13:00.255-05:00| vthread-3| I120: The header path "/lib/modules/3.13.0-24-generic/build/include" for the kernel "3.13.0-24-generic" is valid.  Whoohoo!
2014-04-24T18:13:00.334-05:00| vthread-3| I120: Reading in info for the vmmon module.
2014-04-24T18:13:00.334-05:00| vthread-3| I120: Reading in info for the vmnet module.
2014-04-24T18:13:00.334-05:00| vthread-3| I120: Reading in info for the vmblock module.
2014-04-24T18:13:00.334-05:00| vthread-3| I120: Reading in info for the vmci module.
2014-04-24T18:13:00.334-05:00| vthread-3| I120: Reading in info for the vsock module.
2014-04-24T18:13:00.334-05:00| vthread-3| I120: Setting vsock to depend on vmci.
2014-04-24T18:13:00.334-05:00| vthread-3| I120: Invoking modinfo on "vmmon".
2014-04-24T18:13:00.336-05:00| vthread-3| I120: "/sbin/modinfo" exited with status 0.
2014-04-24T18:13:00.336-05:00| vthread-3| I120: Invoking modinfo on "vmnet".
2014-04-24T18:13:00.337-05:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-04-24T18:13:00.337-05:00| vthread-3| I120: Invoking modinfo on "vmblock".
2014-04-24T18:13:00.339-05:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-04-24T18:13:00.339-05:00| vthread-3| I120: Invoking modinfo on "vmci".
2014-04-24T18:13:00.340-05:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-04-24T18:13:00.340-05:00| vthread-3| I120: Invoking modinfo on "vsock".
2014-04-24T18:13:00.342-05:00| vthread-3| I120: "/sbin/modinfo" exited with status 0.
2014-04-24T18:13:00.359-05:00| vthread-3| I120: to be installed: vmnet status: 0
2014-04-24T18:13:00.373-05:00| vthread-3| I120: Obtaining info using the running kernel.
2014-04-24T18:13:00.373-05:00| vthread-3| I120: Setting header path for 3.13.0-24-generic to "/lib/modules/3.13.0-24-generic/build/include".
2014-04-24T18:13:00.373-05:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-24-generic/build/include" for kernel release "3.13.0-24-generic".
2014-04-24T18:13:00.373-05:00| vthread-3| I120: Failed to find /lib/modules/3.13.0-24-generic/build/include/linux/version.h
2014-04-24T18:13:00.373-05:00| vthread-3| I120: /lib/modules/3.13.0-24-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-04-24T18:13:00.382-05:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-24-generic".
2014-04-24T18:13:00.382-05:00| vthread-3| I120: The header path "/lib/modules/3.13.0-24-generic/build/include" for the kernel "3.13.0-24-generic" is valid.  Whoohoo!
2014-04-24T18:13:00.457-05:00| vthread-3| I120: Kernel header path retrieved from FileEntry: /lib/modules/3.13.0-24-generic/build/include
2014-04-24T18:13:00.457-05:00| vthread-3| I120: Update kernel header path to /lib/modules/3.13.0-24-generic/build/include
2014-04-24T18:13:00.457-05:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-24-generic/build/include" for kernel release "3.13.0-24-generic".
2014-04-24T18:13:00.457-05:00| vthread-3| I120: Failed to find /lib/modules/3.13.0-24-generic/build/include/linux/version.h
2014-04-24T18:13:00.457-05:00| vthread-3| I120: /lib/modules/3.13.0-24-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-04-24T18:13:00.467-05:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-24-generic".
2014-04-24T18:13:00.467-05:00| vthread-3| I120: The header path "/lib/modules/3.13.0-24-generic/build/include" for the kernel "3.13.0-24-generic" is valid.  Whoohoo!
2014-04-24T18:13:00.469-05:00| vthread-3| I120: Found compiler at "/usr/bin/gcc"
2014-04-24T18:13:00.473-05:00| vthread-3| I120: Got gcc version "4.8".
2014-04-24T18:13:00.473-05:00| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-04-24T18:13:00.473-05:00| vthread-3| I120: Using user supplied compiler "/usr/bin/gcc".
2014-04-24T18:13:00.476-05:00| vthread-3| I120: Got gcc version "4.8".
2014-04-24T18:13:00.476-05:00| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-04-24T18:13:00.483-05:00| vthread-3| I120: Trying to find a suitable PBM set for kernel "3.13.0-24-generic".
2014-04-24T18:13:00.483-05:00| vthread-3| I120: No matching PBM set was found for kernel "3.13.0-24-generic".
2014-04-24T18:13:00.484-05:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-24-generic/build/include" for kernel release "3.13.0-24-generic".
2014-04-24T18:13:00.484-05:00| vthread-3| I120: Failed to find /lib/modules/3.13.0-24-generic/build/include/linux/version.h
2014-04-24T18:13:00.484-05:00| vthread-3| I120: /lib/modules/3.13.0-24-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-04-24T18:13:00.494-05:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-24-generic".
2014-04-24T18:13:00.494-05:00| vthread-3| I120: The header path "/lib/modules/3.13.0-24-generic/build/include" for the kernel "3.13.0-24-generic" is valid.  Whoohoo!
2014-04-24T18:13:00.494-05:00| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-04-24T18:13:00.496-05:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-24-generic/build/include" for kernel release "3.13.0-24-generic".
2014-04-24T18:13:00.496-05:00| vthread-3| I120: Failed to find /lib/modules/3.13.0-24-generic/build/include/linux/version.h
2014-04-24T18:13:00.496-05:00| vthread-3| I120: /lib/modules/3.13.0-24-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-04-24T18:13:00.507-05:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-24-generic".
2014-04-24T18:13:00.507-05:00| vthread-3| I120: The header path "/lib/modules/3.13.0-24-generic/build/include" for the kernel "3.13.0-24-generic" is valid.  Whoohoo!
2014-04-24T18:13:00.507-05:00| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-04-24T18:13:00.507-05:00| vthread-3| I120: Using temp dir "/tmp".
2014-04-24T18:13:00.508-05:00| vthread-3| I120: Obtaining info using the running kernel.
2014-04-24T18:13:00.508-05:00| vthread-3| I120: Setting header path for 3.13.0-24-generic to "/lib/modules/3.13.0-24-generic/build/include".
2014-04-24T18:13:00.508-05:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-24-generic/build/include" for kernel release "3.13.0-24-generic".
2014-04-24T18:13:00.508-05:00| vthread-3| I120: Failed to find /lib/modules/3.13.0-24-generic/build/include/linux/version.h
2014-04-24T18:13:00.508-05:00| vthread-3| I120: /lib/modules/3.13.0-24-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-04-24T18:13:00.518-05:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-24-generic".
2014-04-24T18:13:00.518-05:00| vthread-3| I120: The header path "/lib/modules/3.13.0-24-generic/build/include" for the kernel "3.13.0-24-generic" is valid.  Whoohoo!
2014-04-24T18:13:00.598-05:00| vthread-3| I120: Invoking modinfo on "vmnet".
2014-04-24T18:13:00.600-05:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-04-24T18:13:00.919-05:00| vthread-3| I120: Setting destination path for vmnet to "/lib/modules/3.13.0-24-generic/misc/vmnet.ko".
2014-04-24T18:13:00.919-05:00| vthread-3| I120: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2014-04-24T18:13:00.923-05:00| vthread-3| I120: Successfully extracted the vmnet source.
2014-04-24T18:13:00.923-05:00| vthread-3| I120: Building module with command "/usr/bin/make -j4 -C /tmp/modconfig-arrVV4/vmnet-only auto-build HEADER_DIR=/lib/modules/3.13.0-24-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2014-04-24T18:13:03.063-05:00| vthread-3| W110: Failed to build vmnet.  Failed to execute the build command.

This is VMware Wrokstation 9.x - any ideas?

---

### Post by ubfan1 on 2014-04-24
Same errors with the vmplayer 5.02 in my 14.04 upgrade.  Installed the vmplayer 6.01 and at least got a reasonable looking error:
  CC [M]  /tmp/modconfig-plO6Uk/vmnet-only/bridge.o
  CC [M]  /tmp/modconfig-plO6Uk/vmnet-only/filter.o
/tmp/modconfig-plO6Uk/vmnet-only/filter.c:206:1: error: conflicting types for &#8216;VNetFilterHookFn&#8217;
 VNetFilterHookFn(unsigned int hooknum,                 // IN:
 ^
/tmp/modconfig-plO6Uk/vmnet-only/filter.c:64:18: note: previous declaration of &#8216;VNetFilterHookFn&#8217; was here
 static nf_hookfn VNetFilterHookFn;
                  ^
/tmp/modconfig-plO6Uk/vmnet-only/filter.c:64:18: warning: &#8216;VNetFilterHookFn&#8217; used but never defined [enabled by default]
/tmp/modconfig-plO6Uk/vmnet-only/filter.c:206:1: warning: &#8216;VNetFilterHookFn&#8217; defined but not used [-Wunused-function]
 VNetFilterHookFn(unsigned int hooknum,                 // IN:
 ^
make[2]: *** [/tmp/modconfig-plO6Uk/vmnet-only/filter.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[1]: *** [_module_/tmp/modconfig-plO6Uk/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/modconfig-plO6Uk/vmnet-only'
Unable to install all modules.  See log for details.

The 6.01 vmplayer was fine under 13.10, so I  bought over the bundle.  Maybe I should download another copy and see if it has been fixed, but since I only had some old XP vms, I don't care much if I can't get it to run.

---

### Post by ubfan1 on 2014-04-29
Upgraded to the 6.02 vmplayer without any problems.  Try the latest workstation.

---

### Post by dwhitney67 on 2014-05-12
> **ubfan1 said:**
> Upgraded to the 6.02 vmplayer without any problems.  Try the latest workstation.

It was not so cut/dry as you indicated.  I upgraded my Kubuntu 12.04 to 14.04 two weeks ago.  Little did I know that the kernel was not updated.  I was running kernel version 3.2.0-53-generic, for which apparently VMPlayer 6.02 could not find the kernel headers.  Even an apt-get of those headers proved fruitless.

[ATTACH=CONFIG]253091[/ATTACH]

After using the (Muon) Package Manager to upgrade to the latest kernel version available (3.13.0-24-generic) I was able to get VMPlayer working.

---

### Post by honzag on 2015-03-25
> **ubfan1 said:**
> Same errors with the vmplayer 5.02 in my 14.04 upgrade.  Installed the vmplayer 6.01 and at least got a reasonable looking error:
  CC [M]  /tmp/modconfig-plO6Uk/vmnet-only/bridge.o
  CC [M]  /tmp/modconfig-plO6Uk/vmnet-only/filter.o
/tmp/modconfig-plO6Uk/vmnet-only/filter.c:206:1: error: conflicting types for ‘VNetFilterHookFn’
 VNetFilterHookFn(unsigned int hooknum,                 // IN:
 ^
/tmp/modconfig-plO6Uk/vmnet-only/filter.c:64:18: note: previous declaration of ‘VNetFilterHookFn’ was here
 static nf_hookfn VNetFilterHookFn;
                  ^
/tmp/modconfig-plO6Uk/vmnet-only/filter.c:64:18: warning: ‘VNetFilterHookFn’ used but never defined [enabled by default]
/tmp/modconfig-plO6Uk/vmnet-only/filter.c:206:1: warning: ‘VNetFilterHookFn’ defined but not used [-Wunused-function]
 VNetFilterHookFn(unsigned int hooknum,                 // IN:
 ^
make[2]: *** [/tmp/modconfig-plO6Uk/vmnet-only/filter.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[1]: *** [_module_/tmp/modconfig-plO6Uk/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/modconfig-plO6Uk/vmnet-only'
Unable to install all modules.  See log for details.

The 6.01 vmplayer was fine under 13.10, so I  bought over the bundle.  Maybe I should download another copy and see if it has been fixed, but since I only had some old XP vms, I don't care much if I can't get it to run.

I guess that this workarround would help to you:
[http://dandar3.blogspot.cz/2014/01/vmware-player-601-on-ubuntu-1404-alpha.html](http://dandar3.blogspot.cz/2014/01/vmware-player-601-on-ubuntu-1404-alpha.html)
or originally at
[https://communities.vmware.com/thread/467832](https://communities.vmware.com/thread/467832)  (beware of non-printing chars!)  
or
[http://davejingtian.org/2014/03/04/hack-make-vmware-player-6-0-1-start-on-linux-kernel-3-13-x/](http://davejingtian.org/2014/03/04/hack-make-vmware-player-6-0-1-start-on-linux-kernel-3-13-x/)

It worked for my vmplayer4 , too.

---

### Post by nargaroth_reg on 2015-06-24
> **honzag said:**
> I guess that this workarround would help to you:
[http://dandar3.blogspot.cz/2014/01/vmware-player-601-on-ubuntu-1404-alpha.html](http://dandar3.blogspot.cz/2014/01/vmware-player-601-on-ubuntu-1404-alpha.html)
or originally at
[https://communities.vmware.com/thread/467832](https://communities.vmware.com/thread/467832)  (beware of non-printing chars!)  
or
[http://davejingtian.org/2014/03/04/hack-make-vmware-player-6-0-1-start-on-linux-kernel-3-13-x/](http://davejingtian.org/2014/03/04/hack-make-vmware-player-6-0-1-start-on-linux-kernel-3-13-x/)

It worked for my vmplayer4 , too.
Thanks, I had this problem and it worked for me as well (using ubuntu 14.04 and vmware x64 10.0.0).

---


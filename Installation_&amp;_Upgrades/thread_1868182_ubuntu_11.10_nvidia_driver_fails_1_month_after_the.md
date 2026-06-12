---
title: "ubuntu 11.10 nvidia driver fails 1 month after the instalation"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by odror on 2011-10-23
Hardware NVIDIA GTX 550 Ti

For no apparent reason my video driver failed after working for one month. I used the current driver. Than I tried the ppa driver from x-swat 285.05.09-0ubuntu1. I get the same error. jockey also fail when re-installing the nvidia driver. I had to ininstall as follows: apt-get-install nvidia-current.

xorg.conf have this cryptic error:
> [    25.137]    compiled for 4.0.2, module version = 1.0.0
[    25.137]    Module class: X.Org Server Extension
[    25.137] (II) NVIDIA GLX Module  285.05.09  Fri Sep 23 17:51:24 PDT 2011
[    25.137] (II) Loading extension GLX
[    25.137] (II) LoadModule: "record"
[    25.138] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    25.138] (II) Module record: vendor="X.Org Foundation"
[    25.138]    compiled for 1.10.4, module version = 1.13.0
[    25.138]    Module class: X.Org Server Extension
[    25.138]    ABI class: X.Org Server Extension, version 5.0
[    25.138] (II) Loading extension RECORD
[    25.138] (II) LoadModule: "dri"
[    25.138] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    25.139] (II) Module dri: vendor="X.Org Foundation"
[    25.139]    compiled for 1.10.4, module version = 1.0.0
[    25.139]    ABI class: X.Org Server Extension, version 5.0
[    25.139] (II) Loading extension XFree86-DRI
[    25.139] (II) LoadModule: "dri2"
[    25.139] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.139] (II) Module dri2: vendor="X.Org Foundation"
[    25.139]    compiled for 1.10.4, module version = 1.2.0
[    25.139]    ABI class: X.Org Server Extension, version 5.0
[    25.139] (II) Loading extension DRI2
[    25.139] (II) LoadModule: "nvidia"
[    25.139] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/nvidia_drv.so
[    25.140] (II) Module nvidia: vendor="NVIDIA Corporation"
[    25.140]    compiled for 4.0.2, module version = 1.0.0
[    25.140]    Module class: X.Org Video Driver
[    25.142] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    25.142] (EE) NVIDIA:     system's kernel log for additional error messages.
[    25.142] (II) UnloadModule: "nvidia"
[    25.142] (II) Unloading nvidia
[    25.142] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    25.142] (EE) No drivers available.
[    25.142] 
Fatal server error:
[    25.142] no screens found
[    25.142] 
Please consult the The X.Org Foundation support 
         at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    25.142] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    25.142] 


I have the latest version of all the modules. Any help will be appreciated. Thanks

---

### Post by odror on 2011-10-24
I forgot to mention but the jockey error is:
> 2011-10-23 20:45:34,426 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-23 20:45:34,427 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting


---


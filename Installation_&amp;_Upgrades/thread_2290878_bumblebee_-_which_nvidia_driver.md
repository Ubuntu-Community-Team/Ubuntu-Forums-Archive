---
title: "bumblebee - which nvidia driver?"
date: 2015-08-16
forum: Installation &amp; Upgrades
---

### Post by akos.maroy on 2015-08-16
HI,

I did a clean ubuntu 14.04 LTS install an az Asus UX32 laptop, which has an nviida card in it. after the clean install, I installed bumblebee and bumblebee-nvidia, with the expectation that it would 'just work'. Unfortunately it doesn't.

After such an installation, bumblebee-nvidia pulles in nvidia-current, which is nvidia-304. the module is built, but won't load:

```
$ find /lib/modules -name nvidia*
/lib/modules/3.19.0-25-generic/kernel/drivers/video/fbdev/nvidia
/lib/modules/3.19.0-25-generic/kernel/drivers/video/fbdev/nvidia/nvidiafb.ko
/lib/modules/3.19.0-25-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.19.0-25-generic/updates/dkms/nvidia_304.ko
$ sudo modprobe nvidia
modprobe: FATAL: Module nvidia not found.
$ sudo modprobe nvidia-304
modprobe: ERROR: could not insert 'nvidia_304': No such device

```

as a result, bumblee doesn't find the nvidia module either:

```
$ sudo bumblebeed -vv
[  474.743841] [DEBUG]Found card: 03:00.0 (discrete)
[  474.743896] [DEBUG]Found card: 00:02.0 (integrated)
[  474.743920] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[  474.744315] [INFO]Configured driver: nvidia
[  474.744358] [DEBUG]Skipping auto-detection, using configured driver 'nvidia'
[  474.744525] [DEBUG]Process /sbin/modprobe started, PID 22233.
[  474.744607] [DEBUG]Hiding stderr for execution of /sbin/modprobe
[  474.746439] [DEBUG]SIGCHILD received, but wait failed with No child processes
[  474.746518] [DEBUG]bbswitch has been detected.
[  474.746524] [INFO]Switching method 'bbswitch' is available and will be used.
[  474.746530] [DEBUG]Active configuration:
[  474.746534] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[  474.746538] [DEBUG] X display: :8
[  474.746542] [DEBUG] LD_LIBRARY_PATH: /usr/lib/nvidia-304:/usr/lib32/nvidia-304
[  474.746547] [DEBUG] Socket path: /var/run/bumblebee.socket
[  474.746551] [DEBUG] pidfile: /var/run/bumblebeed.pid
[  474.746555] [DEBUG] xorg.conf file: /etc/bumblebee/xorg.conf.nvidia
[  474.746560] [DEBUG] xorg.conf.d dir: /etc/bumblebee/xorg.conf.d
[  474.746564] [DEBUG] ModulePath: /usr/lib/nvidia-304/xorg,/usr/lib/xorg/modules
[  474.746569] [DEBUG] GID name: bumblebee
[  474.746573] [DEBUG] Power method: auto
[  474.746577] [DEBUG] Stop X on exit: 1
[  474.746581] [DEBUG] Driver: nvidia
[  474.746585] [DEBUG] Driver module: nvidia
[  474.746589] [DEBUG] Card shutdown state: 1
[  474.746723] [DEBUG]Process /sbin/modprobe started, PID 22234.
[  474.746810] [DEBUG]Hiding stderr for execution of /sbin/modprobe
[  474.748642] [DEBUG]SIGCHILD received, but wait failed with No child processes
[  474.748665] [ERROR]Module 'nvidia' is not found.

```

if I try an apt-get purge nvidia*, then apt-get install nvidia-346 nvidia-346-uvm, then i can load the nvidia module:

```

$ sudo modprobe nvidia
$ sudo lsmod | grep nvidia
nvidia               8380416  0 
drm                   344064  6 i915,drm_kms_helper,nvidia

```

then I change /etc/bumblebee/bumblebee.conf  to reflect /usr/lib/nvidia-346/... , then bumblebee finds the module:

```
$ sudo bumblebeed -vv
[ 1008.829680] [DEBUG]Found card: 03:00.0 (discrete)
[ 1008.829712] [DEBUG]Found card: 00:02.0 (integrated)
[ 1008.829719] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[ 1008.829873] [INFO]Configured driver: nvidia
[ 1008.829897] [DEBUG]Skipping auto-detection, using configured driver 'nvidia'
[ 1008.829980] [DEBUG]Process /sbin/modprobe started, PID 9908.
[ 1008.830018] [DEBUG]Hiding stderr for execution of /sbin/modprobe
[ 1008.830801] [DEBUG]SIGCHILD received, but wait failed with No child processes
[ 1008.830832] [DEBUG]bbswitch has been detected.
[ 1008.830834] [INFO]Switching method 'bbswitch' is available and will be used.
[ 1008.830836] [DEBUG]Active configuration:
[ 1008.830838] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[ 1008.830839] [DEBUG] X display: :8
[ 1008.830841] [DEBUG] LD_LIBRARY_PATH: /usr/lib/nvidia-346:/usr/lib32/nvidia-346
[ 1008.830842] [DEBUG] Socket path: /var/run/bumblebee.socket
[ 1008.830844] [DEBUG] pidfile: /var/run/bumblebeed.pid
[ 1008.830845] [DEBUG] xorg.conf file: /etc/bumblebee/xorg.conf.nvidia
[ 1008.830847] [DEBUG] xorg.conf.d dir: /etc/bumblebee/xorg.conf.d
[ 1008.830849] [DEBUG] ModulePath: /usr/lib/nvidia-346/xorg,/usr/lib/xorg/modules
[ 1008.830850] [DEBUG] GID name: bumblebee
[ 1008.830852] [DEBUG] Power method: auto
[ 1008.830853] [DEBUG] Stop X on exit: 1
[ 1008.830855] [DEBUG] Driver: nvidia
[ 1008.830856] [DEBUG] Driver module: nvidia
[ 1008.830858] [DEBUG] Card shutdown state: 1
[ 1008.830931] [DEBUG]Process /sbin/modprobe started, PID 9909.
[ 1008.830962] [DEBUG]Hiding stderr for execution of /sbin/modprobe
[ 1008.831818] [DEBUG]SIGCHILD received, but wait failed with No child processes
[ 1008.831828] [DEBUG]Configuration test passed.
[ 1008.832115] [INFO]bumblebeed 3.2.1 started
[ 1008.832201] [INFO]Switching dedicated card OFF [bbswitch]
[ 1008.860336] [INFO]Initialization completed - now handling client requests

```

but: now my 'regular' X is busted. e.g.:

```
$ glxinfo | head
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  24 (X_GLXCreateNewContext)
  Value in failed request:  0x0
  Serial number of failed request:  31
  Current serial number in output stream:  32
name of display: :0

```

but, things run through optirun:

```
$ optirun glxinfo | head
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_ARB_context_flush_control, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_ARB_create_context_robustness, 
    GLX_ARB_fbconfig_float, GLX_ARB_multisample, GLX_EXT_buffer_age, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_create_context_es_profile, 

```

and, as a result, if I log out & log in again, I'm getting a blank screen. In essence, my X is ruined.


what am I doing wrong? why is this not working on an LTS release?

---

### Post by dino99 on 2015-08-16
errors from above, so it seems  related to glx: which mesa version is installed ? (maybe some versions not expected)
if there is a xorg.conf around, then rename it, the kernel prefer to deal with X itself
if you also have some packages installed from ppa(s), then downgrade them if they works with glx

Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  24 (X_GLXCreateNewContext)

Wonder if bumblebee-nvidia do the real job it might:
doc: It does so by configuring the OpenGL library path to use the Mesa graphics library.  **** looks like it could be the culprit

---


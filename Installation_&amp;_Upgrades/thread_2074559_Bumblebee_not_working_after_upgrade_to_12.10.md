---
title: "Bumblebee not working after upgrade to 12.10"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by Stonecold1995 on 2012-10-21
I use to be able to use Bumblebee's "optirun" command, but now that I upgraded to Kubuntu 12.10, it's no longer working.

Here's the output of optirun:
```
alex@kubuntu:~$ optirun -vv glxspheres
[51698.088234] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[51698.088638] [INFO]Configured driver: nouveau
[51698.196161] [DEBUG]optirun version 3.0.1 starting...
[51698.196182] [DEBUG]Active configuration:
[51698.196189] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[51698.196196] [DEBUG] X display: :8
[51698.196203] [DEBUG] LD_LIBRARY_PATH: 
[51698.196209] [DEBUG] Socket path: /var/run/bumblebee.socket
[51698.196216] [DEBUG] VGL Compression: proxy
[51700.678645] [INFO]Response: No - error: [XORG] (EE) [drm] Could not set DRM device bus ID.

[51700.678668] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) [drm] Could not set DRM device bus ID.

[51700.678675] [DEBUG]Socket closed.
[51700.678693] [ERROR]Aborting because fallback start is disabled.
[51700.678699] [DEBUG]Killing all remaining processes.
```

And here's the contents of "/etc/bumblebee/bumblebee.conf":
```
# Configuration file for Bumblebee. Values should **not** be put between quotes

## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=true
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=nouveau


## Client options. Will take effect on the next optirun executed.
[optirun]
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false


# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
#         bbswitch - new in BB 3, recommended if available
#       switcheroo - vga_switcheroo method, use at your own risk
#             none - disable PM completely
# https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods

## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-current
Module=nvidia
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-current:/usr/lib32/nvidia-current
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia

## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau
```

**EDIT: I found out how.  For some reason nouveau won't work with Bumblebee but the closed-source Nvidia driver now does!**

---

### Post by Lekensteyn on 2013-02-22
nouveau is blacklisted when you have nvidia installed. In order to use nouveau, either uninstall nvidia or edit /etc/modprobe.d/nvidia-current_hybrid.conf (exacty name may differ, but it ends with _hybrid.conf) and remove the "alias nouveau off" line.

---

### Post by Jedcurtis on 2013-02-24
If you have an Nvidia graphics device, then your bumblebee.conf file is not using it.  If the line that says "driver=" is left empty or specifies 'nouveau' it will default to using the Nouveau driver.  This is not good as the Nouveau driver seriously suffers from old age!  Again, what I'm saying here is this will only work if, when you installed Bumblebee, you also installed the bumblebee-nvidia driver.  If so the following applies...

Your bumblebee.conf file is incorrect;
driver=nouveau
should instead read;
driver=nvidia  (not bumblebee-nvidia, and not nvidia-current, just nvidia)
Especially if you have installed Bumblebee correctly!  Nouveau is old and seriously out of date...

---

### Post by gnusci on 2013-02-24
Reinstall:

sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic

---


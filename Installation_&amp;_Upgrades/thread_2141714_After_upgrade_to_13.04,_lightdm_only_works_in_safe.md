---
title: "After upgrade to 13.04, lightdm only works in safe mode (1024x768 resolution)"
date: 2013-05-03
forum: Installation &amp; Upgrades
---

### Post by dpapathanasiou on 2013-05-03
I upgraded to 13.04 by running this command from xterm:

```
sudo do-release-upgrade
```

The upgrade didn't report any problems, and after rebooting, the greeter came up normally.

After logging in, though, the screen was mangled and distorted.

I shut down, then restarted in safe mode.

At that resolution (1024x768) the desktop was normal, and the only errors I found in the lightdm logs were these:

```
$ sudo grep -i err /var/log/lightdm/*.log
/var/log/lightdm/x-0-greeter.log:** (at-spi2-registryd:2010): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
/var/log/lightdm/x-0-greeter.log:** (gnome-settings-daemon:2033): WARNING **: Unable to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
/var/log/lightdm/x-0-greeter.log:(gnome-settings-daemon:2033): power-plugin-WARNING **: IsInhibited failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
/var/log/lightdm/x-0.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/lightdm/x-1-greeter.log:[+21.21s] WARNING: unity-greeter: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
/var/log/lightdm/x-1.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
```

Any ideas how to resolve this?

---

### Post by 2F4U on 2013-05-03
What graphics card do you have and which driver are/were you using?

---

### Post by dpapathanasiou on 2013-05-03
Here's the output of 'sudo lshw -c video'

```
  *-display       description: VGA compatible controller
       product: C61 [GeForce 6150SE nForce 430]
       vendor: NVIDIA Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:22 memory:fb000000-fbffffff memory:e0000000-efffffff memory:fc000000-fcffffff memory:80000000-8001ffff
```

And this is the output of 'sudo modinfo nouveau'

```
filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko
license:        GPL and additional rights
description:    nVidia Riva/TNT/GeForce/Quadro/Tesla
author:         Nouveau Project
srcversion:     8654B2CF2419C2A36D40480
alias:          pci:v000012D2d*sv*sd*bc03sc*i*
alias:          pci:v000010DEd*sv*sd*bc03sc*i*
depends:        drm,drm_kms_helper,ttm,mxm-wmi,wmi,video,i2c-algo-bit
intree:         Y
vermagic:       3.8.0-19-generic SMP mod_unload modversions 
parm:           perflvl:Performance level (default: boot) (charp)
parm:           perflvl_wr:Allow perflvl changes (warning: dangerous!) (int)
parm:           tv_norm:Default TV norm.
        Supported: PAL, PAL-M, PAL-N, PAL-Nc, NTSC-M, NTSC-J,
            hd480i, hd480p, hd576i, hd576p, hd720p, hd1080i.
        Default: PAL
        *NOTE* Ignored for cards with external TV encoders. (charp)
parm:           tv_disable:Disable TV-out detection (int)
parm:           ignorelid:Ignore ACPI lid status (int)
parm:           duallink:Allow dual-link TMDS (default: enabled) (int)
parm:           nofbaccel:Disable fbcon acceleration (int)
parm:           agpmode:AGP mode (0 to disable AGP) (int)
parm:           vram_pushbuf:Create DMA push buffers in VRAM (int)
parm:           config:option string to pass to driver core (charp)
parm:           debug:debug string to pass to driver core (charp)
parm:           noaccel:disable kernel/abi16 acceleration (int)
parm:           modeset:enable driver (default: auto, 0 = disabled, 1 = enabled, 2 = headless) (int)
```

---

### Post by dpapathanasiou on 2013-05-06
I solved this problem from switching the nvidia driver.

As per the prior output, I had been using the open-source **Nouveau** driver, but I switched to the **nvidia-304 (proprietary, tested)** option in the software updater:

[IMG]http://i.imgur.com/XtM5biv.png[/IMG]

Interestingly, it now says "this device is using the recommended driver":

[IMG]http://i.imgur.com/T52GX9Z.png[/IMG]

---


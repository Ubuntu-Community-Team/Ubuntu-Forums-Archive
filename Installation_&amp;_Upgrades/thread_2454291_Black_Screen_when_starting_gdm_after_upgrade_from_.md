---
title: "Black Screen when starting gdm after upgrade from 18.04. to 20.04. on nvidia drivers"
date: 2020-11-26
forum: Installation &amp; Upgrades
---

### Post by vilwarin on 2020-11-26
Problem Description:
Starting any display manager (tried gdm, lightdm, sddm) while using nvidia drivers (tried 390, 440, 450, 455) after upgrading Ubuntu from 18.04. to 20.04. results in a black screen.

Kernel:
$uname -r
```
5.6.0-1033-oem
```

I did not find any noticeable errors in /var/log/syslog /var/log/Xorg.0.log or ~/.xsession-errors. Also no noticeable errors in demesg or systemctl status display-manager
nvidia drivers seem to load fine. nvidia-smi displays my card Geforce GTX 950M and lsmod lists nvidia drivers.

$nvidia-smi
```
    +-----------------------------------------------------------------------------+
    | NVIDIA-SMI 440.100      Driver Version: 440.100      CUDA Version: 10.2     |
    |-------------------------------+----------------------+----------------------+
    | GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
    | Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
    |===============================+======================+======================|
    |   0  GeForce GTX 950M    Off  | 00000000:01:00.0 Off |                  N/A |
    | N/A   60C    P8    N/A /  N/A |     19MiB /  2004MiB |      0%      Default |
    +-------------------------------+----------------------+----------------------+
    +-----------------------------------------------------------------------------+
    | Processes:                                                       GPU Memory |
    |  GPU       PID   Type   Process name                             Usage      |
    |=============================================================================|
    |    0      4007      G   /usr/lib/xorg/Xorg                             9MiB |
    |    0      4479      G   /usr/bin/gnome-shell                        1MiB |
    +-----------------------------------------------------------------------------+

```

$lsmod | grep nvidia
```

    nvidia_uvm            962560  0
    nvidia_drm             45056  4
    nvidia_modeset       1114112  4 nvidia_drm
    nvidia              20680704  205 nvidia_uvm,nvidia_modeset
    drm_kms_helper        208896  1 nvidia_drm
    drm                   540672  7 drm_kms_helper,nvidia_drm
    ipmi_msghandler       110592  2 ipmi_devintf,nvidia

```

The graphics card is an Optimus card.
with prime-select nvidia is selected:

$sudo prime-select nvidia
```
Info: the nvidia profile is already set
```

I tried to follow advice on this forum (e.g. adding nomodeset to grub, blacklisting nouveau, etc.) to no avail.

purging all nvidia drivers results in the display manager starting under nouveau driver.
before the upgrade to 20.04. the setup was running fine with nvidia-440 drivers.

Any ideas what I could do?

---

### Post by vilwarin on 2020-11-30
For everybody ending up on this post:

I am a big step further and have the drivers and X running.
What I was missing is that for some reason Xorg in current versions is reading-in not only /etc/X11/xorg.conf but all files in that folder starting with xorg.conf (so e.g. xorg.conf.failsafe or xorg.conf_backup) - and that lead to X not starting without any error messages pointing the way.
What I thus did is remove all xorg.conf* files from /etc/X11/ and uncomment all nvidia related things in /usr/share/X11/xorg.conf.d/10-nvidia.conf and 11-nvidia-prime.conf and then started from there gradually uncommenting things until I had a working config.

My current setup now allows me to run the proprietary drivers for the integrated Intel GPU.
I am not yet able to render things with the NVIDIA GPU.

Currently mine looks like this:

/usr/share/X11/xorg.conf.d/10-nvidia.conf

```
 Section &#8220;OutputClass&#8221;
    Identifier &#8220;nvidia&#8221;
    MatchDriver &#8220;nvidia-drm&#8221;
    Driver &#8220;nvidia&#8221;
    Option &#8220;AllowEmptyInitialConfiguration&#8221;
    ModulePath &#8220;/usr/lib/x86_64-linux-gnu/nvidia/xorg&#8221;
    EndSection

```

/etc/X11/xorg.conf

```

    Section &#8220;Files&#8221;
    ModulePath &#8220;/usr/lib/xorg/modules&#8221;
    ModulePath &#8220;/usr/lib/x86_64-linux-gnu/nvidia/xorg&#8221;
    EndSection

    Section &#8220;Module&#8221;
    Load &#8220;modesetting&#8221;
    Load &#8220;glxserver_nvidia&#8221;
    Load &#8220;glx&#8221;
    EndSection

    Section &#8220;ServerLayout&#8221;
    Identifier &#8220;layout&#8221;
    Screen 0 &#8220;nvidia&#8221;
    Inactive &#8220;intel&#8221;
    Option &#8220;AllowNVIDIAGPUScreens&#8221;
    EndSection

    Section &#8220;Device&#8221;
    Identifier &#8220;intel&#8221;
    Driver &#8220;modesetting&#8221;
    BusID &#8220;PCI:0@0:2:0&#8221;
    #Option &#8220;AccelMethod&#8221; &#8220;none&#8221;
    EndSection

    Section &#8220;Screen&#8221;
    Identifier &#8220;intel&#8221;
    Device &#8220;intel&#8221;
    EndSection

    #Section &#8220;Device&#8221;
    #Identifier &#8220;nvidia&#8221;
    #Driver &#8220;nvidia&#8221;
    #BusID &#8220;PCI:1@0:0:0&#8221;
    #Option &#8220;AllowEmptyInitialConfiguration&#8221;
    #EndSection

    Section &#8220;Screen&#8221;
    Identifier &#8220;nvidia&#8221;
    Device &#8220;nvidia&#8221;
    EndSection

```

Anything commented out will lead to X not starting when being commented-in.
Hope that helps.

My guess is that that the Output Class Section in 10-nvidia.conf and the nvidia device section in xorg.conf conflict.
Therefore there must only be one.

---

### Post by vilwarin on 2020-11-30
So I still want to get the NVIDIA GPU running, that’s why I have this notebook :)

$ inxi -G
```

    Graphics:
    Device-1: Intel 4th Gen Core Processor Integrated Graphics driver: i915
    v: kernel
    Device-2: NVIDIA GM107M [GeForce GTX 950M] driver: nvidia v: 455.45.01
    Display: server: X.Org 1.20.8 driver: modesetting,nvidia
    unloaded: fbdev,nouveau,vesa resolution: 1920x1200~60Hz
    OpenGL: renderer: Mesa DRI Intel HD Graphics 4600 (HSW GT2)
    v: 4.5 Mesa 20.0.8

```

Seems OpenGL renderer is set to intel, although I want Nvidia.

Xorg.0.log reveals two distinct EE:
(EE) Failed to load module “glxservernvidia” (module does not exist, 0)
(EE) modeset(0): failed to set mode: Permission denied

full Xorg.0.log
[https://paste.ubuntu.com/p/23PcYBbpR3/](https://paste.ubuntu.com/p/23PcYBbpR3/)

(EE) modeset(0): failed to set mode: Permission denied
some how xrandr lists two times modesetting. expected would be 1 modesetting and 1 NVIDIA-0

$ xrandr --listproviders
```

    Providers: number : 2
    Provider 0: id: 0x45 cap: 0x9, Source Output, Sink Offload crtcs: 3 outputs: 3 associated providers: 0 name:modesetting
    Provider 1: id: 0xea cap: 0x0 crtcs: 0 outputs: 0 associated providers: 0 name:modesetting

```

(EE) Failed to load module “glxservernvidia” (module does not exist, 0)

Peculiar here is that the module is named glxserver_nvidia and not glxservernvidia.
In fact searching for glxservernvidia does almost not yield any results on Google, and leads to Google suggesting “did you mean glxserver_nvidia ?”.

$ ls /usr/lib/x86_64-linux-gnu/nvidia/xorg
```

libglxserver_nvidia.so
libglxserver_nvidia.so.455.45.01
nvidia_drv.so

```

Any idea where glxservernvidia could come from?
Or about the modesetting permission error?

---

### Post by vilwarin on 2020-12-16
Thanks to help on the Nvidia Developer Forum I was able to get the Performance Mode (NVIDIA-only) working.

The final step was to have no xorg.conf at all and let ubuntu prime-select handle all xorg configuration via files it autogenerates in /usr/share/X11/xorg.conf.d/
After deleting xorg.conf (and a lot of additional steps I’ve already done up to this point) - NVIDIA drivers are working fine now.

For comparison:

$ inxi -G
```
Graphics:
Device-1: Intel 4th Gen Core Processor Integrated Graphics driver: i915
v: kernel
Device-2: NVIDIA GM107M [GeForce GTX 950M] driver: nvidia v: 455.45.01
Display: server: X.Org 1.20.8 driver: modesetting
unloaded: fbdev,nouveau,nvidia,vesa resolution: 1920x1200~60Hz
OpenGL: renderer: GeForce GTX 950M/PCIe/SSE2 v: 4.6.0 NVIDIA 455.45.01
```

$ xrandr --listproviders
```
Providers: number : 2
Provider 0: id: 0x1b8 cap: 0x1, Source Output crtcs: 0 outputs: 0 associated providers: 1 name:NVIDIA-0
Provider 1: id: 0x1de cap: 0x6, Sink Output, Source Offload crtcs: 3 outputs: 3 associated providers: 1 name:modesetting
```

hope this helps others also stumbling at this point!

Cheers and happy winter solstice!

Michael

---


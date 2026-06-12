---
title: "How to switch video drivers?"
date: 2018-09-28
forum: Installation &amp; Upgrades
---

### Post by skewray2 on 2018-09-28
I recently upgraded to the latest lubuntu and used synaptic to switch the driver from nouveau to nvidia-driver-390. It hung up partway through the process. I noticed high CPU thrashing, and it was due to a runaway systemd-udevd process. Dmesg had an error about conflicting drivers. So, I uninstalled and reinstalled nvidia-driver-390. No more runaway, but "lspci -k" says that the nouveau driver is still  being used. How do I switch to nvidia-390? I tried synaptic, but it just hangs.

---

### Post by deadflowr on 2018-09-28
rebooted yet?

---

### Post by skewray2 on 2018-09-28
Rebooting doesn't help. Still the nouveau driver.

---

### Post by Bashing-om on 2018-09-29
skewray2; Hello -

How have you confirmed that the 390 version driver is the correct one for your card ?
post back:
```

lspci -k | grep -EA2 'VGA|3D'
dpkg -l | grep -i nvidia
lsmod | grep nvidia
cat /var/log/gpu-manager.log

```

see what we can figure out for the why.

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by skewray2 on 2018-09-29
I just assumed that Synaptic was suggesting the correct drivers. I suppose, since it hung up, that it may be less smart that I assumed. Output from your commands:

```

D4) lspci -k | grep -EA2 'VGA|3D'
01:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 680] (rev a1)
    Subsystem: eVga.com. Corp. GK104 [GeForce GTX 680]
    Kernel driver in use: nouveau
D5) dpkg -l | grep -i nvidia
ii  libnvidia-cfg1-390:amd64              390.48-0ubuntu3                            amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-390                  390.48-0ubuntu3                            all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-390:amd64           390.48-0ubuntu3                            amd64        NVIDIA libcompute package
ii  libnvidia-compute-390:i386            390.48-0ubuntu3                            i386         NVIDIA libcompute package
ii  libnvidia-decode-390:amd64            390.48-0ubuntu3                            amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-390:i386             390.48-0ubuntu3                            i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-390:amd64            390.48-0ubuntu3                            amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-390:i386             390.48-0ubuntu3                            i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-390:amd64              390.48-0ubuntu3                            amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-390:i386               390.48-0ubuntu3                            i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-390:amd64                390.48-0ubuntu3                            amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-390:i386                 390.48-0ubuntu3                            i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-390:amd64              390.48-0ubuntu3                            amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-390:i386               390.48-0ubuntu3                            i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-390              390.48-0ubuntu3                            amd64        NVIDIA compute utilities
ii  nvidia-dkms-390                       390.48-0ubuntu3                            amd64        NVIDIA DKMS package
ii  nvidia-driver-390                     390.48-0ubuntu3                            amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-390              390.48-0ubuntu3                            amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-390              390.48-0ubuntu3                            amd64        NVIDIA kernel source package
ii  nvidia-prime                          0.8.8                                      all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                       390.42-0ubuntu1                            amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-390                      390.48-0ubuntu3                            amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-390         390.48-0ubuntu3                            amd64        NVIDIA binary Xorg driver
D6) lsmod | grep nvidia
nvidia              14340096  1
D7) cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-34-generic/updates/dkms
Found nvidia module: nvidia-drm.ko
Looking for amdgpu modules in /lib/modules/4.15.0-34-generic/updates/dkms
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? yes
Is nouveau blacklisted? no
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 10de:1180
BusID "PCI:1@0:0:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "nouveau"
Skipping "/dev/dri/card0", driven by "nouveau"
Found "/dev/dri/card0", driven by "nouveau"
output 0:
    card0-DVI-I-1
output 1:
    card0-HDMI-A-1
Number of connected outputs for /dev/dri/card0: 2
Skipping "/dev/dri/card0", driven by "nouveau"
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do

```

---

### Post by Bashing-om on 2018-09-29
skewray2; Well !

We do have a mystery on our hands - confirmed that 390 is the correct version driver.
> 
Is nvidia loaded? yes
Is nouveau loaded? yes
Is nouveau blacklisted? no
Found "/dev/dri/card0", driven by "nouveau"

so, why are both drivers loaded - there can be only one !

post back: - Between code tags, please !
```

ls -al /etc/modprobe.d/
ls -al /usr/share/X11/xorg.conf.d/*.conf
cat /var/log/Xorg.0.log

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]the hunt is on
[/INDENT][/INDENT]

---

### Post by skewray2 on 2018-09-29
ps...still have runaway systemd-udevd process:

```
[ 9871.430778] nvidia-nvlink: Unregistered the Nvlink Core, major device number 240
[ 9871.512899] nvidia-nvlink: Nvlink Core is being initialized, major device number 240
[ 9871.513114] NVRM: The NVIDIA probe routine was not called for 1 device(s).
[ 9871.513115] NVRM: This can occur when a driver such as: 
               NVRM: nouveau, rivafb, nvidiafb or rivatv 
               NVRM: was loaded and obtained ownership of the NVIDIA device(s).
[ 9871.513115] NVRM: Try unloading the conflicting kernel module (and/or
               NVRM: reconfigure your kernel without the conflicting
               NVRM: driver(s)), then try loading the NVIDIA kernel module
               NVRM: again.
[ 9871.513115] NVRM: No NVIDIA graphics adapter probed!
[ 9871.513187] nvidia-nvlink: Unregistered the Nvlink Core, major device number 240
```

---

### Post by Bashing-om on 2018-09-29
skewray2; 

Code tags - to promote readability -

in addition then to the above - show:
```

echo $XDG_SESSION_TYPE

```

[INDENT]sometimes I do wonder
[/INDENT]

---

### Post by skewray2 on 2018-09-29
echo $XDG_SESSION_TYPE returns "x11".

---

### Post by deadflowr on 2018-09-30
You needed to post the output of post #6's requested commands in conjunction with the output from post #8.
(Post #8 output is known, but it's unclear the state of what comes from those of the commands in post #6.)

Use code tags, as instructed already.

---

### Post by skewray2 on 2018-09-30
```

D44) ls -al /etc/modprobe.d/
total 68
 4 drwxr-xr-x   2 root root  4096 Sep 28 09:09 ./
12 drwxr-xr-x 161 root root 12288 Sep 28 09:10 ../
 4 -rw-r--r--   1 root root   154 Nov 29  2016 amd64-microcode-blacklist.conf
 4 -rw-r--r--   1 root root   325 Apr 18  2013 blacklist-ath_pci.conf
 4 -rw-r--r--   1 root root  1603 Apr 18  2013 blacklist.conf
 4 -rw-r--r--   1 root root   210 Apr 18  2013 blacklist-firewire.conf
 4 -rw-r--r--   1 root root   697 Oct 14  2014 blacklist-framebuffer.conf
 4 -rw-r--r--   1 root root   583 Apr 18  2013 blacklist-rare-network.conf
 4 -rw-r--r--   1 root root  1077 Apr 18  2013 blacklist-watchdog.conf
 0 -rw-r--r--   1 root root     0 Nov 22  2014 dkms.conf
 4 -rw-r--r--   1 root root   154 May  3 12:45 intel-microcode-blacklist.conf
 4 -rw-r--r--   1 root root   347 Apr 18  2013 iwlwifi.conf
 4 -rw-r--r--   1 root root    16 Oct 10  2013 libpisock9.conf
 4 -rw-r--r--   1 root root   379 Jul 28  2016 mdadm.conf
 0 lrwxrwxrwx   1 root root    49 May 30 06:46 nvidia-graphics-drivers.conf -> /etc/alternatives/x86_64-linux-gnu_nvidia_modconf
 4 -rw-r--r--   1 root root    81 Apr 18 10:01 nvidia-graphics-drivers.conf.dpkg-new
 4 -rw-r--r--   1 root root    30 Jul 10  2013 vmwgfx-fbdev.conf
D45) ls -al /usr/share/X11/xorg.conf.d/*.conf
4 -rw-r--r-- 1 root root   92 Mar 20  2018 /usr/share/X11/xorg.conf.d/10-amdgpu.conf
4 -rw-r--r-- 1 root root 1099 Mar  7  2017 /usr/share/X11/xorg.conf.d/10-evdev.conf
4 -rw-r--r-- 1 root root  206 Apr 18 10:01 /usr/share/X11/xorg.conf.d/10-nvidia.conf
4 -rw-r--r-- 1 root root 1350 Apr 13 08:31 /usr/share/X11/xorg.conf.d/10-quirks.conf
4 -rw-r--r-- 1 root root   92 Mar 20  2018 /usr/share/X11/xorg.conf.d/10-radeon.conf
4 -rw-r--r-- 1 root root  590 Mar  7  2017 /usr/share/X11/xorg.conf.d/11-evdev-quirks.conf
4 -rw-r--r-- 1 root root  364 Mar  7  2017 /usr/share/X11/xorg.conf.d/11-evdev-trackpoint.conf
4 -rw-r--r-- 1 root root  945 Apr 11 00:50 /usr/share/X11/xorg.conf.d/40-libinput.conf
4 -rw-r--r-- 1 root root  590 Mar  7  2017 /usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
4 -rw-r--r-- 1 root root 1751 Mar  7  2017 /usr/share/X11/xorg.conf.d/70-synaptics.conf
4 -rw-r--r-- 1 root root 3025 Apr  3 00:39 /usr/share/X11/xorg.conf.d/70-wacom.conf
0 lrwxrwxrwx 1 root root   29 Nov  1  2017 /usr/share/X11/xorg.conf.d/glamoregl.conf -> /etc/alternatives/glamor_conf
D46) cat /var/log/Xorg.0.log
[     5.304] 
X.Org X Server 1.19.6
Release Date: 2017-12-20
[     5.304] X Protocol Version 11, Revision 0
[     5.304] Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
[     5.304] Current Operating System: Linux device 4.15.0-34-generic #37-Ubuntu SMP Mon Aug 27 15:21:48 UTC 2018 x86_64
[     5.304] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-34-generic root=UUID=56c146b8-ca77-456e-8606-3395117a8441 ro quiet splash nomdmonddf nomdmonisw nomdmonddf nomdmonisw nomdmonddf nomdmonisw nomdmonddf nomdmonisw
[     5.304] Build Date: 13 April 2018  08:07:36PM
[     5.304] xorg-server 2:1.19.6-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[     5.304] Current version of pixman: 0.34.0
[     5.304]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     5.304] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.304] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 28 20:36:17 2018
[     5.306] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.309] (==) No Layout section.  Using the first Screen section.
[     5.309] (==) No screen section available. Using defaults.
[     5.309] (**) |-->Screen "Default Screen Section" (0)
[     5.309] (**) |   |-->Monitor "<default monitor>"
[     5.310] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     5.310] (==) Automatically adding devices
[     5.310] (==) Automatically enabling devices
[     5.310] (==) Automatically adding GPU devices
[     5.310] (==) Automatically binding GPU devices
[     5.310] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     5.310] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.311]     Entry deleted from font path.
[     5.311] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.311]     Entry deleted from font path.
[     5.311] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.311]     Entry deleted from font path.
[     5.311] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.311]     Entry deleted from font path.
[     5.311] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.311]     Entry deleted from font path.
[     5.311] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     5.311] (==) ModulePath set to "/usr/lib/xorg/modules"
[     5.311] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     5.311] (II) Loader magic: 0x55e835f23020
[     5.311] (II) Module ABI versions:
[     5.311]     X.Org ANSI C Emulation: 0.4
[     5.311]     X.Org Video Driver: 23.0
[     5.311]     X.Org XInput driver : 24.1
[     5.311]     X.Org Server Extension : 10.0
[     5.311] (++) using VT number 7

[     5.311] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     5.312] (II) xfree86: Adding drm device (/dev/dri/card0)
[     5.314] (--) PCI:*(0:1:0:0) 10de:1180:3842:2680 rev 161, Mem @ 0xf6000000/16777216, 0xe8000000/134217728, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/131072
[     5.314] (II) LoadModule: "glx"
[     5.316] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     5.322] (II) Module glx: vendor="X.Org Foundation"
[     5.322]     compiled for 1.19.6, module version = 1.0.0
[     5.322]     ABI class: X.Org Server Extension, version 10.0
[     5.322] (==) Matched nouveau as autoconfigured driver 0
[     5.322] (==) Matched nouveau as autoconfigured driver 1
[     5.322] (==) Matched modesetting as autoconfigured driver 2
[     5.322] (==) Matched fbdev as autoconfigured driver 3
[     5.322] (==) Matched vesa as autoconfigured driver 4
[     5.322] (==) Assigned the driver to the xf86ConfigLayout
[     5.322] (II) LoadModule: "nouveau"
[     5.322] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     5.324] (II) Module nouveau: vendor="X.Org Foundation"
[     5.324]     compiled for 1.19.3, module version = 1.0.15
[     5.324]     Module class: X.Org Video Driver
[     5.324]     ABI class: X.Org Video Driver, version 23.0
[     5.324] (II) LoadModule: "modesetting"
[     5.324] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     5.325] (II) Module modesetting: vendor="X.Org Foundation"
[     5.325]     compiled for 1.19.6, module version = 1.19.6
[     5.325]     Module class: X.Org Video Driver
[     5.325]     ABI class: X.Org Video Driver, version 23.0
[     5.325] (II) LoadModule: "fbdev"
[     5.325] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.325] (II) Module fbdev: vendor="X.Org Foundation"
[     5.325]     compiled for 1.19.3, module version = 0.4.4
[     5.325]     Module class: X.Org Video Driver
[     5.325]     ABI class: X.Org Video Driver, version 23.0
[     5.325] (II) LoadModule: "vesa"
[     5.325] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.325] (II) Module vesa: vendor="X.Org Foundation"
[     5.325]     compiled for 1.19.3, module version = 2.3.4
[     5.325]     Module class: X.Org Video Driver
[     5.325]     ABI class: X.Org Video Driver, version 23.0
[     5.325] (II) NOUVEAU driver Date:   Fri Apr 21 14:41:17 2017 -0400
[     5.325] (II) NOUVEAU driver for NVIDIA chipset families :
[     5.325]     RIVA TNT        (NV04)
[     5.325]     RIVA TNT2       (NV05)
[     5.325]     GeForce 256     (NV10)
[     5.325]     GeForce 2       (NV11, NV15)
[     5.325]     GeForce 4MX     (NV17, NV18)
[     5.325]     GeForce 3       (NV20)
[     5.325]     GeForce 4Ti     (NV25, NV28)
[     5.325]     GeForce FX      (NV3x)
[     5.325]     GeForce 6       (NV4x)
[     5.326]     GeForce 7       (G7x)
[     5.326]     GeForce 8       (G8x)
[     5.326]     GeForce GTX 200 (NVA0)
[     5.326]     GeForce GTX 400 (NVC0)
[     5.326] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     5.326] (II) FBDEV: driver for framebuffer: fbdev
[     5.326] (II) VESA: driver for VESA chipsets: vesa
[     5.338] (II) [drm] nouveau interface version: 1.3.1
[     5.338] (WW) Falling back to old probe method for modesetting
[     5.339] (WW) Falling back to old probe method for fbdev
[     5.339] (II) Loading sub module "fbdevhw"
[     5.339] (II) LoadModule: "fbdevhw"
[     5.339] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     5.339] (II) Module fbdevhw: vendor="X.Org Foundation"
[     5.339]     compiled for 1.19.6, module version = 0.0.2
[     5.339]     ABI class: X.Org Video Driver, version 23.0
[     5.339] (WW) Falling back to old probe method for vesa
[     5.339] (II) Loading sub module "dri2"
[     5.339] (II) LoadModule: "dri2"
[     5.339] (II) Module "dri2" already built-in
[     5.339] (--) NOUVEAU(0): Chipset: "NVIDIA NVE4"
[     5.339] (II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     5.339] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[     5.339] (==) NOUVEAU(0): RGB weight 888
[     5.339] (==) NOUVEAU(0): Default visual is TrueColor
[     5.339] (==) NOUVEAU(0): Using HW cursor
[     5.339] (==) NOUVEAU(0): Allowed maximum DRI level 2.
[     5.339] (==) NOUVEAU(0): GLX sync to VBlank enabled.
[     5.339] (==) NOUVEAU(0): Page flipping enabled
[     5.339] (==) NOUVEAU(0): Swap limit set to 1 [Max allowed 2]
[     5.339] (==) NOUVEAU(0): Page flipping synced to vblank by kernel.
[     5.339] (II) NOUVEAU(0): Initializing outputs ...
[     5.373] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[     5.374] (II) NOUVEAU(0): Output DVI-D-1 has no monitor section
[     5.408] (II) NOUVEAU(0): Output HDMI-1 has no monitor section
[     5.472] (II) NOUVEAU(0): Output DP-1 has no monitor section
[     5.472] (II) NOUVEAU(0): 4 crtcs needed for screen.
[     5.472] (II) NOUVEAU(0): Allocated crtc nr. 0 to this screen.
[     5.472] (II) NOUVEAU(0): Allocated crtc nr. 1 to this screen.
[     5.472] (II) NOUVEAU(0): Allocated crtc nr. 2 to this screen.
[     5.472] (II) NOUVEAU(0): Allocated crtc nr. 3 to this screen.
[     5.505] (II) NOUVEAU(0): EDID for output DVI-I-1
[     5.505] (II) NOUVEAU(0): Manufacturer: ACR  Model: 281  Serial#: 811610094
[     5.505] (II) NOUVEAU(0): Year: 2013  Week: 6
[     5.505] (II) NOUVEAU(0): EDID Version: 1.3
[     5.505] (II) NOUVEAU(0): Digital Display Input
[     5.505] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[     5.505] (II) NOUVEAU(0): Gamma: 2.20
[     5.505] (II) NOUVEAU(0): DPMS capabilities: StandBy Off
[     5.505] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     5.505] (II) NOUVEAU(0): Default color space is primary color space
[     5.505] (II) NOUVEAU(0): First detailed timing is preferred mode
[     5.505] (II) NOUVEAU(0): redX: 0.642 redY: 0.332   greenX: 0.305 greenY: 0.625
[     5.505] (II) NOUVEAU(0): blueX: 0.150 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
[     5.505] (II) NOUVEAU(0): Supported established timings:
[     5.505] (II) NOUVEAU(0): 720x400@70Hz
[     5.505] (II) NOUVEAU(0): 640x480@60Hz
[     5.505] (II) NOUVEAU(0): 640x480@67Hz
[     5.505] (II) NOUVEAU(0): 800x600@56Hz
[     5.505] (II) NOUVEAU(0): 800x600@60Hz
[     5.505] (II) NOUVEAU(0): 1024x768@60Hz
[     5.505] (II) NOUVEAU(0): 1024x768@70Hz
[     5.505] (II) NOUVEAU(0): Manufacturer's mask: 0
[     5.505] (II) NOUVEAU(0): Supported standard timings:
[     5.505] (II) NOUVEAU(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[     5.505] (II) NOUVEAU(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     5.505] (II) NOUVEAU(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
[     5.505] (II) NOUVEAU(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[     5.505] (II) NOUVEAU(0): #4: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[     5.505] (II) NOUVEAU(0): Supported detailed timing:
[     5.505] (II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[     5.505] (II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     5.505] (II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     5.505] (II) NOUVEAU(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 175 MHz
[     5.505] (II) NOUVEAU(0): Monitor name: S220HQL
[     5.505] (II) NOUVEAU(0): Serial No: LTK0R0292401
[     5.505] (II) NOUVEAU(0): EDID (in hex):
[     5.505] (II) NOUVEAU(0):     00ffffffffffff0004728102ee2f6030
[     5.505] (II) NOUVEAU(0):     0617010380301b78ae40a5a4554ea026
[     5.505] (II) NOUVEAU(0):     115054b30c00714f818081009500d1c0
[     5.505] (II) NOUVEAU(0):     010101010101023a801871382d40582c
[     5.505] (II) NOUVEAU(0):     4500dd0c1100001e000000fd00374b1e
[     5.505] (II) NOUVEAU(0):     5011000a202020202020000000fc0053
[     5.505] (II) NOUVEAU(0):     32323048514c0a2020202020000000ff
[     5.505] (II) NOUVEAU(0):     004c544b3052303239323430310a009d
[     5.505] (II) NOUVEAU(0): Printing probed modes for output DVI-I-1
[     5.505] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     5.505] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     5.505] (II) NOUVEAU(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     5.505] (II) NOUVEAU(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     5.505] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     5.506] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     5.506] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     5.506] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     5.506] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     5.506] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     5.506] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     5.506] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     5.507] (II) NOUVEAU(0): EDID for output DVI-D-1
[     5.540] (II) NOUVEAU(0): EDID for output HDMI-1
[     5.540] (II) NOUVEAU(0): Manufacturer: ACR  Model: 101  Serial#: 2475722209
[     5.540] (II) NOUVEAU(0): Year: 2009  Week: 39
[     5.540] (II) NOUVEAU(0): EDID Version: 1.3
[     5.540] (II) NOUVEAU(0): Digital Display Input
[     5.540] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[     5.540] (II) NOUVEAU(0): Gamma: 2.20
[     5.540] (II) NOUVEAU(0): DPMS capabilities: Off
[     5.540] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     5.540] (II) NOUVEAU(0): First detailed timing is preferred mode
[     5.540] (II) NOUVEAU(0): redX: 0.646 redY: 0.334   greenX: 0.303 greenY: 0.616
[     5.540] (II) NOUVEAU(0): blueX: 0.147 blueY: 0.067   whiteX: 0.313 whiteY: 0.329
[     5.540] (II) NOUVEAU(0): Supported established timings:
[     5.540] (II) NOUVEAU(0): 720x400@70Hz
[     5.540] (II) NOUVEAU(0): 640x480@60Hz
[     5.540] (II) NOUVEAU(0): 640x480@67Hz
[     5.540] (II) NOUVEAU(0): 800x600@56Hz
[     5.540] (II) NOUVEAU(0): 800x600@60Hz
[     5.540] (II) NOUVEAU(0): 1024x768@60Hz
[     5.540] (II) NOUVEAU(0): 1024x768@70Hz
[     5.540] (II) NOUVEAU(0): Manufacturer's mask: 0
[     5.540] (II) NOUVEAU(0): Supported standard timings:
[     5.540] (II) NOUVEAU(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[     5.540] (II) NOUVEAU(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
[     5.540] (II) NOUVEAU(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     5.540] (II) NOUVEAU(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[     5.540] (II) NOUVEAU(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[     5.540] (II) NOUVEAU(0): #5: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[     5.540] (II) NOUVEAU(0): Supported detailed timing:
[     5.540] (II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[     5.540] (II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     5.540] (II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     5.540] (II) NOUVEAU(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[     5.540] (II) NOUVEAU(0): Monitor name: Acer E211H
[     5.540] (II) NOUVEAU(0): Serial No: Q270W0014310
[     5.540] (II) NOUVEAU(0): EDID (in hex):
[     5.540] (II) NOUVEAU(0):     00ffffffffffff0004720101e1859093
[     5.540] (II) NOUVEAU(0):     2713010380301b782aabd5a5554d9d25
[     5.540] (II) NOUVEAU(0):     115054b30c00714f810081809500b300
[     5.540] (II) NOUVEAU(0):     d1c001010101023a801871382d40582c
[     5.540] (II) NOUVEAU(0):     4500dd0c1100001e000000fd00384b1e
[     5.540] (II) NOUVEAU(0):     5311000a202020202020000000fc0041
[     5.540] (II) NOUVEAU(0):     6365722045323131480a2020000000ff
[     5.540] (II) NOUVEAU(0):     005132373057303031343331300a0002
[     5.541] (II) NOUVEAU(0): Printing probed modes for output HDMI-1
[     5.541] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     5.541] (II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     5.541] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     5.541] (II) NOUVEAU(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     5.541] (II) NOUVEAU(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     5.541] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     5.541] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     5.541] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     5.541] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     5.541] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     5.541] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     5.541] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     5.541] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     5.604] (II) NOUVEAU(0): EDID for output DP-1
[     5.604] (II) NOUVEAU(0): Output DVI-I-1 connected
[     5.604] (II) NOUVEAU(0): Output DVI-D-1 disconnected
[     5.604] (II) NOUVEAU(0): Output HDMI-1 connected
[     5.604] (II) NOUVEAU(0): Output DP-1 disconnected
[     5.604] (II) NOUVEAU(0): Using spanning desktop for initial modes
[     5.604] (II) NOUVEAU(0): Output DVI-I-1 using initial mode 1920x1080 +0+0
[     5.604] (II) NOUVEAU(0): Output HDMI-1 using initial mode 1920x1080 +1920+0
[     5.604] (==) NOUVEAU(0): Using gamma correction (1.0, 1.0, 1.0)
[     5.604] (--) NOUVEAU(0): Virtual size is 3840x1080 (pitch 0)
[     5.604] (**) NOUVEAU(0):  Driver mode "1920x1080": 148.5 MHz (scaled from 0.0 MHz), 67.5 kHz, 60.0 Hz
[     5.604] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     5.604] (**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[     5.604] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     5.604] (**) NOUVEAU(0):  Driver mode "1440x900": 88.8 MHz (scaled from 0.0 MHz), 55.5 kHz, 59.9 Hz
[     5.604] (II) NOUVEAU(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     5.604] (**) NOUVEAU(0):  Driver mode "1280x800": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 59.9 Hz
[     5.604] (II) NOUVEAU(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     5.604] (**) NOUVEAU(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
[     5.604] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     5.604] (**) NOUVEAU(0):  Driver mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
[     5.604] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     5.604] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[     5.604] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     5.604] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[     5.604] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     5.604] (**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[     5.604] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     5.604] (**) NOUVEAU(0):  Driver mode "640x480": 30.2 MHz (scaled from 0.0 MHz), 35.0 kHz, 66.7 Hz
[     5.604] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     5.604] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
[     5.604] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     5.604] (**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
[     5.604] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     5.604] (==) NOUVEAU(0): DPI set to (96, 96)
[     5.604] (II) Loading sub module "fb"
[     5.604] (II) LoadModule: "fb"
[     5.604] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.605] (II) Module fb: vendor="X.Org Foundation"
[     5.605]     compiled for 1.19.6, module version = 1.0.0
[     5.605]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.605] (II) Loading sub module "shadowfb"
[     5.605] (II) LoadModule: "shadowfb"
[     5.605] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[     5.605] (II) Module shadowfb: vendor="X.Org Foundation"
[     5.605]     compiled for 1.19.6, module version = 1.0.0
[     5.605]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.605] (II) UnloadModule: "modesetting"
[     5.605] (II) Unloading modesetting
[     5.606] (II) UnloadModule: "fbdev"
[     5.606] (II) Unloading fbdev
[     5.606] (II) UnloadSubModule: "fbdevhw"
[     5.606] (II) Unloading fbdevhw
[     5.606] (II) UnloadModule: "vesa"
[     5.606] (II) Unloading vesa
[     5.606] (--) Depth 24 pixmap format is 32 bpp
[     5.607] (II) NOUVEAU(0): Channel setup complete.
[     5.607] (II) NOUVEAU(0): [COPY] async initialised.
[     5.608] (II) NOUVEAU(0): Hardware support for Present enabled
[     5.608] (II) NOUVEAU(0): [DRI2] Setup complete
[     5.608] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[     5.608] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[     5.608] (II) Loading sub module "exa"
[     5.608] (II) LoadModule: "exa"
[     5.608] (II) Loading /usr/lib/xorg/modules/libexa.so
[     5.609] (II) Module exa: vendor="X.Org Foundation"
[     5.609]     compiled for 1.19.6, module version = 2.6.0
[     5.609]     ABI class: X.Org Video Driver, version 23.0
[     5.609] (II) EXA(0): Driver allocated offscreen pixmaps
[     5.609] (II) EXA(0): Driver registered support for the following operations:
[     5.609] (II)         Solid
[     5.609] (II)         Copy
[     5.609] (II)         Composite (RENDER acceleration)
[     5.609] (II)         UploadToScreen
[     5.609] (II)         DownloadFromScreen
[     5.609] (==) NOUVEAU(0): Backing store enabled
[     5.609] (==) NOUVEAU(0): Silken mouse enabled
[     5.609] (II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
[     5.609] (II) NOUVEAU(0): [XvMC] Extension initialized.
[     5.609] (==) NOUVEAU(0): DPMS enabled
[     5.609] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     5.610] (--) RandR disabled
[     5.612] (II) SELinux: Disabled on system
[     5.707] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     5.707] (II) AIGLX: enabled GLX_ARB_create_context
[     5.707] (II) AIGLX: enabled GLX_ARB_create_context_profile
[     5.707] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[     5.707] (II) AIGLX: enabled GLX_INTEL_swap_event
[     5.707] (II) AIGLX: enabled GLX_SGI_swap_control
[     5.707] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[     5.707] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[     5.707] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[     5.707] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     5.708] (II) AIGLX: Loaded and initialized nouveau
[     5.708] (II) GLX: Initialized DRI2 GL provider for screen 0
[     5.709] (II) NOUVEAU(0): NVEnterVT is called.
[     5.737] (II) NOUVEAU(0): Setting screen physical size to 1016 x 285
[     5.737] resize called 3840 1080
[     5.775] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     5.775] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.775] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[     5.775] (II) LoadModule: "libinput"
[     5.775] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[     5.778] (II) Module libinput: vendor="X.Org Foundation"
[     5.778]     compiled for 1.19.6, module version = 0.27.1
[     5.778]     Module class: X.Org XInput Driver
[     5.778]     ABI class: X.Org XInput driver, version 24.1
[     5.778] (II) Using input driver 'libinput' for 'Power Button'
[     5.778] (**) Power Button: always reports core events
[     5.778] (**) Option "Device" "/dev/input/event1"
[     5.778] (**) Option "_source" "server/udev"
[     5.778] (II) event1  - Power Button: is tagged by udev as: Keyboard
[     5.778] (II) event1  - Power Button: device is a keyboard
[     5.778] (II) event1  - Power Button: device removed
[     5.816] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     5.816] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     5.816] (**) Option "xkb_model" "pc105"
[     5.816] (**) Option "xkb_layout" "us"
[     5.816] (II) event1  - Power Button: is tagged by udev as: Keyboard
[     5.816] (II) event1  - Power Button: device is a keyboard
[     5.816] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     5.816] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.816] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[     5.816] (II) Using input driver 'libinput' for 'Power Button'
[     5.816] (**) Power Button: always reports core events
[     5.816] (**) Option "Device" "/dev/input/event0"
[     5.816] (**) Option "_source" "server/udev"
[     5.817] (II) event0  - Power Button: is tagged by udev as: Keyboard
[     5.817] (II) event0  - Power Button: device is a keyboard
[     5.817] (II) event0  - Power Button: device removed
[     5.856] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     5.856] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     5.856] (**) Option "xkb_model" "pc105"
[     5.856] (**) Option "xkb_layout" "us"
[     5.856] (II) event0  - Power Button: is tagged by udev as: Keyboard
[     5.856] (II) event0  - Power Button: device is a keyboard
[     5.857] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event12)
[     5.857] (II) No input driver specified, ignoring this device.
[     5.857] (II) This device may have been added with another device file.
[     5.857] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event13)
[     5.857] (II) No input driver specified, ignoring this device.
[     5.857] (II) This device may have been added with another device file.
[     5.857] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event14)
[     5.857] (II) No input driver specified, ignoring this device.
[     5.857] (II) This device may have been added with another device file.
[     5.857] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event15)
[     5.857] (II) No input driver specified, ignoring this device.
[     5.857] (II) This device may have been added with another device file.
[     5.858] (II) config/udev: Adding input device HDA Intel PCH Line Out Side (/dev/input/event10)
[     5.858] (II) No input driver specified, ignoring this device.
[     5.858] (II) This device may have been added with another device file.
[     5.858] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event11)
[     5.858] (II) No input driver specified, ignoring this device.
[     5.858] (II) This device may have been added with another device file.
[     5.858] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event4)
[     5.858] (II) No input driver specified, ignoring this device.
[     5.858] (II) This device may have been added with another device file.
[     5.858] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event5)
[     5.858] (II) No input driver specified, ignoring this device.
[     5.858] (II) This device may have been added with another device file.
[     5.859] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event6)
[     5.859] (II) No input driver specified, ignoring this device.
[     5.859] (II) This device may have been added with another device file.
[     5.859] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event7)
[     5.859] (II) No input driver specified, ignoring this device.
[     5.859] (II) This device may have been added with another device file.
[     5.859] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event8)
[     5.859] (II) No input driver specified, ignoring this device.
[     5.859] (II) This device may have been added with another device file.
[     5.859] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event9)
[     5.859] (II) No input driver specified, ignoring this device.
[     5.859] (II) This device may have been added with another device file.
[     5.860] (II) config/udev: Adding input device Kensington      USB/PS2 Wheel Mouse (/dev/input/event3)
[     5.860] (**) Kensington      USB/PS2 Wheel Mouse: Applying InputClass "evdev pointer catchall"
[     5.860] (**) Kensington      USB/PS2 Wheel Mouse: Applying InputClass "libinput pointer catchall"
[     5.860] (II) Using input driver 'libinput' for 'Kensington      USB/PS2 Wheel Mouse'
[     5.860] (**) Kensington      USB/PS2 Wheel Mouse: always reports core events
[     5.860] (**) Option "Device" "/dev/input/event3"
[     5.860] (**) Option "_source" "server/udev"
[     5.920] (II) event3  - Kensington      USB/PS2 Wheel Mouse: is tagged by udev as: Mouse
[     5.920] (II) event3  - Kensington      USB/PS2 Wheel Mouse: device is a pointer
[     5.920] (II) event3  - Kensington      USB/PS2 Wheel Mouse: device removed
[     5.980] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.7/0000:04:00.0/usb5/5-1/5-1:1.0/0003:047D:1029.0002/input/input3/event3"
[     5.980] (II) XINPUT: Adding extended input device "Kensington      USB/PS2 Wheel Mouse" (type: MOUSE, id 8)
[     5.980] (**) Option "AccelerationScheme" "none"
[     5.980] (**) Kensington      USB/PS2 Wheel Mouse: (accel) selected scheme none/0
[     5.980] (**) Kensington      USB/PS2 Wheel Mouse: (accel) acceleration factor: 2.000
[     5.980] (**) Kensington      USB/PS2 Wheel Mouse: (accel) acceleration threshold: 4
[     6.040] (II) event3  - Kensington      USB/PS2 Wheel Mouse: is tagged by udev as: Mouse
[     6.040] (II) event3  - Kensington      USB/PS2 Wheel Mouse: device is a pointer
[     6.040] (II) config/udev: Adding input device Kensington      USB/PS2 Wheel Mouse (/dev/input/mouse0)
[     6.040] (II) No input driver specified, ignoring this device.
[     6.040] (II) This device may have been added with another device file.
[     6.041] (II) config/udev: Adding input device HID 046a:0001 (/dev/input/event2)
[     6.041] (**) HID 046a:0001: Applying InputClass "evdev keyboard catchall"
[     6.041] (**) HID 046a:0001: Applying InputClass "libinput keyboard catchall"
[     6.041] (II) Using input driver 'libinput' for 'HID 046a:0001'
[     6.041] (**) HID 046a:0001: always reports core events
[     6.041] (**) Option "Device" "/dev/input/event2"
[     6.041] (**) Option "_source" "server/udev"
[     6.041] (II) event2  - HID 046a:0001: is tagged by udev as: Keyboard
[     6.041] (II) event2  - HID 046a:0001: device is a keyboard
[     6.041] (II) event2  - HID 046a:0001: device removed
[     6.064] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.7/0000:04:00.0/usb5/5-2/5-2:1.0/0003:046A:0001.0001/input/input2/event2"
[     6.064] (II) XINPUT: Adding extended input device "HID 046a:0001" (type: KEYBOARD, id 9)
[     6.064] (**) Option "xkb_model" "pc105"
[     6.064] (**) Option "xkb_layout" "us"
[     6.064] (II) event2  - HID 046a:0001: is tagged by udev as: Keyboard
[     6.064] (II) event2  - HID 046a:0001: device is a keyboard
[    14.468] (II) NOUVEAU(0): EDID vendor "ACR", prod id 641
[    14.468] (II) NOUVEAU(0): Using EDID range info for horizontal sync
[    14.468] (II) NOUVEAU(0): Using EDID range info for vertical refresh
[    14.468] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    14.468] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    14.468] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    14.468] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    14.468] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    14.468] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    14.468] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    14.468] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    14.468] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    14.468] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    14.468] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    14.468] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    14.468] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    14.468] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    14.840] resize called 3840 1080
[    14.875] (II) NOUVEAU(0): EDID vendor "ACR", prod id 641
[    14.875] (II) NOUVEAU(0): Using hsync ranges from config file
[    14.875] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    14.875] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    14.875] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    14.875] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    14.875] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    14.875] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    14.875] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    14.875] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    14.875] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    14.875] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    14.875] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    14.875] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    14.875] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    14.875] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    14.875] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
D47) echo $XDG_SESSION_TYPE
x11

```

---

### Post by ubfan1 on 2018-09-30
Looks like you have some old (non Ubuntu) Nvidia configuration files which mess things up.  The nvidia-graphics-drivers.conf file should not be a link, and should blacklist the nouveau drivers:  

```
$ cat /etc/modprobe.d/nvidia-graphics-drivers.conf  
blacklist nouveau
blacklist lbm-nouveau
alias nouveau off
alias lbm-nouveau off
```

You have this (based on the size) in the nvidia-graphics-drivers.conf.dpkg-new file, so delete the link, and rename that file to nvidia-graphics-drivers.conf

---

### Post by skewray2 on 2018-09-30
I deleted the link and renamed the file, which has exactly the contents that you showed. After a reboot, I still get the errors in 'dmesg' and the runaway systemd-udevd process. Now:
```

D9) ls -al /etc/modprobe.d/
total 68
 4 drwxr-xr-x   2 root root  4096 Sep 30 09:22 ./
12 drwxr-xr-x 161 root root 12288 Sep 28 09:10 ../
 4 -rw-r--r--   1 root root   154 Nov 29  2016 amd64-microcode-blacklist.conf
 4 -rw-r--r--   1 root root   325 Apr 18  2013 blacklist-ath_pci.conf
 4 -rw-r--r--   1 root root  1603 Apr 18  2013 blacklist.conf
 4 -rw-r--r--   1 root root   210 Apr 18  2013 blacklist-firewire.conf
 4 -rw-r--r--   1 root root   697 Oct 14  2014 blacklist-framebuffer.conf
 4 -rw-r--r--   1 root root   583 Apr 18  2013 blacklist-rare-network.conf
 4 -rw-r--r--   1 root root  1077 Apr 18  2013 blacklist-watchdog.conf
 0 -rw-r--r--   1 root root     0 Nov 22  2014 dkms.conf
 4 -rw-r--r--   1 root root   154 May  3 12:45 intel-microcode-blacklist.conf
 4 -rw-r--r--   1 root root   347 Apr 18  2013 iwlwifi.conf
 4 -rw-r--r--   1 root root    16 Oct 10  2013 libpisock9.conf
 4 -rw-r--r--   1 root root   379 Jul 28  2016 mdadm.conf
 4 -rw-r--r--   1 root root    81 Apr 18 10:01 nvidia-graphics-drivers.conf
 4 -rw-r--r--   1 root root    30 Jul 10  2013 vmwgfx-fbdev.conf

```
```

D8) lspci -k | grep -EA2 'VGA|3D'
01:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 680] (rev a1)
    Subsystem: eVga.com. Corp. GK104 [GeForce GTX 680]
    Kernel driver in use: nouveau

```

---

### Post by ubfan1 on 2018-09-30
Lets take a look at what happened at boot with:  
dmesg |egrep -i "nouveau|nvidia"  

The blacklist should prevent the kernel pulling the nouveau by default, but does not prevent anything from explicitly loading it.

---

### Post by skewray2 on 2018-09-30
All I see from 'dmesg | egrep -i "nouveau|nvidia"' is a continuous repeat of:
```

               NVRM: driver(s)), then try loading the NVIDIA kernel module
[ 5629.388120] NVRM: No NVIDIA graphics adapter probed!
[ 5629.388211] nvidia-nvlink: Unregistered the Nvlink Core, major device number 240
[ 5629.438099] nvidia-nvlink: Nvlink Core is being initialized, major device number 240
[ 5629.438317] NVRM: The NVIDIA probe routine was not called for 1 device(s).
               NVRM: nouveau, rivafb, nvidiafb or rivatv 
               NVRM: was loaded and obtained ownership of the NVIDIA device(s).

```
This is the first iteration above, so it doesn't happen right away.

---

### Post by ubfan1 on 2018-09-30
I don't know what that NVRM is, my output looks like:
```
$ dmesg |egrep -i "nouveau|nvidia|NVRM"
[    1.386788] nvidia: loading out-of-tree module taints kernel.
[    1.386799] nvidia: module license 'NVIDIA' taints kernel.
[    1.444276] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[    1.452025] nvidia-nvlink: Nvlink Core is being initialized, major device number 240
[    1.452229] nvidia 0000:01:00.0: enabling device (0000 -> 0003)
[    1.452305] nvidia 0000:01:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=none
[    1.452392] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  390.48  Thu Mar 22 00:42:57 PDT 2018 (using threaded interrupts)
[    1.454175] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  390.48  Wed Mar 21 23:48:34 PDT 2018
[    1.454778] [drm] [nvidia-drm] [GPU ID 0x00000100] Loading driver
[    1.454779] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:01:00.0 on minor 0
[   24.550779] nvidia-uvm: Loaded the UVM driver in 8 mode, major device number 237
```

According to [https://www.x.org/wiki/NVIDIAProprietaryDriver/](https://www.x.org/wiki/NVIDIAProprietaryDriver/)  those NVRM lines are error type messages.
Take a look at the /dev/nv*, mine look like:  
```
$ ls -l /dev/nv*
crw-rw-rw- 1 root root 195,   0 Sep 28 21:34 /dev/nvidia0
crw-rw-rw- 1 root root 195, 255 Sep 28 21:34 /dev/nvidiactl
crw-rw-rw- 1 root root 237,   0 Sep 28 21:34 /dev/nvidia-uvm
crw-r----- 1 root kmem  10, 144 Sep 28 21:34 /dev/nvram
```

You might have to remake them. (See the link).

---

### Post by ubfan1 on 2018-09-30
Just a thought, does your system have an /etc/rc.local file?  Most don't these days, but if present, systemd will run it.  That used to be the place to make last minute modprobes to set up the drivers the preferred way.

---

### Post by skewray2 on 2018-09-30
I have an rc.local file, but the first executable line is "exit 0". For the device files,
```

D1) ls -l /dev/nv*
0 crw-rw-rw- 1 root root 195, 255 Sep 30 15:22 /dev/nvidiactl

```
I ran the script in the link that recreated the /dev/nvidia[0-9] devices. I then checked that they were created correctly. After a reboot, they were gone again.

---

### Post by ubfan1 on 2018-09-30
I don't l;ike the line:
NVRM: No NVIDIA graphics adapter probed!
Maybe the 390 isn't new enough.  You can try the beta of 18.10, and see what their default driver is (hopefully 410?).  Or add the graphics-drivers ppa,
update and see what the recommended driver is.  It's been awhile since I've used a ppa, so if you try that, just search this site and askubuntu.com for graphics-driver
or nvidia.

---

### Post by skewray2 on 2018-09-30
> **ubfan1 said:**
> I don't like the line:
NVRM: No NVIDIA graphics adapter probed!
Maybe the 390 isn't new enough.  You can try the beta of 18.10, and see what their default driver is (hopefully 410?).  Or add the graphics-drivers ppa,
update and see what the recommended driver is.  It's been awhile since I've used a ppa, so if you try that, just search this site and askubuntu.com for graphics-driver
or nvidia.

The graphics card must be at least five years old, and has worked fine with the proprietary drivers for previous incarnations of Ubuntu. I doubt the driver isn't new enough. I think Synaptic hanging up left some steps out or half done.

If no one can figure this out, I can suffer with my computer sucking down an extra kilowatt, fans blowing at full speed and lame graphics, for another three weeks and upgrade to 18.10 when in come out officially. I'd rather not beta test, though.

---

### Post by ubfan1 on 2018-09-30
When you previously did the remove of the nvidia packages, did you use the purge switch (or apt-get purge nvidia...)?  Without the purge, some config files are probably left around.  If not, try the purge and install again).

---


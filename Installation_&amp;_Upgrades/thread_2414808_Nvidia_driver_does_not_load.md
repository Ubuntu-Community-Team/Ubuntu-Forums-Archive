---
title: "Nvidia driver does not load"
date: 2019-03-15
forum: Installation &amp; Upgrades
---

### Post by skottfelt on 2019-03-15
Yet another thread about an Nvidia driver that has been working, but suddenly doesn't load on startup. I think this happened after Ubuntu was updated from 4.15.0-33 to 4.14.0-34, but I am not sure if this is related. I can use my monitor, but it has really low resolution, and takes for ages to update. 
I have looked through the other threads, but none of the solutions that has been proposed has worked for me. I have 
[LIST]
[*]upgraded the driver from 390 to 418,
[*]added nvidia-drm.modeset=1 to grub
[*]purged all nvidia packages and installed everything again
[*]EDIT: starting up using 4.15.0-33 instead of 4.14.0-34
[*]probably a few other things that I have forgotten by now
[/LIST]
but the problem remains the same. I have posted some details below, which I hope can give you some insights.

Thanks in advance for any help you can give me, 
Jesper

```
:~$ nvidia-smi
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.

```

```
:~$ sudo lshw -c display
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: GK104 [GeForce GTX 770]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:17:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:b4000000-b4ffffff memory:a8000000-afffffff memory:b0000000-b1ffffff ioport:7000(size=128) memory:b5000000-b507ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: GK208B [GeForce GT 730]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:65:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d7000000-d7ffffff memory:c8000000-cfffffff memory:d0000000-d1ffffff ioport:b000(size=128) memory:c0000-dffff

```
```

:~$ dpkg -l | grep -i nvidia
ii  libnvidia-cfg1-418:amd64                      418.43-0ubuntu0~18.04.1                      amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-418                          418.43-0ubuntu0~18.04.1                      all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-418:amd64                   418.43-0ubuntu0~18.04.1                      amd64        NVIDIA libcompute package
ii  libnvidia-compute-418:i386                    418.43-0ubuntu0~18.04.1                      i386         NVIDIA libcompute package
ii  libnvidia-decode-418:amd64                    418.43-0ubuntu0~18.04.1                      amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-418:i386                     418.43-0ubuntu0~18.04.1                      i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-418:amd64                    418.43-0ubuntu0~18.04.1                      amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-418:i386                     418.43-0ubuntu0~18.04.1                      i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-418:amd64                      418.43-0ubuntu0~18.04.1                      amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-418:i386                       418.43-0ubuntu0~18.04.1                      i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-418:amd64                        418.43-0ubuntu0~18.04.1                      amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-418:i386                         418.43-0ubuntu0~18.04.1                      i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-418:amd64                      418.43-0ubuntu0~18.04.1                      amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-418:i386                       418.43-0ubuntu0~18.04.1                      i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-418                      418.43-0ubuntu0~18.04.1                      amd64        NVIDIA compute utilities
ii  nvidia-dkms-418                               418.43-0ubuntu0~18.04.1                      amd64        NVIDIA DKMS package
ii  nvidia-driver-418                             418.43-0ubuntu0~18.04.1                      amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-418                      418.43-0ubuntu0~18.04.1                      amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-418                      418.43-0ubuntu0~18.04.1                      amd64        NVIDIA kernel source package
ii  nvidia-prime                                  0.8.8.2                                      all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                               418.43-0ubuntu0~gpu18.04.1                   amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-418                              418.43-0ubuntu0~18.04.1                      amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-418                 418.43-0ubuntu0~18.04.1                      amd64        NVIDIA binary Xorg driver

```

```

:~$ lsmod | grep nvidia
:~$ 
```

```

:~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-34-generic/updates/dkms
Looking for amdgpu modules in /lib/modules/4.15.0-34-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is nvidia kernel module available? no
Is amdgpu kernel module available? no
Vendor/Device Id: 10de:1184
BusID "PCI:23@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:17:00.0/driver
The device is not bound to any driver.
Vendor/Device Id: 10de:1287
BusID "PCI:101@0:0:0"
Is boot vga? yes
Error: can't access /sys/bus/pci/devices/0000:65:00.0/driver
The device is not bound to any driver.
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Does it require offloading? no
last cards number = 2
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 2
Has the system changed? No
Unsupported discrete card vendor: 10de
Nothing to do
```



```

:~$ dmesg | grep nvidia[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-4.15.0-34-generic root=UUID=05e7fb76-dabf-45d1-b88d-f0ed9f79fa98 ro quiet splash nvidia-drm.modeset=1 vt.handoff=1
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-4.15.0-34-generic root=UUID=05e7fb76-dabf-45d1-b88d-f0ed9f79fa98 ro quiet splash nvidia-drm.modeset=1 vt.handoff=1

```

```
:~$ sudo modprobe nvidia
modprobe: FATAL: Module nvidia not found in directory /lib/modules/4.15.0-34-generic

```

---


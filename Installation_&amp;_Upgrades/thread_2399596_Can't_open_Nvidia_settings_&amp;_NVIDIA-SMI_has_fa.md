---
title: "Can't open Nvidia settings &amp; NVIDIA-SMI has failed."
date: 2018-08-27
forum: Installation &amp; Upgrades
---

### Post by niek265 on 2018-08-27
I installed the Nvidia drivers succesfully once, then I removed them  because I had problems with optimus. But because I need them now to run a  couple of programs and games.

Using dpkg -l | grep nvidia:
```

ii  libnvidia-cfg1-390:amd64                   390.77-0ubuntu0~gpu18.04.1          amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-390                       390.77-0ubuntu0~gpu18.04.1          all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-390:amd64                390.77-0ubuntu0~gpu18.04.1          amd64        NVIDIA libcompute package
ii  libnvidia-compute-390:i386                 390.77-0ubuntu0~gpu18.04.1          i386         NVIDIA libcompute package
ii  libnvidia-decode-390:amd64                 390.77-0ubuntu0~gpu18.04.1          amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-390:i386                  390.77-0ubuntu0~gpu18.04.1          i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-390:amd64                 390.77-0ubuntu0~gpu18.04.1          amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-390:i386                  390.77-0ubuntu0~gpu18.04.1          i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-390:amd64                   390.77-0ubuntu0~gpu18.04.1          amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-390:i386                    390.77-0ubuntu0~gpu18.04.1          i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-390:amd64                     390.77-0ubuntu0~gpu18.04.1          amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-390:i386                      390.77-0ubuntu0~gpu18.04.1          i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-390:amd64                   390.77-0ubuntu0~gpu18.04.1          amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-390:i386                    390.77-0ubuntu0~gpu18.04.1          i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-390                                 390.77-0ubuntu0~gpu18.04.1          amd64        Transitional package for nvidia-driver-390
ii  nvidia-compute-utils-390                   390.77-0ubuntu0~gpu18.04.1          amd64        NVIDIA compute utilities
ii  nvidia-dkms-390                            390.77-0ubuntu0~gpu18.04.1          amd64        NVIDIA DKMS package
ii  nvidia-driver-390                          390.77-0ubuntu0~gpu18.04.1          amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-390                   390.77-0ubuntu0~gpu18.04.1          amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-390                   390.77-0ubuntu0~gpu18.04.1          amd64        NVIDIA kernel source package
ii  nvidia-prime                               0.8.8                               all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                            396.54-0ubuntu0~gpu18.04.1          amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-390                           390.77-0ubuntu0~gpu18.04.1          amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-390              390.77-0ubuntu0~gpu18.04.1          amd64        NVIDIA binary Xorg driver
```
Display adapter info:


```
*-display                 
       description: 3D controller
       product: GP107M [GeForce GTX 1050 Ti Mobile]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:160 memory:ec000000-ecffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128) memory:ed000000-ed07ffff
```

Nvidia module info:


```
filename:       /lib/modules/4.18.3-041803-generic/updates/dkms/nvidia.ko
alias:          char-major-195-*
version:        390.77
supported:      external
license:        NVIDIA
srcversion:     209B1D0CB123DE466F700AD
alias:          pci:v000010DEd00000E00sv*sd*bc04sc80i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        ipmi_msghandler
retpoline:      Y
name:           nvidia
vermagic:       4.18.3-041803-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           NVreg_Mobile:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_UpdateMemoryTypes:int
parm:           NVreg_InitializeSystemMemoryAllocations:int
parm:           NVreg_UsePageAttributeTable:int
parm:           NVreg_MapRegistersEarly:int
parm:           NVreg_RegisterForACPIEvents:int
parm:           NVreg_CheckPCIConfigSpace:int
parm:           NVreg_EnablePCIeGen3:int
parm:           NVreg_EnableMSI:int
parm:           NVreg_TCEBypassMode:int
parm:           NVreg_UseThreadedInterrupts:int
parm:           NVreg_EnableStreamMemOPs:int
parm:           NVreg_EnableBacklightHandler:int
parm:           NVreg_EnableUserNUMAManagement:int
parm:           NVreg_EnableIBMNPURelaxedOrderingMode:int
parm:           NVreg_MemoryPoolSize:int
parm:           NVreg_IgnoreMMIOCheck:int
parm:           NVreg_RegistryDwords:charp
parm:           NVreg_RegistryDwordsPerDevice:charp
parm:           NVreg_RmMsg:charp
parm:           NVreg_AssignGpus:charp
```

After purgung all nvidia packages I get this from ```
cat /var/log/gpu-manager.log
```:

```
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.18.5-041805-generic/updates/dkms
Found nvidia module: nvidia-uvm.ko
Looking for amdgpu modules in /lib/modules/4.18.5-041805-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? yes
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 8086:3e9b
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1c8c
BusID "PCI:1@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver. Skipping...
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
output 0:
    card0-eDP-1
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? no
How many cards? 1
The number of cards has changed!
Has the system changed? Yes
System configuration has changed
Single card detected
Nothing to do

```

So I read this can happen because I didn's purge all Nvidia files off my pc.

Could someone help me remove every single Nvidia file off of my pc, or provide me with another way that I could use to fix this problem?

Thanks!

---


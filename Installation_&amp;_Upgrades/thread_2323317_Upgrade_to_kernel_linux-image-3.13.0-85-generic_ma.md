---
title: "Upgrade to kernel linux-image-3.13.0-85-generic makes screen wobble, damaging  video"
date: 2016-05-04
forum: Installation &amp; Upgrades
---

### Post by pilotopirx on 2016-05-04
After installing linux-image-3.13.0-85-generic, the images in the screen wobble. Upper left corner of the screen is fine, but the rest is a mess. I am running the older kernel, and the screen works fine. 

My graphic card is 

```
root@I39549:~# lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
```

I am runing ubuntu 14.04

The permanent solution can not be running and older kernel. What should be the issue?

---

### Post by RobGoss on 2016-05-04
> [h=2]linux-image-3.13.0-85-generic[/h]

Hello and welcome, Are you stating you installed a version of **Ubuntu?** because this does not really tell me which distribution you've installed

---

### Post by pilotopirx on 2016-07-01
I am runing Ubuntu 14.04 LTS

---

### Post by Bashing-om on 2016-07-01
pilotopirx; Hello;

Your thread has gotten stale now,
What kernel are you presently running ?
as what is now current:
> 
sysop@1404mini:~$ uname -r
3.13.0-91-generic
sysop@1404mini:~$ 

does the problem persist with the -91 version of the kernel ?

[INDENT][INDENT]maybe yes
[INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pilotopirx on 2016-11-30
I had to go back to :

3.13.0-79-generic

It is the only one that works. Even tried with 4. and would not.

---

### Post by ajgreeny on 2016-11-30
Why not try 3.13.0-101 which I think is the latest in the 3.13 series.

---

### Post by pilotopirx on 2016-11-30
I have also tried that one, and would not work. 

This is a video of the situation: 

[https://www.youtube.com/watch?v=k6vF7iRcg6w](https://www.youtube.com/watch?v=k6vF7iRcg6w)

I followed the troubleshooting procedure from here: [https://help.ubuntu.com/community/GraphicsTroubleshootingProcedure](https://help.ubuntu.com/community/GraphicsTroubleshootingProcedure)

The output is:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
01:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8670A/8670M/8750M] [1002:6600]
	Kernel driver in use: radeon
Linux I39549 3.13.0-101-generic #148-Ubuntu SMP Thu Oct 20 22:08:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

X.Org X Server 1.15.1
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
Current Operating System: Linux I39549 3.13.0-101-generic #148-Ubuntu SMP Thu Oct 20 22:08:32 UTC 2016 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-101-generic root=UUID=769b2ef2-08f8-4ea5-9848-1c970b3d62cd ro quiet splash vt.handoff=7
Build Date: 12 February 2015  02:49:29PM
xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.30.2
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[sudo] password for gavox: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) raring InRelease                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease                                 
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease [65,9 kB]             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://www.geogebra.net](http://www.geogebra.net) stable InRelease                                   
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                             
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security InRelease [65,9 kB]            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg             
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://www.geogebra.net](http://www.geogebra.net) stable/main amd64 Packages                         
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner amd64 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://www.geogebra.net](http://www.geogebra.net) stable/main i386 Packages                          
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Sources [7.522 B]    
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages               
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Sources [5.888 B]    
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages                
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Sources [387 kB]           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-es                            
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Sources [169 kB]       
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US            
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en               
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-es             
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main amd64 Packages [926 kB]    
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en                
Ign [http://www.geogebra.net](http://www.geogebra.net) stable/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-es
Ign [http://www.geogebra.net](http://www.geogebra.net) stable/main Translation-en  
Ign [http://www.geogebra.net](http://www.geogebra.net) stable/main Translation-es                 
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted amd64 Packages [16,4 kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe amd64 Packages [389 kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [14,0 kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [886 kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages [16,2 kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages [390 kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages [14,5 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en           
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Sources [3.207 B]  
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Sources [4.613 B]  
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Sources [123 kB]         
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Sources [45,8 kB]    
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main amd64 Packages [562 kB]  
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted amd64 Packages [13,3 kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe amd64 Packages [145 kB]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse amd64 Packages [4.138 B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main i386 Packages [521 kB]   
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted i386 Packages [13,1 kB]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe i386 Packages [145 kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse i386 Packages [4.289 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main amd64 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted amd64 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe amd64 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse amd64 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-es                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-es                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-es                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-es                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en_US                
Fetched 4.938 kB in 33s (148 kB/s)                                             
Reading package lists... Done
W: There is no public key available for the following key IDs:
1397BC53640DB551
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fbset is already the newest version.
hardinfo is already the newest version.
mesa-utils is already the newest version.
nux-tools is already the newest version.
The following package was automatically installed and is no longer required:
  thermald
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
```

```
mode "1920x1080"
    geometry 1920 1080 1920 1080 32
    timings 0 0 0 0 0 0 0
    accel true
    rgba 8/16,8/8,8/0,0/0
endmode

Frame buffer device information:
    Name        : inteldrmfb
    Address     : 0xd00a1000
    Size        : 8294400
    Type        : PACKED PIXELS
    Visual      : TRUECOLOR
    XPanStep    : 1
    YPanStep    : 1
    YWrapStep   : 0
    LineLength  : 7680
    Accelerator : No
Version: 1:7.7+1ubuntu8.1
Version: 1:7.7+1ubuntu8
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 32767 x 32767
eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080      60.2*+   59.9  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
display: :0  screen: 0
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Desktop 
OpenGL version string: 3.0 Mesa 10.1.3

The program 'nvidia-settings' is currently not installed. To run 'nvidia-settings' please ask your administrator to install the package 'nvidia-settings'
H/W path         Device      Class          Description
=======================================================
                             system         OptiPlex 9020 AIO (OptiPlex 9020 AIO
/0                           bus            0V8DVD
/0/0                         memory         64KiB BIOS
/0/45                        processor      Intel(R) Core(TM) i7-4770S CPU @ 3.1
/0/45/46                     memory         256KiB L1 cache
/0/45/47                     memory         1MiB L2 cache
/0/45/48                     memory         8MiB L3 cache
/0/49                        memory         8GiB System Memory
/0/49/0                      memory         4GiB SODIMM DDR3 Synchronous 1600 MH
/0/49/1                      memory         4GiB SODIMM DDR3 Synchronous 1600 MH
/0/100                       bridge         4th Gen Core Processor DRAM Controll
/0/100/1                     bridge         Xeon E3-1200 v3/4th Gen Core Process
/0/100/1/0                   display        Mars [Radeon HD 8670A/8670M/8750M]
/0/100/2                     display        Xeon E3-1200 v3/4th Gen Core Process
/0/100/3                     multimedia     Xeon E3-1200 v3/4th Gen Core Process
/0/100/14                    bus            8 Series/C220 Series Chipset Family 
/0/100/16                    communication  8 Series/C220 Series Chipset Family 
/0/100/19        eth0        network        Ethernet Connection I217-LM
/0/100/1a                    bus            8 Series/C220 Series Chipset Family 
/0/100/1b                    multimedia     8 Series/C220 Series Chipset High De
/0/100/1c                    bridge         8 Series/C220 Series Chipset Family 
/0/100/1c.6                  bridge         8 Series/C220 Series Chipset Family 
/0/100/1c.6/0                generic        RTS5209 PCI Express Card Reader
/0/100/1c.6/0.1              generic        RTS5209 PCI Express Card Reader
/0/100/1d                    bus            8 Series/C220 Series Chipset Family 
/0/100/1f                    bridge         Q87 Express LPC Controller
/0/100/1f.2                  storage        SATA Controller [RAID mode]
/0/100/1f.3                  bus            8 Series/C220 Series Chipset Family 
/0/1             scsi0       storage        
/0/1/0.0.0       /dev/sda    disk           500GB ST500DM002-1BD14
/0/1/0.0.0/1     /dev/sda1   volume         350MiB Windows NTFS volume
/0/1/0.0.0/2     /dev/sda2   volume         134GiB Windows NTFS volume
/0/1/0.0.0/3     /dev/sda3   volume         97GiB Windows NTFS volume
/0/1/0.0.0/4     /dev/sda4   volume         232GiB Extended partition
/0/1/0.0.0/4/5   /dev/sda5   volume         232GiB Linux filesystem partition
/0/2             scsi1       storage        
/0/2/0.0.0       /dev/cdrom  disk           DVD+-RW SN-208DN
  *-display               
       description: Display controller
       product: Mars [Radeon HD 8670A/8670M/8750M]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:53 memory:e0000000-efffffff memory:f7d00000-f7d3ffff ioport:e000(size=256) memory:f7d40000-f7d5ffff
  *-display
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:50 memory:f7800000-f7bfffff memory:d0000000-dfffffff ioport:f000(size=64)
ii  bbswitch-dkms                                         0.7-2ubuntu1                                        amd64        Interface for toggling the power on nVidia Optimus video cards
ii  fglrx                                                 2:15.201-0ubuntu0.14.04.1                           amd64        Video driver for the AMD graphics accelerators
ii  fglrx-amdcccle                                        2:15.201-0ubuntu0.14.04.1                           amd64        Catalyst Control Center for the AMD graphics accelerators
ii  fglrx-core                                            2:15.201-0ubuntu0.14.04.1                           amd64        Minimal video driver for the AMD graphics accelerators
ii  gir1.2-ibus-1.0                                       1.5.5-1ubuntu3.2                                    amd64        Intelligent Input Bus - introspection data
ii  ibus                                                  1.5.5-1ubuntu3.2                                    amd64        Intelligent Input Bus - core
ii  ibus-gtk:amd64                                        1.5.5-1ubuntu3.2                                    amd64        Intelligent Input Bus - GTK+2 support
ii  ibus-gtk3:amd64                                       1.5.5-1ubuntu3.2                                    amd64        Intelligent Input Bus - GTK+3 support
ii  intel-gpu-tools                                       1.3-0ubuntu2.1                                      amd64        tools for debugging the Intel graphics driver
ii  libcuda1-340                                          340.98-0ubuntu0.14.04.1                             amd64        NVIDIA CUDA runtime library
ii  libdrm-intel1:amd64                                   2.4.67-1ubuntu0.14.04.1                             amd64        Userspace interface to intel-specific kernel DRM services -- runtime
ii  libdrm-intel1:i386                                    2.4.67-1ubuntu0.14.04.1                             i386         Userspace interface to intel-specific kernel DRM services -- runtime
ii  libdrm-nouveau2:amd64                                 2.4.67-1ubuntu0.14.04.1                             amd64        Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-nouveau2:i386                                  2.4.67-1ubuntu0.14.04.1                             i386         Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-radeon1:amd64                                  2.4.67-1ubuntu0.14.04.1                             amd64        Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libdrm-radeon1:i386                                   2.4.67-1ubuntu0.14.04.1                             i386         Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libegl1-mesa:amd64                                    10.1.3-0ubuntu0.6                                   amd64        free implementation of the EGL API -- runtime
ii  libegl1-mesa-drivers:amd64                            10.1.3-0ubuntu0.6                                   amd64        free implementation of the EGL API -- hardware drivers
ii  libgl1-mesa-dev                                       10.1.3-0ubuntu0.6                                   amd64        free implementation of the OpenGL API -- GLX development files
ii  libgl1-mesa-dri:amd64                                 10.1.3-0ubuntu0.6                                   amd64        free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-dri:i386                                  10.1.3-0ubuntu0.6                                   i386         free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx:amd64                                 10.1.3-0ubuntu0.6                                   amd64        free implementation of the OpenGL API -- GLX runtime
ii  libgl1-mesa-glx:i386                                  10.1.3-0ubuntu0.6                                   i386         free implementation of the OpenGL API -- GLX runtime
ii  libglapi-mesa:amd64                                   10.1.3-0ubuntu0.6                                   amd64        free implementation of the GL API -- shared library
ii  libglapi-mesa:i386                                    10.1.3-0ubuntu0.6                                   i386         free implementation of the GL API -- shared library
ii  libgles2-mesa:amd64                                   10.1.3-0ubuntu0.6                                   amd64        free implementation of the OpenGL|ES 2.x API -- runtime
ii  libglu1-mesa:amd64                                    9.0.0-2                                             amd64        Mesa OpenGL utility library (GLU)
ii  libglu1-mesa-dev                                      9.0.0-2                                             amd64        Mesa OpenGL utility library -- development files
ii  libibus-1.0-0:amd64                                   1.4.2-0ubuntu2                                      amd64        Intelligent Input Bus - shared library
ii  libibus-1.0-5:amd64                                   1.5.5-1ubuntu3.2                                    amd64        Intelligent Input Bus - shared library
ii  libopenvg1-mesa:amd64                                 10.1.3-0ubuntu0.6                                   amd64        free implementation of the OpenVG API -- runtime
ii  libtxc-dxtn-s2tc0:amd64                               0~git20131104-1.1                                   amd64        Texture compression library for Mesa
ii  libtxc-dxtn-s2tc0:i386                                0~git20131104-1.1                                   i386         Texture compression library for Mesa
ii  libwayland-egl1-mesa:amd64                            10.1.3-0ubuntu0.6                                   amd64        implementation of the Wayland EGL platform -- runtime
ii  mesa-common-dev                                       10.1.3-0ubuntu0.6                                   amd64        Developer documentation for Mesa
ii  mesa-utils                                            8.1.0-2                                             amd64        Miscellaneous Mesa GL utilities
ii  nvidia-prime                                          0.6.2                                               amd64        Tools to enable NVIDIA's Prime
ii  python-ibus                                           1.5.5-1ubuntu3.2                                    all          Intelligent Input Bus - Python support
ii  radeontool                                            1.6.3-1                                             amd64        utility to control ATI Radeon backlight functions on laptops
ii  xserver-xorg-video-ati                                1:7.3.0-1ubuntu3.1                                  amd64        X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-intel                              2:2.99.910-0ubuntu1.6                               amd64        X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-nouveau                            1:1.0.10-1ubuntu2                                   amd64        X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-radeon                             1:7.3.0-1ubuntu3.1                                  amd64        X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-trident                            1:1.3.6-0ubuntu5                                    amd64        X.Org X server -- Trident display driver
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"
[    0.000000]   Intel GenuineIntel
[    0.000000] ACPI: ASF! 00000000c9ffd458 0000A5 (v32 INTEL       HCG 00000001 TFSM 000F4240)
[    0.000000] ACPI: DMAR 00000000c9ffd558 0000B8 (v01 INTEL      HSW  00000001 INTL 00000001)
[    0.058006] smpboot: CPU0: Intel(R) Core(TM) i7-4770S CPU @ 3.10GHz (fam: 06, model: 3c, stepping: 03)
[    0.058017] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.173677] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.190623] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.221993] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.329296] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.329298] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.329299] vgaarb: loaded
[    0.329300] vgaarb: bridge control possible 0000:00:02.0
[    0.585799] vesafb: mode is 1920x1080x32, linelength=7680, pages=0
[    0.585799] vesafb: scrolling: redraw
[    0.585800] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.586501] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90004e80000, using 8128k, total 8128k
[    0.592307] fb0: VESA VGA frame buffer device
[    0.592318] intel_idle: MWAIT substates: 0x42120
[    0.592318] intel_idle: v0.4 model 0x3C
[    0.592319] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.595103] ehci-pci 0000:00:1a.0: debug port 2
[    0.609019] ehci-pci 0000:00:1d.0: debug port 2
[    0.669227] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    0.669229] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[    0.847161] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    7.810113] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   12.250274] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   12.333802] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.679921] fbcon: inteldrmfb (fb0) is primary device
[   13.134092] [drm] radeon kernel modesetting enabled.
[   13.134100] VGA switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle
[   13.399112] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   13.399426] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   13.399926] ACPI Error: [\_SB_.PCI0.GFX0.DD02._BCL] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[   13.399929] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP.DD02._BCL] (Node ffff880222907190), AE_NOT_FOUND (20131115/psparse-536)
[   13.401030] vga_switcheroo: enabled
[   13.401043] snd_hda_intel 0000:00:03.0: irq 51 for MSI/MSI-X
[   13.432441] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input12
[   13.477719] snd_hda_intel 0000:00:1b.0: irq 52 for MSI/MSI-X
[   13.584401] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input15
[   13.584468] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card1/input14
[   13.584499] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input13
[   14.493609] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[   14.493611] radeon 0000:01:00.0: GTT: 1024M 0x0000000080000000 - 0x00000000BFFFFFFF
[   14.493753] [drm] radeon: 2048M of VRAM memory ready
[   14.493754] [drm] radeon: 1024M of GTT memory ready.
[   15.320938] [drm] radeon/OLAND_mc2.bin: 31452 bytes
[   15.453742] [drm] GART: num cpu pages 262144, num gpu pages 262144
[   15.456588] radeon 0000:01:00.0: WB enabled
[   15.456590] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff88021ff59c00
[   15.456591] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff88021ff59c04
[   15.456591] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff88021ff59c08
[   15.456592] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff88021ff59c0c
[   15.456593] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff88021ff59c10
[   15.457018] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90005335a18
[   15.457020] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[   15.457044] radeon 0000:01:00.0: irq 53 for MSI/MSI-X
[   15.457051] radeon 0000:01:00.0: radeon: using MSI.
[   15.457083] [drm] radeon: irq initialized.
[   15.936038] [drm] Radeon Display Connectors
[   16.197688] init: failsafe main process (726) killed by TERM signal
[   17.036425] [drm] radeon: dpm initialized
[   17.036483] radeon 0000:01:00.0: No connectors reported connected with modes
[   17.037454] radeon 0000:01:00.0: fb1: radeondrmfb frame buffer device
[   17.037461] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:00.0 on minor 1
[   19.238839] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   19.238842] Disabling lock debugging due to kernel taint
[   19.242119] fglrx: module verification failed: signature and/or  required key missing - tainting kernel
[   19.245188] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7662 MBytes.
[   19.245290] <6>[fglrx]   vendor: 1002 device: 6600 revision: 0 count: 1
[   19.245433] <6>[fglrx] ioport: bar 4, base 0xe000, size: 0x100
[   19.245502] <6>[fglrx] Kernel PAT support is enabled
[   19.245513] <6>[fglrx] module loaded - fglrx 15.20.3 [Sep  8 2015] with 1 minors
[   30.771055] radeon 0000:01:00.0: WB enabled
[   30.771056] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff88021ff59c00
[   30.771057] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff88021ff59c04
[   30.771058] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff88021ff59c08
[   30.771059] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff88021ff59c0c
[   30.771060] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff88021ff59c10
[   30.771458] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90005335a18
[   31.190539] [drm:r600_ring_test] *ERROR* radeon: ring 0 test failed (scratch(0x850C)=0xCAFEDEAD)
[   31.190542] [drm:si_resume] *ERROR* si startup failed on resume
model		: 60
model name	: Intel(R) Core(TM) i7-4770S CPU @ 3.10GHz
model		: 60
model name	: Intel(R) Core(TM) i7-4770S CPU @ 3.10GHz
model		: 60
model name	: Intel(R) Core(TM) i7-4770S CPU @ 3.10GHz
model		: 60
model name	: Intel(R) Core(TM) i7-4770S CPU @ 3.10GHz
model		: 60
model name	: Intel(R) Core(TM) i7-4770S CPU @ 3.10GHz
model		: 60
model name	: Intel(R) Core(TM) i7-4770S CPU @ 3.10GHz
model		: 60
model name	: Intel(R) Core(TM) i7-4770S CPU @ 3.10GHz
model		: 60
model name	: Intel(R) Core(TM) i7-4770S CPU @ 3.10GHz
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    33.404] (==) Automatically adding GPU devices
[    33.445] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    33.502] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    33.564] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    33.594] (II) LoadModule: "glx"
[    33.705] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    33.733] (II) Module glx: vendor="X.Org Foundation"
[    33.733] (==) AIGLX enabled
[    33.733] Loading extension GLX
[    33.733] (==) Matched intel as autoconfigured driver 0
[    33.733] (==) Matched fglrx as autoconfigured driver 1
[    33.733] (==) Matched intel as autoconfigured driver 3
[    33.733] (==) Matched vesa as autoconfigured driver 6
[    33.733] (II) LoadModule: "intel"
[    33.794] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    33.844] (II) Module intel: vendor="X.Org Foundation"
[    33.844] (II) LoadModule: "fglrx"
[    33.845] (WW) Warning, couldn't open module fglrx
[    33.845] (II) UnloadModule: "fglrx"
[    33.845] (II) Unloading fglrx
[    33.845] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    33.859] (II) LoadModule: "radeon"
[    33.859] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    33.936] (II) Module radeon: vendor="X.Org Foundation"
[    33.967] (II) LoadModule: "vesa"
[    33.967] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    33.968] (II) Module vesa: vendor="X.Org Foundation"
[    33.968] (==) Matched intel as autoconfigured driver 0
[    33.968] (==) Matched fglrx as autoconfigured driver 1
[    33.968] (==) Matched intel as autoconfigured driver 3
[    33.968] (==) Matched vesa as autoconfigured driver 6
[    33.968] (II) LoadModule: "intel"
[    33.968] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    33.968] (II) Module intel: vendor="X.Org Foundation"
[    33.968] (II) UnloadModule: "intel"
[    33.968] (II) Unloading intel
[    33.968] (II) Failed to load module "intel" (already loaded, 32615)
[    33.968] (II) LoadModule: "fglrx"
[    33.968] (WW) Warning, couldn't open module fglrx
[    33.968] (II) UnloadModule: "fglrx"
[    33.968] (II) Unloading fglrx
[    33.968] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    33.968] (II) Failed to load module "modesetting" (already loaded, 0)
[    33.968] (II) Failed to load module "fbdev" (already loaded, 0)
[    33.968] (II) LoadModule: "vesa"
[    33.968] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    33.968] (II) Module vesa: vendor="X.Org Foundation"
[    33.968] (II) UnloadModule: "vesa"
[    33.968] (II) Unloading vesa
[    33.968] (II) Failed to load module "vesa" (already loaded, 0)
[    33.968] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
[    33.969] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    33.969] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    33.969] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    33.969] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
	ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
	ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
[    33.972] (II) VESA: driver for VESA chipsets: vesa
[    33.985] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1.6 (Timo Aaltonen <tjaalton@debian.org>)
[    34.003] (WW) Falling back to old probe method for modesetting
[    34.003] (WW) Falling back to old probe method for fbdev
[    34.014] (WW) Falling back to old probe method for vesa
[    34.015] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    34.015] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[    34.015] (II) intel(0): Creating default Display subsection in Screen section
[    34.015] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    34.015] (==) intel(0): RGB weight 888
[    34.015] (==) intel(0): Default visual is TrueColor
[    34.015] (**) intel(0): Framebuffer tiled
[    34.015] (**) intel(0): Pixmaps tiled
[    34.015] (**) intel(0): "Tear free" disabled
[    34.015] (**) intel(0): Forcing per-crtc-pixmaps? no
[    34.015] (II) intel(0): Output eDP1 has no monitor section
[    34.015] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')
[    34.015] (II) intel(0): Output VGA1 has no monitor section
[    34.015] (II) intel(0): Output HDMI1 has no monitor section
[    34.015] (II) intel(0): Output VIRTUAL1 has no monitor section
[    34.015] (--) intel(0): Output eDP1 using initial mode 1920x1080 on pipe 0
[    34.015] (==) intel(0): DPI set to (96, 96)
[    34.016] (==) RADEON(G0): Depth 24, (--) framebuffer bpp 32
[    34.016] (II) RADEON(G0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    34.016] (==) RADEON(G0): Default visual is TrueColor
[    34.016] (==) RADEON(G0): RGB weight 888
[    34.016] (II) RADEON(G0): Using 8 bits per RGB (8 bit DAC)
[    34.016] (--) RADEON(G0): Chipset: "OLAND" (ChipID = 0x6600)
[    34.016] (II) RADEON(G0): GPU accel disabled or not working, using shadowfb for KMS
[    34.018] (II) RADEON(G0): KMS Color Tiling: disabled
[    34.018] (II) RADEON(G0): KMS Color Tiling 2D: disabled
[    34.018] (II) RADEON(G0): KMS Pageflipping: enabled
[    34.018] (II) RADEON(G0): SwapBuffers wait for vsync: enabled
[    34.018] (II) RADEON(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    34.018] (II) RADEON(G0): mem size init: gart size :3fbde000 vram size: s:80000000 visible:fcc0000
[    34.018] (II) RADEON(G0): EXA: Driver will allow EXA pixmaps in VRAM
[    34.018] (==) RADEON(G0): DPI set to (96, 96)
[    34.040] (II) UnloadModule: "vesa"
[    34.040] (II) Unloading vesa
[    34.041] (II) RADEON(G0): Front buffer size: 3072K
[    34.041] (II) RADEON(G0): VRAM usage limit set to 230140K
[    34.050] (==) RADEON(G0): Backing store enabled
[    34.050] (WW) RADEON(G0): Direct rendering disabled
[    34.050] (II) RADEON(G0): Acceleration disabled
[    34.050] (==) RADEON(G0): DPMS enabled
[    34.050] (==) RADEON(G0): Silken mouse enabled
[    34.050] (II) RADEON(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    34.075] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[    34.075] (==) intel(0): Backing store enabled
[    34.075] (==) intel(0): Silken mouse enabled
[    34.075] (II) intel(0): HW Cursor enabled
[    34.075] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    34.075] (==) intel(0): DPMS enabled
[    34.075] (II) intel(0): [DRI2] Setup complete
[    34.075] (II) intel(0): [DRI2]   DRI driver: i965
[    34.075] (II) intel(0): [DRI2]   VDPAU driver: i965
[    34.075] (II) intel(0): direct rendering: DRI2 Enabled
[    34.075] (==) intel(0): hotplug detection: "enabled"
[    34.226] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    34.226] (II) AIGLX: enabled GLX_ARB_create_context
[    34.226] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    34.226] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    34.226] (II) AIGLX: enabled GLX_INTEL_swap_event
[    34.226] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    34.226] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    34.226] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    34.226] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    34.226] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    34.226] (II) AIGLX: Loaded and initialized i965
[    34.226] (II) GLX: Initialized DRI2 GL provider for screen 0
[    34.241] (II) intel(0): switch to mode 1920x1080@60.2 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    34.260] (II) intel(0): Setting screen physical size to 508 x 285
[    34.469] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event8)
[    34.470] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event11)
[    34.470] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event10)
[    34.470] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event9)
[    45.211] (II) intel(0): EDID vendor "DEL", prod id 37847
[    45.211] (II) intel(0): DDCModeFromDetailedTiming: 1920x1080 Warning: We only handle separate sync.
[    45.211] (II) intel(0): Printing DDC gathered Modelines:
[    45.211] (II) intel(0): Modeline "1920x1080"x0.0  144.00  1920 2016 2080 2176  1080 1088 1092 1100 -hsync -vsync (66.2 kHz eP)
	Release Date: 08/13/2013
		Serial services are supported (int 14h)
	Manufacturer: Dell Inc.
	Product Name: OptiPlex 9020 AIO
	Serial Number: HVHW8Z1
	Manufacturer: Dell Inc.
	Product Name: 0V8DVD
	Serial Number: /HVHW8Z1/CN7443138V001L/
	Manufacturer: Dell Inc.
	Serial Number: HVHW8Z1
	Manufacturer: Intel
	Serial Number: Not Specified
	Manufacturer: Samsung
	Serial Number: E40BB836
	Manufacturer: Samsung
	Serial Number: 690BB836
cat: /etc/X11/xorg.conf: No such file or directory
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Desktop 
OpenGL version string:  3.0 Mesa 10.1.3

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
Support status summary of 'I39549':

You have 88 packages (2.6%) supported until mayo 2017 (3y)
You have 2425 packages (71.5%) supported until mayo 2019 (5y)
You have 36 packages (1.1%) supported until agosto 2017 (9m)

You have 107 packages (3.2%) that can not/no-longer be downloaded
You have 734 packages (21.7%) that are unsupported

Your Hardware Enablement Stack (HWE) is supported until abril 2019.

Run with --show-unsupported, --show-supported or --show-all to see more details
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               409768  3 vboxnetadp,vboxnetflt,vboxpci
fglrx               13510274  0 
amd_iommu_v2           19054  1 fglrx
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391136  10 bnep,rfcomm
uvcvideo               80885  0 
snd_hda_codec_realtek    65904  1 
snd_hda_codec_hdmi     46368  1 
videobuf2_vmalloc      13216  1 uvcvideo
radeon               1522941  1 
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_hda_intel          56611  5 
videobuf2_core         40664  1 uvcvideo
snd_hda_codec         193017  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
videodev              134688  2 uvcvideo,videobuf2_core
joydev                 17381  0 
snd_hwdep              13602  1 snd_hda_codec
hid_multitouch         17407  0 
dell_wmi_aio           12652  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
sparse_keymap          13948  1 dell_wmi_aio
i915                  788212  5 
dcdbas                 14928  0 
ttm                    93424  1 radeon
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
drm_kms_helper         55071  2 i915,radeon
drm                   303102  7 ttm,i915,drm_kms_helper,radeon
snd_seq_midi           13324  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30731  1 snd_seq_midi
wmi                    19177  1 dell_wmi_aio
kvm_intel             143187  0 
snd_seq                61616  2 snd_seq_midi_event,snd_seq_midi
i2c_algo_bit           13413  2 i915,radeon
mei_me                 18627  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29549  2 snd_pcm,snd_seq
mei                    82276  1 mei_me
kvm                   455843  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
rtsx_pci_ms            18151  0 
memstick               16966  1 rtsx_pci_ms
lpc_ich                21080  0 
snd                    69416  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
aesni_intel            55624  0 
mac_hid                13205  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
shpchp                 37032  0 
ablk_helper            13597  1 aesni_intel
cryptd                 20359  2 aesni_intel,ablk_helper
video                  19476  1 i915
serio_raw              13462  0 
binfmt_misc            17468  1 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  3 hid_multitouch,hid_generic,usbhid
rtsx_pci_sdmmc         23274  0 
e1000e                254433  0 
ahci                   34091  2 
psmouse               106692  0 
sdhci_pci              23172  0 
ptp                    18933  1 e1000e
libahci                32716  1 ahci
rtsx_pci               46245  2 rtsx_pci_ms,rtsx_pci_sdmmc
sdhci                  43023  1 sdhci_pci
pps_core               19382  1 ptp
```

---

### Post by pilotopirx on 2016-12-02
Bump!

---


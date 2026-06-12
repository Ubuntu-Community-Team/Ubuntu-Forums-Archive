---
title: "Unable to use my NVIDIA GeForce GTX 960M GPU"
date: 2019-08-20
forum: Installation &amp; Upgrades
---

### Post by jdosio on 2019-08-20
Hello everyone i made a [post]("https://ubuntuforums.org/showthread.php?t=2423346") about this issue a while earlier and was unable to resolve it; hopefully someone with the same issue sees this post.

i am sure the gpu is being detected because if i try,
```

jdosio@2io-01:~$ lspci | grep -i --color 'vga\|3d\|2d'
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 530 (rev 06)
02:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 960M] (rev a2)
jdosio@2io-01:~$ sudo lspci -v -s 02:00.0
02:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 960M] (rev a2)
    Subsystem: Dell GM107M [GeForce GTX 960M]
    Flags: bus master, fast devsel, latency 0, IRQ 255
    Memory at de000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [disabled] [size=128]
    Expansion ROM at df000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [250] Latency Tolerance Reporting
    Capabilities: [258] L1 PM Substates
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Capabilities: [900] #19
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia




```

i have noticed that the gpu has been regarded as unclaimed and am not sure how to "claim" it, i found this term used here,
```

root@2io-01:/home/jdosio# lshw -class display
  *-display UNCLAIMED       
       description: 3D controller
       product: GM107M [GeForce GTX 960M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:df000000-df07ffff
  *-display
       description: VGA compatible controller
       product: HD Graphics 530
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:129 memory:dd000000-ddffffff memory:b0000000-bfffffff ioport:f000(size=64) memory:c0000-dffff

```

Has anyone ran into a similar problem installing their NVIDIA Cards?

---

### Post by Bashing-om on 2019-08-20
jdosio; Hello -

What is the method you are doing to install the Nvidia driver ?

Left overs ?
```

dpkg -l | grep -i nvidia

```

Modules available ?
```

lsmod | grep nvidia

```

What does the GPU manager have to relate ?
```

cat /var/log/gpu-manager.log

```

And we go on the hunt

[INDENT][INDENT]gots to be a reason
[/INDENT][/INDENT]

---

### Post by jdosio on 2019-08-21
Well i have tried vary many methods and infact found out how unhealthy that can be for my computer(hehe), but have since deleted old versions of the installation, the last method i used to intall was through the ppa repository i believe!
```

jdosio@2io-01:~$ dpkg -l | grep -i nvidia
ii  libnvidia-cfg1-430:amd64                   430.40-0ubuntu0~gpu18.04.1                   amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-430                       430.40-0ubuntu0~gpu18.04.1                   all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-390:amd64                390.116-0ubuntu0.18.04.1                     amd64        NVIDIA libcompute package
rc  libnvidia-compute-390:i386                 390.116-0ubuntu0.18.04.1                     i386         NVIDIA libcompute package
ii  libnvidia-compute-430:amd64                430.40-0ubuntu0~gpu18.04.1                   amd64        NVIDIA libcompute package
ii  libnvidia-compute-430:i386                 430.40-0ubuntu0~gpu18.04.1                   i386         NVIDIA libcompute package
ii  libnvidia-decode-430:amd64                 430.40-0ubuntu0~gpu18.04.1                   amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-430:i386                  430.40-0ubuntu0~gpu18.04.1                   i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-430:amd64                 430.40-0ubuntu0~gpu18.04.1                   amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-430:i386                  430.40-0ubuntu0~gpu18.04.1                   i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-430:amd64                   430.40-0ubuntu0~gpu18.04.1                   amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-430:i386                    430.40-0ubuntu0~gpu18.04.1                   i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-430:amd64                     430.40-0ubuntu0~gpu18.04.1                   amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-430:i386                      430.40-0ubuntu0~gpu18.04.1                   i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-430:amd64                   430.40-0ubuntu0~gpu18.04.1                   amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-430:i386                    430.40-0ubuntu0~gpu18.04.1                   i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-430                   430.40-0ubuntu0~gpu18.04.1                   amd64        NVIDIA compute utilities
ii  nvidia-dkms-430                            430.40-0ubuntu0~gpu18.04.1                   amd64        NVIDIA DKMS package
ii  nvidia-driver-430                          430.40-0ubuntu0~gpu18.04.1                   amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-430                   430.40-0ubuntu0~gpu18.04.1                   amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-430                   430.40-0ubuntu0~gpu18.04.1                   amd64        NVIDIA kernel source package
ii  nvidia-prime                               0.8.8.2                                      all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                            418.56-0ubuntu0~gpu18.04.1                   amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-430                           430.40-0ubuntu0~gpu18.04.1                   amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-430              430.40-0ubuntu0~gpu18.04.1                   amd64        NVIDIA binary Xorg driver

```
```

jdosio@2io-01:~$ lsmod | grep nvidia
jdosio@2io-01:~$ 

```

^^none

```

jdosio@2io-01:~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/5.0.0-25-generic/updates/dkms
Found nvidia module: nvidia-drm.ko
Looking for amdgpu modules in /lib/modules/5.0.0-25-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
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
Vendor/Device Id: 8086:191b
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:139b
BusID "PCI:2@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:02:00.0/driver
The device is not bound to any driver.
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
output 0:
    card0-HDMI-A-1
output 1:
    card0-eDP-1
Number of connected outputs for /dev/dri/card0: 2
Does it require offloading? yes
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
Intel IGP detected
Intel hybrid system
Creating /usr/share/X11/xorg.conf.d/11-nvidia-prime.conf
Setting power control to "on" in /sys/bus/pci/devices/0000:02:00.0/power/control
Loading nvidia with "no" parameters

```
Thank you for the help, rather new at the hunt.


And yes im sure there gots to be a reason.:p

---

### Post by Bashing-om on 2019-08-21
jdosio; Ouch ...

We have from the log:
> 
can't access /run/u-d-c-nvidia-was-loaded file
Is nvidia loaded? no
Error: can't access /sys/bus/pci/devices/0000:02:00.0/driver


the lsmod output confirms that the driver did not build and 
[https://www.nvidia.com/Download/driverResults.aspx/149138/en-us](https://www.nvidia.com/Download/driverResults.aspx/149138/en-us)
confirms that the 430 version driver is proper..

So, where is that failure that the driver does not build ?

Let's poke about a bit - post back:
```

ls -al /usr/share/X11/xorg.conf.d
ls -al /etc/X11/xorg.conf
cat /var/log/Xorg.0.log

```

Let us keep in mind that fast boot and secure boot in the firmware could be at play here.

When we know more
[INDENT][INDENT]we do more
[/INDENT][/INDENT]

---

### Post by jdosio on 2019-08-22
Here are the results!
```

jdosio@2io-01:~$ ls -al /usr/share/X11/xorg.conf.d
total 36
drwxr-xr-x 2 root root 4096 Aug 22 00:30 .
drwxr-xr-x 5 root root 4096 May 29 15:37 ..
-rw-r--r-- 1 root root   92 May 29 06:19 10-amdgpu.conf
-rw-r--r-- 1 root root  210 Jul 31 02:15 10-nvidia.conf
-rw-r--r-- 1 root root 1350 May  2 04:06 10-quirks.conf
-rw-r--r-- 1 root root   92 May 29 06:19 10-radeon.conf
-rw-r--r-- 1 root root  945 Nov 27  2018 40-libinput.conf
-rw-r--r-- 1 root root 3025 Nov 27  2018 70-wacom.conf
-r--r--r-- 1 root root  489 Jul  7 05:20 nvidia-drm-outputclass.conf



```
xorg.conf was not found however,
```

jdosio@2io-01:~$ ls -al /etc/X11/
total 100
drwxr-xr-x  11 root root  4096 Jul  7 13:27 .
drwxr-xr-x 149 root root 12288 Aug 22 00:28 ..
drwxr-xr-x   2 root root  4096 Jun  1 04:02 app-defaults
drwxr-xr-x   2 root root  4096 Feb  9  2019 cursors
-rw-r--r--   1 root root    15 Jul  7 13:27 default-display-manager
-rw-r--r--   1 root root    15 Jul  7 13:20 default-display-manager.dpkg-tmp
drwxr-xr-x   4 root root  4096 Feb  9  2019 fonts
-rw-r--r--   1 root root 17394 Jan 20  2017 rgb.txt
drwxr-xr-x   2 root root  4096 May 29 15:43 xinit
drwxr-xr-x   2 root root  4096 Feb  2  2018 xkb
-rwxr-xr-x   1 root root   709 Jan 20  2017 Xreset
drwxr-xr-x   2 root root  4096 Feb  9  2019 Xreset.d
drwxr-xr-x   2 root root  4096 Feb  9  2019 Xresources
-rwxr-xr-x   1 root root  3730 May  3  2017 Xsession
drwxr-xr-x   2 root root  4096 Jul  5 12:46 Xsession.d
-rw-r--r--   1 root root   265 Jan 20  2017 Xsession.options
drwxr-xr-x   2 root root  4096 Feb  9  2019 xsm
-rw-r--r--   1 root root    13 Dec  5  2016 XvMCConfig
-rw-r--r--   1 root root   630 Feb  9  2019 Xwrapper.config

```
and the last command had too long of an output so i had to make a link for it here it is below,
[https://paste.ubuntu.com/p/8m8VV8K5sT/plain/](https://paste.ubuntu.com/p/8m8VV8K5sT/plain/)

I wish i knew how this stuff was useful to you lol.

---

### Post by Bashing-om on 2019-08-22
jdosio; Well -
> 
I wish i know how this stuff was useful to you lol.


we are looking to see if we can learn why the Nvidia driver did not build.

The Xorg file relates:
```

3377.672] (==) ModulePath set to "/usr/lib/xorg/modules"
3377.692] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
3377.693] (==) Matched modesetting as autoconfigured driver 0
3377.693] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so

```
Huh ?? why is not Nvidia loaded !

Is the driver available per the path ? show:
```

ls -al /usr/lib/xorg/modules/drivers
sudo find / -name "NVIDIA-Linux-*"

```

As I do consider to clean everything out and try to re-install the driver one more time. See here if the system reports any issues at that point.

[INDENT][INDENT]clean is good
[/INDENT][/INDENT]

---

### Post by jdosio on 2019-08-23
```

jdosio@2io-01:~$ ls -al /usr/lib/xorg/modules/drivers
total 9324
drwxr-xr-x 2 root root    4096 Jul  7 05:20 .
drwxr-xr-x 5 root root    4096 Jul  7 05:20 ..
-rw-r--r-- 1 root root  160896 May 29 06:19 amdgpu_drv.so
-rw-r--r-- 1 root root   10408 May 29 06:19 ati_drv.so
-rw-r--r-- 1 root root   23552 Nov 27  2018 fbdev_drv.so
-rw-r--r-- 1 root root 1677832 Feb  1  2019 intel_drv.so
-rw-r--r-- 1 root root  107072 May  2 04:06 modesetting_drv.so
-rw-r--r-- 1 root root  217224 May 29 06:19 nouveau_drv.so
-rwxr-xr-x 1 root root 6434624 Jul  7 05:20 nvidia_drv.so
-rw-r--r-- 1 root root  180840 Nov 27  2018 qxl_drv.so
-rw-r--r-- 1 root root  506176 May 29 06:19 radeon_drv.so
-rw-r--r-- 1 root root   27688 Nov 27  2018 vesa_drv.so
-rw-r--r-- 1 root root  170296 Nov 27  2018 vmware_drv.so
jdosio@2io-01:~$ sudo find / -name "NVIDIA-Linux-*"
[sudo] password for jdosio: 
find: &#8216;/run/user/1000/doc&#8217;: Permission denied
find: &#8216;/run/user/1000/gvfs&#8217;: Permission denied
/home/jdosio/.local/share/Trash/info/NVIDIA-Linux-x86_64-430.14 (1).run.trashinfo
/home/jdosio/.local/share/Trash/info/NVIDIA-Linux-x86_64-430.14.run.trashinfo
/home/jdosio/.local/share/Trash/files/NVIDIA-Linux-x86_64-430.14 (1).run
/home/jdosio/.local/share/Trash/files/NVIDIA-Linux-x86_64-430.14.run
/home/jdosio/Downloads/apps/NVIDIA-Linux-x86_64-430.26.run
find: &#8216;/proc/15030/task/15030/net&#8217;: Invalid argument
find: &#8216;/proc/15030/net&#8217;: Invalid argument

```
since it said permission denied i tried it in root but had the same result,
```

jdosio@2io-01:~$ su
Password: 
root@2io-01:/home/jdosio# find / -name "NVIDIA-Linux-*"
find: &#8216;/run/user/1000/doc&#8217;: Permission denied
find: &#8216;/run/user/1000/gvfs&#8217;: Permission denied
/home/jdosio/.local/share/Trash/info/NVIDIA-Linux-x86_64-430.14 (1).run.trashinfo
/home/jdosio/.local/share/Trash/info/NVIDIA-Linux-x86_64-430.14.run.trashinfo
/home/jdosio/.local/share/Trash/files/NVIDIA-Linux-x86_64-430.14 (1).run
/home/jdosio/.local/share/Trash/files/NVIDIA-Linux-x86_64-430.14.run
/home/jdosio/Downloads/apps/NVIDIA-Linux-x86_64-430.26.run
find: &#8216;/proc/15030/task/15030/net&#8217;: Invalid argument
find: &#8216;/proc/15030/net&#8217;: Invalid argument
find: &#8216;/proc/24048/task/24048/net&#8217;: Invalid argument
find: &#8216;/proc/24048/net&#8217;: Invalid argument
find: &#8216;/proc/24342/task/24342/net&#8217;: Invalid argument
find: &#8216;/proc/24342/net&#8217;: Invalid argument
find: &#8216;/proc/26408/task/26408/net&#8217;: Invalid argument
find: &#8216;/proc/26408/net&#8217;: Invalid argument
find: &#8216;/proc/27809/task/27809/net&#8217;: Invalid argument
find: &#8216;/proc/27809/net&#8217;: Invalid argument
find: &#8216;/proc/28222/task/28222/net&#8217;: Invalid argument
find: &#8216;/proc/28222/net&#8217;: Invalid argument



```


i also know,
```

jdosio@2io-01:~$ sudo locate "NVIDIA"
[sudo] password for jdosio: 
/home/jdosio/.local/share/Trash/files/NVIDIA-Linux-x86_64-430.14 (1).run
/home/jdosio/.local/share/Trash/files/NVIDIA-Linux-x86_64-430.14.run
/home/jdosio/.local/share/Trash/info/NVIDIA-Linux-x86_64-430.14 (1).run.trashinfo
/home/jdosio/.local/share/Trash/info/NVIDIA-Linux-x86_64-430.14.run.trashinfo
/home/jdosio/Downloads/apps/NVIDIA-Linux-x86_64-430.26.run
/usr/share/cmake-3.10/Modules/Compiler/NVIDIA-CUDA.cmake
/usr/share/cmake-3.10/Modules/Compiler/NVIDIA-DetermineCompiler.cmake
/usr/share/cmake-3.10/Modules/Platform/Darwin-NVIDIA-CUDA.cmake
/usr/share/cmake-3.10/Modules/Platform/Windows-NVIDIA-CUDA.cmake
/usr/share/doc/NVIDIA_GLX-1.0
/usr/share/doc/NVIDIA_GLX-1.0/LICENSE
/usr/share/doc/NVIDIA_GLX-1.0/NVIDIA_Changelog
/usr/share/doc/NVIDIA_GLX-1.0/README.txt
/usr/share/doc/NVIDIA_GLX-1.0/html
/usr/share/doc/NVIDIA_GLX-1.0/nvidia-settings.png
/usr/share/doc/NVIDIA_GLX-1.0/samples
/usr/share/doc/NVIDIA_GLX-1.0/html/acknowledgements.html
/usr/share/doc/NVIDIA_GLX-1.0/html/addressingcapabilities.html
/usr/share/doc/NVIDIA_GLX-1.0/html/addtlresources.html
/usr/share/doc/NVIDIA_GLX-1.0/html/appendices.html
/usr/share/doc/NVIDIA_GLX-1.0/html/audiosupport.html
/usr/share/doc/NVIDIA_GLX-1.0/html/commonproblems.html
/usr/share/doc/NVIDIA_GLX-1.0/html/configlaptop.html
/usr/share/doc/NVIDIA_GLX-1.0/html/configmultxscreens.html
/usr/share/doc/NVIDIA_GLX-1.0/html/configtwinview.html
/usr/share/doc/NVIDIA_GLX-1.0/html/depth30.html
/usr/share/doc/NVIDIA_GLX-1.0/html/displaydevicenames.html
/usr/share/doc/NVIDIA_GLX-1.0/html/dma_issues.html
/usr/share/doc/NVIDIA_GLX-1.0/html/dpi.html
/usr/share/doc/NVIDIA_GLX-1.0/html/editxconfig.html
/usr/share/doc/NVIDIA_GLX-1.0/html/egpu.html
/usr/share/doc/NVIDIA_GLX-1.0/html/faq.html
/usr/share/doc/NVIDIA_GLX-1.0/html/flippingubb.html
/usr/share/doc/NVIDIA_GLX-1.0/html/framelock.html
/usr/share/doc/NVIDIA_GLX-1.0/html/glxsupport.html
/usr/share/doc/NVIDIA_GLX-1.0/html/gpunames.html
/usr/share/doc/NVIDIA_GLX-1.0/html/i2c.html
/usr/share/doc/NVIDIA_GLX-1.0/html/index.html
/usr/share/doc/NVIDIA_GLX-1.0/html/installationandconfiguration.html
/usr/share/doc/NVIDIA_GLX-1.0/html/installdriver.html
/usr/share/doc/NVIDIA_GLX-1.0/html/installedcomponents.html
/usr/share/doc/NVIDIA_GLX-1.0/html/introduction.html
/usr/share/doc/NVIDIA_GLX-1.0/html/kms.html
/usr/share/doc/NVIDIA_GLX-1.0/html/knownissues.html
/usr/share/doc/NVIDIA_GLX-1.0/html/minimumrequirements.html
/usr/share/doc/NVIDIA_GLX-1.0/html/newusertips.html
/usr/share/doc/NVIDIA_GLX-1.0/html/nvidia-debugdump.html
/usr/share/doc/NVIDIA_GLX-1.0/html/nvidia-ml.html
/usr/share/doc/NVIDIA_GLX-1.0/html/nvidia-persistenced.html
/usr/share/doc/NVIDIA_GLX-1.0/html/nvidia-smi.html
/usr/share/doc/NVIDIA_GLX-1.0/html/nvidiasettings.html
/usr/share/doc/NVIDIA_GLX-1.0/html/openglenvvariables.html
/usr/share/doc/NVIDIA_GLX-1.0/html/optimus.html
/usr/share/doc/NVIDIA_GLX-1.0/html/powermanagement.html
/usr/share/doc/NVIDIA_GLX-1.0/html/procinterface.html
/usr/share/doc/NVIDIA_GLX-1.0/html/profiles.html
/usr/share/doc/NVIDIA_GLX-1.0/html/programmingmodes.html
/usr/share/doc/NVIDIA_GLX-1.0/html/randr14.html
/usr/share/doc/NVIDIA_GLX-1.0/html/retpoline.html
/usr/share/doc/NVIDIA_GLX-1.0/html/sdi.html
/usr/share/doc/NVIDIA_GLX-1.0/html/selectdriver.html
/usr/share/doc/NVIDIA_GLX-1.0/html/sli.html
/usr/share/doc/NVIDIA_GLX-1.0/html/supportedchips.html
/usr/share/doc/NVIDIA_GLX-1.0/html/vdpausupport.html
/usr/share/doc/NVIDIA_GLX-1.0/html/xcompositeextension.html
/usr/share/doc/NVIDIA_GLX-1.0/html/xconfigoptions.html
/usr/share/doc/NVIDIA_GLX-1.0/html/xineramaglx.html
/usr/share/doc/NVIDIA_GLX-1.0/html/xrandrextension.html
/usr/share/doc/NVIDIA_GLX-1.0/samples/nvidia-persistenced-init.tar.bz2
/usr/share/doc/NVIDIA_GLX-1.0/samples/systemd
/usr/share/doc/NVIDIA_GLX-1.0/samples/systemd/nvidia
/usr/share/doc/NVIDIA_GLX-1.0/samples/systemd/nvidia-hibernate.service
/usr/share/doc/NVIDIA_GLX-1.0/samples/systemd/nvidia-resume.service
/usr/share/doc/NVIDIA_GLX-1.0/samples/systemd/nvidia-sleep.sh
/usr/share/doc/NVIDIA_GLX-1.0/samples/systemd/nvidia-suspend.service
/usr/share/doc/nvidia-driver-430/NVIDIA_Changelog.gz



```

---

### Post by Bashing-om on 2019-08-23
jdosio; Oh Boy !

OK .. OEM install - even Nvidia says do not do that:
> 
Note that many Linux distributions provide their own packages of the NVIDIA Linux Graphics Driver in the distribution's native package management format. This may interact better with the rest of your distribution's framework, and you may want to use this rather than NVIDIA's official package.

[https://www.nvidia.com/Download/driverResults.aspx/149138/en-us](https://www.nvidia.com/Download/driverResults.aspx/149138/en-us)

So now we need to figure out how to UN-install the OEM attempt to install.

The command is:
```

sudo ./NVIDIA-Linux-x86_64-430.14.run --uninstall

```
where the command is to be ran from within the same directory (explicit path ./) as the OEM installer. As presently in the Trash I do not know how it would run there. Maybe move it back out of Trash ? If moved to the /home directory, then do not use sudo to run that command !

[INDENT]maybe now we move forward
[/INDENT]

---

### Post by jdosio on 2019-08-23
well i tried  moving the .run file from /trash to /Desktop and running the command but it was not recognized i am reading up on how to uninstall now,
```

jdosio@2io-01:~$  cd /home/jdosio/Desktop/
jdosio@2io-01:~/Desktop$ NVIDIA-Linux-x86_64-430.14.run --uninstall
NVIDIA-Linux-x86_64-430.14.run: command not found

```

---

### Post by Bashing-om on 2019-08-23
jdosio; Well ..

as the file is now sitting in your Desktop directory -
cd to that directory and tell the nvidia installer to look in that there directory  (./).
run here:
```

sudo ./NVIDIA-Linux-x86_64-430.14.run --uninstall

```

computers,
[INDENT]they are so literal[/INDENT]

---

### Post by jdosio on 2019-08-24
```

jdosio@2io-01:~/Desktop$ sudo ./NVIDIA-Linux-x86_64-430.14.run --uninstall
sudo: ./NVIDIA-Linux-x86_64-430.14.run: command not found



```

no luck.
        you're quite humorous tho :P

---

### Post by Bashing-om on 2019-08-24
jdosio; Hummm 

Does not compute ..

As the find command yields " NVIDIA-Linux-x86_64-430.14.run" That is/was in your Trash.

Copied to your Desktop directory then I do expect to see it there.

When the Desktop is the present working directory (jdosio@2io-01:~/Desktop$ )
what shows:
```

ls -al

```

And again be aware that using elevated authority within any directory in your /home can lead to undesired side effects .. don't - just don't - unless there is a expressed need for that level of escalation.

[INDENT]are we there yet ?
[/INDENT]

---

### Post by jdosio on 2019-08-25
yep pretty sure it is there, checked right after i moved it there.but perhaps i did something wrong?
```

jdosio@2io-01:~$ cd /home/jdosio/Desktop/
jdosio@2io-01:~/Desktop$ ls -al
total 34941200
drwxr-xr-x  7 jdosio jdosio        4096 Aug 23 20:17  .
drwxr-xr-x 40 jdosio jdosio        4096 Aug 23 13:07  ..
-rwxrwxrwx  1 jdosio jdosio 35668512186 May 19 20:40  Academic.rar
-rw-rw-r--  1 jdosio jdosio       15660 Aug 11 23:11  agr.docx
-rw-rw-r--  1 jdosio jdosio        1034 Aug 19 09:28  AUG19.log
-rw-rw-r--  1 jdosio jdosio        6359 Aug 19 09:29  AUG19.tex
drwxrwxr-x  6 jdosio jdosio        4096 Jun  9 18:19  Esteban_2io
drwxrwxrwx  9 jdosio jdosio        4096 Jun  9 04:08  Esteban_2iousb
-rwxr-xr-x  1 jdosio jdosio         345 Jun  9 01:45  fromscratch_fromscratch.desktop
-rw-rw-r--  1 jdosio jdosio       15396 Aug 11 23:07 'Indep Study.docx'
-rwxr-xr-x  1 jdosio jdosio       21390 May  7 07:35  libreoffice-writer.desktop
-rw-rw-r--  1 jdosio jdosio   110886277 May 29 17:21  NVIDIA-Linux-x86_64-430.14.run
-rw-rw-r--  1 jdosio jdosio      277378 Aug  3 11:59  squat_rippetoe.pdf
-rwx--x--x  1 jdosio jdosio        1906 Jun  3 02:58  start-tor-browser.desktop
drwxrwxrwx  2 jdosio jdosio        4096 Jun  9 03:00 'System Volume Information'
drwxrwxr-x  3 jdosio jdosio        4096 Aug 12 23:01  tex
drwxrwxrwx  4 jdosio jdosio        4096 May 19 23:10  USB2io

jdosio@2io-01:~/Desktop$ ./NVIDIA-Linux-x86_64-430.14.run --uninstall
bash: ./NVIDIA-Linux-x86_64-430.14.run: Permission denied
jdosio@2io-01:~/Desktop$ sudo ./NVIDIA-Linux-x86_64-430.14.run --uninstall
[sudo] password for jdosio: 
sudo: ./NVIDIA-Linux-x86_64-430.14.run: command not found
jdosio@2io-01:~/Desktop$ 

```

---

### Post by Bashing-om on 2019-08-25
jdosio; Yukkie on me :(

I can not explain why the --uninstall fails.
Hopefully others here will have the greater insight.

[INDENT][INDENT]sometimes I do wonder
[INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jdosio on 2019-08-25
bump

---

### Post by oldfred on 2019-08-27
```
        -rw-rw-r--  1 jdosio jdosio   110886277 May 29 17:21  NVIDIA-Linux-x86_64-430.14.run 
    
```

Shows why you cannot execute it. No x in permissions.
You can change with Naulitus (right click, properties) & permissions on box that says allow executing or use command line to change permissions to allow execute.

---

### Post by jdosio on 2019-08-27
Haza ! it seems you were correct!
i checked the box like you said and executed the 
```

sudo ./NVIDIA-Linux-x86_64-430.14.run --uninstall

```
as soon as the uninstall began it asked me if i wanted to restor the back up x conficuration to which i put yes, and was then faced with this screen;(See pic)
the installation continued and showed me a myriad of error messeges mentioning it was unable to create a directorry here or access some other thing somewhere else, there were a few of them. eventually the uninstall finished and so know going over some of the initial commands that you mentioned...
```

jdosio@2io-01:~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/5.0.0-25-generic/updates/dkms
Found nvidia module: nvidia-drm.ko
Looking for amdgpu modules in /lib/modules/5.0.0-25-generic/updates/dkms
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

```
seems the uninstall blacklisted it :(
here is the result of 
```

cat /var/log/gpu-manager.log

```
[https://paste.ubuntu.com/p/FhXtGkPfF8/](https://paste.ubuntu.com/p/FhXtGkPfF8/)

---

### Post by Bashing-om on 2019-08-27
jdosio; Yukkie - somewhat 

As removing the Nvidia driver should have released the nouveau driver.
So we poke some more.
what shows:
```

sudo grep 'blacklist.*nouveau' /etc/modprobe.d/*
ls -al /lib/modprobe.d
ls -al /usr/share/X11/xorg.conf.d/
find /lib/modules/`uname -r`/ -name 'nvidia*' ##(those are back ticks around uname -r ``)

```

see what it takes to clean the system up and get it functional  .. then see what we are going to do.

-all in the process-

---

### Post by oldfred on 2019-08-27
I just uninstalled nVidia from my system, but have never used the .run file.
I was only running nVidia as old monitor had DVI-D & VGA in, but motherboard had HDMI & displayport out. Older nVidia card had DVI connection. Intel chip's video performance was same or slightly better than older nVidia card.

Found HDMI to DVI cable, so removed nVidia, but because card was still  installed it saw it. And all the nVidia software was still in system.

1952  dkms status
 1953  sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
 1954  cat /etc/X11/xorg.conf  <--- did not show anything so ok
 1955  dkms status   <--- only after reboot did it not show nVidia as part of dkms.
 1956  lspci -vnn | grep VGA -A 12
 1957  dkms status
Did a few other things:
 1980  lspci | grep VGA
Only after I rebooted & then did sudo apt autoremove to clear out all the old nVidia related software.


You will either need to change nouveau's status so not blacklisted when you reboot, you may need nomodeset boot parameter.
But probably better to install nVidia driver correctly using ppa before reboot.

       If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

### Post by jdosio on 2019-08-30
hey here are the results of what you mentioned...

```

jdosio@2io-01:~$ sudo grep 'blacklist.*nouveau' /etc/modprobe.d/*
[sudo] password for jdosio: 
jdosio@2io-01:~$ sudo grep 'blacklist.*nouveau' /etc/modprobe.d/*
jdosio@2io-01:~$ ls -al /lib/modprobe.d
total 44
drwxr-xr-x  2 root root 4096 Aug 18 20:40 .
drwxr-xr-x 22 root root 4096 May 29 18:19 ..
-rw-r--r--  1 root root  655 Nov 12  2018 aliases.conf
-rw-r--r--  1 root root 1461 Aug  6 06:45 blacklist_linux_4.15.0-58-generic.conf
-rw-r--r--  1 root root 1528 Jul 29 11:46 blacklist_linux-hwe_5.0.0-23-generic.conf
-rw-r--r--  1 root root 1528 Aug  1 08:34 blacklist_linux-hwe_5.0.0-25-generic.conf
-rw-r--r--  1 root root  183 Aug 18 20:40 blacklist-nvidia.conf
-rw-r--r--  1 root root  390 Jul 22 12:45 fbdev-blacklist.conf
-rw-r--r--  1 root root   81 Jul 31 02:15 nvidia-graphics-drivers.conf
-rw-r--r--  1 root root  110 Jun  1 15:05 nvidia-kms.conf
-rw-r--r--  1 root root  765 Jan 28  2018 systemd.conf
jdosio@2io-01:~$ ls -al /usr/share/X11/xorg.conf.d/
total 32
drwxr-xr-x 2 root root 4096 Aug 27 22:13 .
drwxr-xr-x 5 root root 4096 May 29 15:37 ..
-rw-r--r-- 1 root root   92 May 29 06:19 10-amdgpu.conf
-rw-r--r-- 1 root root  210 Jul 31 02:15 10-nvidia.conf
-rw-r--r-- 1 root root 1350 May  2 04:06 10-quirks.conf
-rw-r--r-- 1 root root   92 May 29 06:19 10-radeon.conf
-rw-r--r-- 1 root root  945 Nov 27  2018 40-libinput.conf
-rw-r--r-- 1 root root 3025 Nov 27  2018 70-wacom.conf
jdosio@2io-01:~$ find /lib/modules/`uname -r`/ -name 'nvidia*'
/lib/modules/5.0.0-25-generic/updates/dkms/nvidia-drm.ko
/lib/modules/5.0.0-25-generic/updates/dkms/nvidia.ko
/lib/modules/5.0.0-25-generic/updates/dkms/nvidia-modeset.ko
/lib/modules/5.0.0-25-generic/updates/dkms/nvidia-uvm.ko
/lib/modules/5.0.0-25-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/5.0.0-25-generic/kernel/drivers/video/fbdev/nvidia
/lib/modules/5.0.0-25-generic/kernel/drivers/video/fbdev/nvidia/nvidiafb.ko

```

also im not sure how to implement oldfred's solution, still reading the threads you sent. this is my dkms status though,

```

jdosio@2io-01:~$ dkms status
nvidia, 430.40, 4.15.0-58-generic, x86_64: installed
nvidia, 430.40, 5.0.0-23-generic, x86_64: installed
nvidia, 430.40, 5.0.0-25-generic, x86_64: installed
wireguard, 0.0.20190702, 5.0.0-23-generic, x86_64: installed
wireguard, 0.0.20190702, 5.0.0-25-generic, x86_64: installed

```
im assuming the goal is to get nvidia to not show up there to confirm it is uninstalled?

---

### Post by oldfred on 2019-08-30
Yes you want it out of dkms, but may need nouveau to be able to use nomodeset boot parameter to boot. Make sure that is not still blacklisted.

But your nVidia 430.xx looks like a normal install. Did you already reinstall?
And did you purge all old nVidia before reinstall? Otherwise conflicts and problems.
If purged & reinstalled, it may be ok.

---

### Post by jdosio on 2019-08-31
so i followed the 
```

jdosio@2io-01:~$ sudo apt-get purge nvidia*
[sudo] password for jdosio: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'nvidia-325-updates' for glob 'nvidia*'
Note, selecting 'nvidia-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-binary' for glob 'nvidia*'
Note, selecting 'nvidia-331-dev' for glob 'nvidia*'
Note, selecting 'nvidia-304-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-384-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-cg-toolkit' for glob 'nvidia*'
Note, selecting 'nvidia-driver-libs-i386:i386' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-390' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-410' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-415' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-418' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-430' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-384-updates' for glob 'nvidia*'
Note, selecting 'nvidia' for glob 'nvidia*'
Note, selecting 'nvidia-driver' for glob 'nvidia*'
Note, selecting 'nvidia-367-updates' for glob 'nvidia*'
Note, selecting 'nvidia-modprobe' for glob 'nvidia*'
Note, selecting 'nvidia-texture-tools' for glob 'nvidia*'
Note, selecting 'nvidia-utils' for glob 'nvidia*'
Note, selecting 'nvidia-387-updates' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-340xx-vdpau-driver' for glob 'nvidia*'
Note, selecting 'nvidia-349-updates' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-304-updates' for glob 'nvidia*'
Note, selecting 'nvidia-310-updates' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-352-dev' for glob 'nvidia*'
Note, selecting 'nvidia-vdpau-driver' for glob 'nvidia*'
Note, selecting 'nvidia-346-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-utils-390' for glob 'nvidia*'
Note, selecting 'nvidia-smi' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-313-updates' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-340xx-kernel-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-334-updates' for glob 'nvidia*'
Note, selecting 'nvidia-utils-410' for glob 'nvidia*'
Note, selecting 'nvidia-utils-415' for glob 'nvidia*'
Note, selecting 'nvidia-utils-418' for glob 'nvidia*'
Note, selecting 'nvidia-utils-430' for glob 'nvidia*'
Note, selecting 'nvidia-331-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-prime' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-390' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-410' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-415' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-418' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-430' for glob 'nvidia*'
Note, selecting 'nvidia-current-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-dev' for glob 'nvidia*'
Note, selecting 'nvidia-nsight' for glob 'nvidia*'
Note, selecting 'nvidia-common' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-390' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-410' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-415' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-418' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-430' for glob 'nvidia*'
Note, selecting 'nvidia-current-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-390' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-410' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-415' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-418' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-430' for glob 'nvidia*'
Note, selecting 'nvidia-355-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-libs-nonglvnd' for glob 'nvidia*'
Note, selecting 'nvidia-375-dev' for glob 'nvidia*'
Note, selecting 'nvidia-current' for glob 'nvidia*'
Note, selecting 'nvidia-profiler' for glob 'nvidia*'
Note, selecting 'nvidia-375-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-390' for glob 'nvidia*'
Note, selecting 'nvidia-337-updates' for glob 'nvidia*'
Note, selecting 'nvidia-358-updates' for glob 'nvidia*'
Note, selecting 'nvidia-367-dev' for glob 'nvidia*'
Note, selecting 'nvidia-driver-410' for glob 'nvidia*'
Note, selecting 'nvidia-driver-415' for glob 'nvidia*'
Note, selecting 'nvidia-driver-418' for glob 'nvidia*'
Note, selecting 'nvidia-driver-430' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-toolkit' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-304xx-driver' for glob 'nvidia*'
Note, selecting 'nvidia-driver-libs' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source' for glob 'nvidia*'
Note, selecting 'nvidia-378-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-319-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304-dev' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-visual-profiler' for glob 'nvidia*'
Note, selecting 'nvidia-persistenced' for glob 'nvidia*'
Note, selecting 'nvidia-361-dev' for glob 'nvidia*'
Note, selecting 'nvidia-settings-binary' for glob 'nvidia*'
Note, selecting 'nvidia-361-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-304' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-331' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-340' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-346' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-352' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-361' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-367' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-375' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-384' for glob 'nvidia*'
Note, selecting 'nvidia-352-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-headless-390' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-340xx-driver' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-304-updates' for glob 'nvidia*'
Note, selecting 'nvidia-headless-410' for glob 'nvidia*'
Note, selecting 'nvidia-headless-415' for glob 'nvidia*'
Note, selecting 'nvidia-headless-418' for glob 'nvidia*'
Note, selecting 'nvidia-headless-430' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-doc' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-dev' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-dev' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-304xx-kernel-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-cg-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cg-doc' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-381-updates' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-304' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-331' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-340' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-346' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-352' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-361' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-367' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-375' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-gdb' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-304' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-384' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-310' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-313' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-319' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-325' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-331' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-334' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-337' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-340' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-343' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-346' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-349' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-352' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-355' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-358' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-361' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-364' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-367' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-375' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-378' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-381' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-384' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-387' for glob 'nvidia*'
Note, selecting 'nvidia-343-updates' for glob 'nvidia*'
Note, selecting 'nvidia-364-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304' for glob 'nvidia*'
Note, selecting 'nvidia-310' for glob 'nvidia*'
Note, selecting 'nvidia-313' for glob 'nvidia*'
Note, selecting 'nvidia-319' for glob 'nvidia*'
Note, selecting 'nvidia-325' for glob 'nvidia*'
Note, selecting 'nvidia-331' for glob 'nvidia*'
Note, selecting 'nvidia-334' for glob 'nvidia*'
Note, selecting 'nvidia-337' for glob 'nvidia*'
Note, selecting 'nvidia-340' for glob 'nvidia*'
Note, selecting 'nvidia-343' for glob 'nvidia*'
Note, selecting 'nvidia-346' for glob 'nvidia*'
Note, selecting 'nvidia-349' for glob 'nvidia*'
Note, selecting 'nvidia-352' for glob 'nvidia*'
Note, selecting 'nvidia-355' for glob 'nvidia*'
Note, selecting 'nvidia-358' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-390' for glob 'nvidia*'
Note, selecting 'nvidia-361' for glob 'nvidia*'
Note, selecting 'nvidia-364' for glob 'nvidia*'
Note, selecting 'nvidia-367' for glob 'nvidia*'
Note, selecting 'nvidia-375' for glob 'nvidia*'
Note, selecting 'nvidia-378' for glob 'nvidia*'
Note, selecting 'nvidia-381' for glob 'nvidia*'
Note, selecting 'nvidia-384' for glob 'nvidia*'
Note, selecting 'nvidia-387' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-kernel' for glob 'nvidia*'
Note, selecting 'nvidia-390' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-410' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-415' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-418' for glob 'nvidia*'
Note, selecting 'nvidia-346-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-430' for glob 'nvidia*'
Note, selecting 'nvidia-settings' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd' for glob 'nvidia*'
Note, selecting 'nvidia-settings' instead of 'nvidia-settings-binary'
Package 'nvidia-libopencl1-dev' is not installed, so not removed
Package 'nvidia-libopencl1' is not installed, so not removed
Package 'nvidia-vdpau-driver' is not installed, so not removed
Package 'nvidia-legacy-340xx-vdpau-driver' is not installed, so not removed
Package 'nvidia-driver' is not installed, so not removed
Package 'nvidia-legacy-340xx-driver' is not installed, so not removed
Package 'nvidia-legacy-304xx-driver' is not installed, so not removed
Package 'nvidia-kernel-dkms' is not installed, so not removed
Package 'nvidia-legacy-340xx-kernel-dkms' is not installed, so not removed
Package 'nvidia-legacy-304xx-kernel-dkms' is not installed, so not removed
Package 'nvidia' is not installed, so not removed
Package 'nvidia-current-updates' is not installed, so not removed
Package 'nvidia-experimental-304' is not installed, so not removed
Package 'nvidia-310' is not installed, so not removed
Package 'nvidia-310-updates' is not installed, so not removed
Package 'nvidia-experimental-310' is not installed, so not removed
Package 'nvidia-313' is not installed, so not removed
Package 'nvidia-313-updates' is not installed, so not removed
Package 'nvidia-experimental-313' is not installed, so not removed
Package 'nvidia-319' is not installed, so not removed
Package 'nvidia-319-updates' is not installed, so not removed
Package 'nvidia-experimental-319' is not installed, so not removed
Package 'nvidia-325' is not installed, so not removed
Package 'nvidia-325-updates' is not installed, so not removed
Package 'nvidia-experimental-325' is not installed, so not removed
Package 'nvidia-experimental-331' is not installed, so not removed
Package 'nvidia-334' is not installed, so not removed
Package 'nvidia-334-updates' is not installed, so not removed
Package 'nvidia-experimental-334' is not installed, so not removed
Package 'nvidia-337' is not installed, so not removed
Package 'nvidia-337-updates' is not installed, so not removed
Package 'nvidia-experimental-337' is not installed, so not removed
Package 'nvidia-experimental-340' is not installed, so not removed
Package 'nvidia-343' is not installed, so not removed
Package 'nvidia-343-updates' is not installed, so not removed
Package 'nvidia-experimental-343' is not installed, so not removed
Package 'nvidia-experimental-346' is not installed, so not removed
Package 'nvidia-349' is not installed, so not removed
Package 'nvidia-349-updates' is not installed, so not removed
Package 'nvidia-experimental-349' is not installed, so not removed
Package 'nvidia-experimental-352' is not installed, so not removed
Package 'nvidia-355' is not installed, so not removed
Package 'nvidia-355-updates' is not installed, so not removed
Package 'nvidia-experimental-355' is not installed, so not removed
Package 'nvidia-358' is not installed, so not removed
Package 'nvidia-358-updates' is not installed, so not removed
Package 'nvidia-experimental-358' is not installed, so not removed
Package 'nvidia-experimental-361' is not installed, so not removed
Package 'nvidia-364' is not installed, so not removed
Package 'nvidia-364-updates' is not installed, so not removed
Package 'nvidia-experimental-364' is not installed, so not removed
Package 'nvidia-367-updates' is not installed, so not removed
Package 'nvidia-experimental-367' is not installed, so not removed
Package 'nvidia-375-updates' is not installed, so not removed
Package 'nvidia-experimental-375' is not installed, so not removed
Package 'nvidia-378' is not installed, so not removed
Package 'nvidia-378-updates' is not installed, so not removed
Package 'nvidia-experimental-378' is not installed, so not removed
Package 'nvidia-381' is not installed, so not removed
Package 'nvidia-381-updates' is not installed, so not removed
Package 'nvidia-experimental-381' is not installed, so not removed
Package 'nvidia-384-updates' is not installed, so not removed
Package 'nvidia-experimental-384' is not installed, so not removed
Package 'nvidia-387' is not installed, so not removed
Package 'nvidia-387-updates' is not installed, so not removed
Package 'nvidia-experimental-387' is not installed, so not removed
Note, selecting 'libnvtt-bin' instead of 'nvidia-texture-tools'
Package 'nvidia-driver-libs' is not installed, so not removed
Package 'nvidia-driver-libs-nonglvnd' is not installed, so not removed
Package 'nvidia-390' is not installed, so not removed
Package 'nvidia-driver-libs-i386:i386' is not installed, so not removed
Package 'nvidia-340-updates-uvm' is not installed, so not removed
Package 'nvidia-346' is not installed, so not removed
Package 'nvidia-346-dev' is not installed, so not removed
Package 'nvidia-346-updates' is not installed, so not removed
Package 'nvidia-346-updates-dev' is not installed, so not removed
Package 'nvidia-352' is not installed, so not removed
Package 'nvidia-352-dev' is not installed, so not removed
Package 'nvidia-352-updates' is not installed, so not removed
Package 'nvidia-352-updates-dev' is not installed, so not removed
Package 'nvidia-361' is not installed, so not removed
Package 'nvidia-361-dev' is not installed, so not removed
Package 'nvidia-361-updates' is not installed, so not removed
Package 'nvidia-361-updates-dev' is not installed, so not removed
Package 'nvidia-367' is not installed, so not removed
Package 'nvidia-367-dev' is not installed, so not removed
Package 'nvidia-375' is not installed, so not removed
Package 'nvidia-375-dev' is not installed, so not removed
Package 'nvidia-cg-dev' is not installed, so not removed
Package 'nvidia-cg-doc' is not installed, so not removed
Package 'nvidia-cg-toolkit' is not installed, so not removed
Package 'nvidia-cuda-dev' is not installed, so not removed
Package 'nvidia-cuda-doc' is not installed, so not removed
Package 'nvidia-cuda-gdb' is not installed, so not removed
Package 'nvidia-cuda-toolkit' is not installed, so not removed
Package 'nvidia-libopencl1-346' is not installed, so not removed
Package 'nvidia-libopencl1-346-updates' is not installed, so not removed
Package 'nvidia-libopencl1-352' is not installed, so not removed
Package 'nvidia-libopencl1-352-updates' is not installed, so not removed
Package 'nvidia-libopencl1-361' is not installed, so not removed
Package 'nvidia-libopencl1-361-updates' is not installed, so not removed
Package 'nvidia-libopencl1-367' is not installed, so not removed
Package 'nvidia-libopencl1-375' is not installed, so not removed
Package 'nvidia-modprobe' is not installed, so not removed
Package 'nvidia-nsight' is not installed, so not removed
Package 'nvidia-opencl-dev' is not installed, so not removed
Package 'nvidia-opencl-icd-346' is not installed, so not removed
Package 'nvidia-opencl-icd-346-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-352' is not installed, so not removed
Package 'nvidia-opencl-icd-352-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-361' is not installed, so not removed
Package 'nvidia-opencl-icd-361-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-367' is not installed, so not removed
Package 'nvidia-opencl-icd-375' is not installed, so not removed
Package 'nvidia-profiler' is not installed, so not removed
Package 'nvidia-visual-profiler' is not installed, so not removed
Package 'nvidia-common' is not installed, so not removed
Package 'nvidia-331' is not installed, so not removed
Package 'nvidia-331-dev' is not installed, so not removed
Package 'nvidia-331-updates' is not installed, so not removed
Package 'nvidia-331-updates-dev' is not installed, so not removed
Package 'nvidia-331-updates-uvm' is not installed, so not removed
Package 'nvidia-331-uvm' is not installed, so not removed
Package 'nvidia-340' is not installed, so not removed
Package 'nvidia-340-dev' is not installed, so not removed
Package 'nvidia-340-updates' is not installed, so not removed
Package 'nvidia-340-updates-dev' is not installed, so not removed
Package 'nvidia-340-uvm' is not installed, so not removed
Package 'nvidia-opencl-icd-340' is not installed, so not removed
Package 'nvidia-libopencl1-331' is not installed, so not removed
Package 'nvidia-libopencl1-331-updates' is not installed, so not removed
Package 'nvidia-libopencl1-340' is not installed, so not removed
Package 'nvidia-libopencl1-340-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-331' is not installed, so not removed
Package 'nvidia-opencl-icd-331-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-340-updates' is not installed, so not removed
Package 'nvidia-304' is not installed, so not removed
Package 'nvidia-304-dev' is not installed, so not removed
Package 'nvidia-304-updates' is not installed, so not removed
Package 'nvidia-304-updates-dev' is not installed, so not removed
Package 'nvidia-384' is not installed, so not removed
Package 'nvidia-384-dev' is not installed, so not removed
Package 'nvidia-compute-utils-390' is not installed, so not removed
Package 'nvidia-compute-utils-410' is not installed, so not removed
Package 'nvidia-compute-utils-415' is not installed, so not removed
Package 'nvidia-compute-utils-418' is not installed, so not removed
Package 'nvidia-current' is not installed, so not removed
Package 'nvidia-current-dev' is not installed, so not removed
Package 'nvidia-dkms-390' is not installed, so not removed
Package 'nvidia-dkms-410' is not installed, so not removed
Package 'nvidia-dkms-415' is not installed, so not removed
Package 'nvidia-dkms-418' is not installed, so not removed
Package 'nvidia-driver-390' is not installed, so not removed
Package 'nvidia-driver-410' is not installed, so not removed
Package 'nvidia-driver-415' is not installed, so not removed
Package 'nvidia-driver-418' is not installed, so not removed
Package 'nvidia-headless-390' is not installed, so not removed
Package 'nvidia-headless-410' is not installed, so not removed
Package 'nvidia-headless-415' is not installed, so not removed
Package 'nvidia-headless-418' is not installed, so not removed
Package 'nvidia-headless-430' is not installed, so not removed
Package 'nvidia-headless-no-dkms-390' is not installed, so not removed
Package 'nvidia-headless-no-dkms-410' is not installed, so not removed
Package 'nvidia-headless-no-dkms-415' is not installed, so not removed
Package 'nvidia-headless-no-dkms-418' is not installed, so not removed
Package 'nvidia-headless-no-dkms-430' is not installed, so not removed
Package 'nvidia-kernel-common-390' is not installed, so not removed
Package 'nvidia-kernel-common-410' is not installed, so not removed
Package 'nvidia-kernel-common-415' is not installed, so not removed
Package 'nvidia-kernel-common-418' is not installed, so not removed
Package 'nvidia-kernel-source-390' is not installed, so not removed
Package 'nvidia-kernel-source-410' is not installed, so not removed
Package 'nvidia-kernel-source-415' is not installed, so not removed
Package 'nvidia-kernel-source-418' is not installed, so not removed
Package 'nvidia-libopencl1-304' is not installed, so not removed
Package 'nvidia-libopencl1-304-updates' is not installed, so not removed
Package 'nvidia-libopencl1-384' is not installed, so not removed
Package 'nvidia-opencl-icd-304' is not installed, so not removed
Package 'nvidia-opencl-icd-304-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-384' is not installed, so not removed
Package 'nvidia-utils-390' is not installed, so not removed
Package 'nvidia-utils-410' is not installed, so not removed
Package 'nvidia-utils-415' is not installed, so not removed
Package 'nvidia-utils-418' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libnvidia-cfg1-430 libnvidia-common-430 libnvidia-decode-430
  libnvidia-decode-430:i386 libnvidia-encode-430 libnvidia-encode-430:i386
  libnvidia-fbc1-430 libnvidia-fbc1-430:i386 libnvidia-gl-430
  libnvidia-gl-430:i386 libnvidia-ifr1-430 libnvidia-ifr1-430:i386 libxnvctrl0
  pkg-config screen-resolution-extra xserver-xorg-video-nvidia-430
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  nvidia-compute-utils-430* nvidia-dkms-430* nvidia-driver-430*
  nvidia-kernel-common-430* nvidia-kernel-source-430* nvidia-prime*
  nvidia-settings* nvidia-utils-430*
0 upgraded, 0 newly installed, 8 to remove and 3 not upgraded.
After this operation, 38.8 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 301520 files and directories currently installed.)
Removing nvidia-driver-430 (430.40-0ubuntu0~gpu18.04.1) ...
Removing nvidia-compute-utils-430 (430.40-0ubuntu0~gpu18.04.1) ...
Removing nvidia-dkms-430 (430.40-0ubuntu0~gpu18.04.1) ...
Removing all DKMS Modules
Done.
INFO:Disable nvidia
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
update-initramfs: deferring update (trigger activated)
Removing nvidia-kernel-common-430 (430.40-0ubuntu0~gpu18.04.1) ...
update-initramfs: deferring update (trigger activated)
Removing nvidia-kernel-source-430 (430.40-0ubuntu0~gpu18.04.1) ...
Removing nvidia-prime (0.8.8.2) ...
Removing nvidia-settings (418.56-0ubuntu0~gpu18.04.1) ...
Removing nvidia-utils-430 (430.40-0ubuntu0~gpu18.04.1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for initramfs-tools (0.130ubuntu3.8) ...
update-initramfs: Generating /boot/initrd.img-5.0.0-25-generic
Processing triggers for bamfdaemon (0.5.3+18.04.20180207.2-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
(Reading database ... 301022 files and directories currently installed.)
Purging configuration files for nvidia-prime (0.8.8.2) ...
Purging configuration files for nvidia-kernel-common-430 (430.40-0ubuntu0~gpu18.04.1) ...
update-initramfs: deferring update (trigger activated)
Purging configuration files for nvidia-settings (418.56-0ubuntu0~gpu18.04.1) ...
Purging configuration files for nvidia-compute-utils-430 (430.40-0ubuntu0~gpu18.04.1) ...
Purging configuration files for nvidia-dkms-430 (430.40-0ubuntu0~gpu18.04.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.130ubuntu3.8) ...
update-initramfs: Generating /boot/initrd.img-5.0.0-25-generic
jdosio@2io-01:~$ dkms status
wireguard, 0.0.20190702, 5.0.0-23-generic, x86_64: installed
wireguard, 0.0.20190702, 5.0.0-25-generic, x86_64: installed
jdosio@2io-01:~$ 

```

And now dkms no longer shows nvidia, however i have not un-blacklisted the nouveau driver, nor know what a nomodeset boot parameter is so i have not restarted just yet, how would i go about unblacklisting nouveau?

---

### Post by oldfred on 2019-08-31
Does this still show it blacklisted?
cat /var/log/gpu-manager.log

I have never unblacklisted nouveau as driver install seems to control that.
You can look in /etc/modprobe.d/blacklist.conf or perhaps other file in that folder.

I prefer to make sure the related files nVidia installs also are gone.

If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
    
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by jdosio on 2019-08-31
as you mentioned i checked with [COLOR=#000000]cat /var/log/gpu-manager.log and here are the results 
[/COLOR]```
jdosio@2io-01:~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/5.0.0-25-generic/updates/dkms
Found nvidia module: nvidia-drm.ko
Looking for amdgpu modules in /lib/modules/5.0.0-25-generic/updates/dkms
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
Vendor/Device Id: 8086:191b
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:139b
BusID "PCI:2@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:02:00.0/driver
The device is not bound to any driver.
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
output 0:
    card0-HDMI-A-1
output 1:
    card0-eDP-1
Number of connected outputs for /dev/dri/card0: 2
Does it require offloading? yes
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
Intel IGP detected
Intel hybrid system
Removing /usr/share/X11/xorg.conf.d/11-nvidia-prime.conf
Setting power control to "auto" in /sys/bus/pci/devices/0000:02:00.0/power/control

```[COLOR=#000000]

i also purged again like you instructed,
[/COLOR]```
jdosio@2io-01:~$ sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'nvidia-325-updates' for glob 'nvidia*'
Note, selecting 'nvidia-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-binary' for glob 'nvidia*'
Note, selecting 'nvidia-331-dev' for glob 'nvidia*'
Note, selecting 'nvidia-304-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-384-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-cg-toolkit' for glob 'nvidia*'
Note, selecting 'nvidia-driver-libs-i386:i386' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-390' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-410' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-415' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-418' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-430' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-384-updates' for glob 'nvidia*'
Note, selecting 'nvidia' for glob 'nvidia*'
Note, selecting 'nvidia-driver' for glob 'nvidia*'
Note, selecting 'nvidia-367-updates' for glob 'nvidia*'
Note, selecting 'nvidia-modprobe' for glob 'nvidia*'
Note, selecting 'nvidia-texture-tools' for glob 'nvidia*'
Note, selecting 'nvidia-utils' for glob 'nvidia*'
Note, selecting 'nvidia-387-updates' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-340xx-vdpau-driver' for glob 'nvidia*'
Note, selecting 'nvidia-349-updates' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-304-updates' for glob 'nvidia*'
Note, selecting 'nvidia-310-updates' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-352-dev' for glob 'nvidia*'
Note, selecting 'nvidia-vdpau-driver' for glob 'nvidia*'
Note, selecting 'nvidia-346-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-utils-390' for glob 'nvidia*'
Note, selecting 'nvidia-smi' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-313-updates' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-340xx-kernel-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-334-updates' for glob 'nvidia*'
Note, selecting 'nvidia-utils-410' for glob 'nvidia*'
Note, selecting 'nvidia-utils-415' for glob 'nvidia*'
Note, selecting 'nvidia-utils-418' for glob 'nvidia*'
Note, selecting 'nvidia-utils-430' for glob 'nvidia*'
Note, selecting 'nvidia-331-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-prime' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-390' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-410' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-415' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-418' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-430' for glob 'nvidia*'
Note, selecting 'nvidia-current-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-dev' for glob 'nvidia*'
Note, selecting 'nvidia-nsight' for glob 'nvidia*'
Note, selecting 'nvidia-common' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-390' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-410' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-415' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-418' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-430' for glob 'nvidia*'
Note, selecting 'nvidia-current-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-390' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-410' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-415' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-418' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-430' for glob 'nvidia*'
Note, selecting 'nvidia-355-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-libs-nonglvnd' for glob 'nvidia*'
Note, selecting 'nvidia-375-dev' for glob 'nvidia*'
Note, selecting 'nvidia-current' for glob 'nvidia*'
Note, selecting 'nvidia-profiler' for glob 'nvidia*'
Note, selecting 'nvidia-375-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-390' for glob 'nvidia*'
Note, selecting 'nvidia-337-updates' for glob 'nvidia*'
Note, selecting 'nvidia-358-updates' for glob 'nvidia*'
Note, selecting 'nvidia-367-dev' for glob 'nvidia*'
Note, selecting 'nvidia-driver-410' for glob 'nvidia*'
Note, selecting 'nvidia-driver-415' for glob 'nvidia*'
Note, selecting 'nvidia-driver-418' for glob 'nvidia*'
Note, selecting 'nvidia-driver-430' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-toolkit' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-304xx-driver' for glob 'nvidia*'
Note, selecting 'nvidia-driver-libs' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source' for glob 'nvidia*'
Note, selecting 'nvidia-378-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-319-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304-dev' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-visual-profiler' for glob 'nvidia*'
Note, selecting 'nvidia-persistenced' for glob 'nvidia*'
Note, selecting 'nvidia-361-dev' for glob 'nvidia*'
Note, selecting 'nvidia-settings-binary' for glob 'nvidia*'
Note, selecting 'nvidia-361-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-304' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-331' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-340' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-346' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-352' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-361' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-367' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-375' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-384' for glob 'nvidia*'
Note, selecting 'nvidia-352-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-headless-390' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-340xx-driver' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-304-updates' for glob 'nvidia*'
Note, selecting 'nvidia-headless-410' for glob 'nvidia*'
Note, selecting 'nvidia-headless-415' for glob 'nvidia*'
Note, selecting 'nvidia-headless-418' for glob 'nvidia*'
Note, selecting 'nvidia-headless-430' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-doc' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-dev' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-dev' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-304xx-kernel-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-cg-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cg-doc' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-381-updates' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-304' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-331' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-340' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-346' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-352' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-361' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-367' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-375' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-gdb' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-304' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-384' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-310' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-313' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-319' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-325' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-331' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-334' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-337' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-340' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-343' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-346' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-349' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-352' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-355' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-358' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-361' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-364' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-367' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-375' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-378' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-381' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-384' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-387' for glob 'nvidia*'
Note, selecting 'nvidia-343-updates' for glob 'nvidia*'
Note, selecting 'nvidia-364-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304' for glob 'nvidia*'
Note, selecting 'nvidia-310' for glob 'nvidia*'
Note, selecting 'nvidia-313' for glob 'nvidia*'
Note, selecting 'nvidia-319' for glob 'nvidia*'
Note, selecting 'nvidia-325' for glob 'nvidia*'
Note, selecting 'nvidia-331' for glob 'nvidia*'
Note, selecting 'nvidia-334' for glob 'nvidia*'
Note, selecting 'nvidia-337' for glob 'nvidia*'
Note, selecting 'nvidia-340' for glob 'nvidia*'
Note, selecting 'nvidia-343' for glob 'nvidia*'
Note, selecting 'nvidia-346' for glob 'nvidia*'
Note, selecting 'nvidia-349' for glob 'nvidia*'
Note, selecting 'nvidia-352' for glob 'nvidia*'
Note, selecting 'nvidia-355' for glob 'nvidia*'
Note, selecting 'nvidia-358' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-390' for glob 'nvidia*'
Note, selecting 'nvidia-361' for glob 'nvidia*'
Note, selecting 'nvidia-364' for glob 'nvidia*'
Note, selecting 'nvidia-367' for glob 'nvidia*'
Note, selecting 'nvidia-375' for glob 'nvidia*'
Note, selecting 'nvidia-378' for glob 'nvidia*'
Note, selecting 'nvidia-381' for glob 'nvidia*'
Note, selecting 'nvidia-384' for glob 'nvidia*'
Note, selecting 'nvidia-387' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-kernel' for glob 'nvidia*'
Note, selecting 'nvidia-390' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-410' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-415' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-418' for glob 'nvidia*'
Note, selecting 'nvidia-346-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-430' for glob 'nvidia*'
Note, selecting 'nvidia-settings' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd' for glob 'nvidia*'
Note, selecting 'nvidia-settings' instead of 'nvidia-settings-binary'
Package 'nvidia-libopencl1-dev' is not installed, so not removed
Package 'nvidia-libopencl1' is not installed, so not removed
Package 'nvidia-vdpau-driver' is not installed, so not removed
Package 'nvidia-legacy-340xx-vdpau-driver' is not installed, so not removed
Package 'nvidia-driver' is not installed, so not removed
Package 'nvidia-legacy-340xx-driver' is not installed, so not removed
Package 'nvidia-legacy-304xx-driver' is not installed, so not removed
Package 'nvidia-kernel-dkms' is not installed, so not removed
Package 'nvidia-legacy-340xx-kernel-dkms' is not installed, so not removed
Package 'nvidia-legacy-304xx-kernel-dkms' is not installed, so not removed
Package 'nvidia' is not installed, so not removed
Package 'nvidia-current-updates' is not installed, so not removed
Package 'nvidia-experimental-304' is not installed, so not removed
Package 'nvidia-310' is not installed, so not removed
Package 'nvidia-310-updates' is not installed, so not removed
Package 'nvidia-experimental-310' is not installed, so not removed
Package 'nvidia-313' is not installed, so not removed
Package 'nvidia-313-updates' is not installed, so not removed
Package 'nvidia-experimental-313' is not installed, so not removed
Package 'nvidia-319' is not installed, so not removed
Package 'nvidia-319-updates' is not installed, so not removed
Package 'nvidia-experimental-319' is not installed, so not removed
Package 'nvidia-325' is not installed, so not removed
Package 'nvidia-325-updates' is not installed, so not removed
Package 'nvidia-experimental-325' is not installed, so not removed
Package 'nvidia-experimental-331' is not installed, so not removed
Package 'nvidia-334' is not installed, so not removed
Package 'nvidia-334-updates' is not installed, so not removed
Package 'nvidia-experimental-334' is not installed, so not removed
Package 'nvidia-337' is not installed, so not removed
Package 'nvidia-337-updates' is not installed, so not removed
Package 'nvidia-experimental-337' is not installed, so not removed
Package 'nvidia-experimental-340' is not installed, so not removed
Package 'nvidia-343' is not installed, so not removed
Package 'nvidia-343-updates' is not installed, so not removed
Package 'nvidia-experimental-343' is not installed, so not removed
Package 'nvidia-experimental-346' is not installed, so not removed
Package 'nvidia-349' is not installed, so not removed
Package 'nvidia-349-updates' is not installed, so not removed
Package 'nvidia-experimental-349' is not installed, so not removed
Package 'nvidia-experimental-352' is not installed, so not removed
Package 'nvidia-355' is not installed, so not removed
Package 'nvidia-355-updates' is not installed, so not removed
Package 'nvidia-experimental-355' is not installed, so not removed
Package 'nvidia-358' is not installed, so not removed
Package 'nvidia-358-updates' is not installed, so not removed
Package 'nvidia-experimental-358' is not installed, so not removed
Package 'nvidia-experimental-361' is not installed, so not removed
Package 'nvidia-364' is not installed, so not removed
Package 'nvidia-364-updates' is not installed, so not removed
Package 'nvidia-experimental-364' is not installed, so not removed
Package 'nvidia-367-updates' is not installed, so not removed
Package 'nvidia-experimental-367' is not installed, so not removed
Package 'nvidia-375-updates' is not installed, so not removed
Package 'nvidia-experimental-375' is not installed, so not removed
Package 'nvidia-378' is not installed, so not removed
Package 'nvidia-378-updates' is not installed, so not removed
Package 'nvidia-experimental-378' is not installed, so not removed
Package 'nvidia-381' is not installed, so not removed
Package 'nvidia-381-updates' is not installed, so not removed
Package 'nvidia-experimental-381' is not installed, so not removed
Package 'nvidia-384-updates' is not installed, so not removed
Package 'nvidia-experimental-384' is not installed, so not removed
Package 'nvidia-387' is not installed, so not removed
Package 'nvidia-387-updates' is not installed, so not removed
Package 'nvidia-experimental-387' is not installed, so not removed
Note, selecting 'libnvtt-bin' instead of 'nvidia-texture-tools'
Package 'nvidia-driver-libs' is not installed, so not removed
Package 'nvidia-driver-libs-nonglvnd' is not installed, so not removed
Package 'nvidia-390' is not installed, so not removed
Package 'nvidia-driver-libs-i386:i386' is not installed, so not removed
Package 'bbswitch-dkms' is not installed, so not removed
Package 'bumblebee' is not installed, so not removed
Package 'primus' is not installed, so not removed
Package 'nvidia-340-updates-uvm' is not installed, so not removed
Package 'nvidia-346' is not installed, so not removed
Package 'nvidia-346-dev' is not installed, so not removed
Package 'nvidia-346-updates' is not installed, so not removed
Package 'nvidia-346-updates-dev' is not installed, so not removed
Package 'nvidia-352' is not installed, so not removed
Package 'nvidia-352-dev' is not installed, so not removed
Package 'nvidia-352-updates' is not installed, so not removed
Package 'nvidia-352-updates-dev' is not installed, so not removed
Package 'nvidia-361' is not installed, so not removed
Package 'nvidia-361-dev' is not installed, so not removed
Package 'nvidia-361-updates' is not installed, so not removed
Package 'nvidia-361-updates-dev' is not installed, so not removed
Package 'nvidia-367' is not installed, so not removed
Package 'nvidia-367-dev' is not installed, so not removed
Package 'nvidia-375' is not installed, so not removed
Package 'nvidia-375-dev' is not installed, so not removed
Package 'nvidia-cg-dev' is not installed, so not removed
Package 'nvidia-cg-doc' is not installed, so not removed
Package 'nvidia-cg-toolkit' is not installed, so not removed
Package 'nvidia-cuda-dev' is not installed, so not removed
Package 'nvidia-cuda-doc' is not installed, so not removed
Package 'nvidia-cuda-gdb' is not installed, so not removed
Package 'nvidia-cuda-toolkit' is not installed, so not removed
Package 'nvidia-libopencl1-346' is not installed, so not removed
Package 'nvidia-libopencl1-346-updates' is not installed, so not removed
Package 'nvidia-libopencl1-352' is not installed, so not removed
Package 'nvidia-libopencl1-352-updates' is not installed, so not removed
Package 'nvidia-libopencl1-361' is not installed, so not removed
Package 'nvidia-libopencl1-361-updates' is not installed, so not removed
Package 'nvidia-libopencl1-367' is not installed, so not removed
Package 'nvidia-libopencl1-375' is not installed, so not removed
Package 'nvidia-modprobe' is not installed, so not removed
Package 'nvidia-nsight' is not installed, so not removed
Package 'nvidia-opencl-dev' is not installed, so not removed
Package 'nvidia-opencl-icd-346' is not installed, so not removed
Package 'nvidia-opencl-icd-346-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-352' is not installed, so not removed
Package 'nvidia-opencl-icd-352-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-361' is not installed, so not removed
Package 'nvidia-opencl-icd-361-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-367' is not installed, so not removed
Package 'nvidia-opencl-icd-375' is not installed, so not removed
Package 'nvidia-profiler' is not installed, so not removed
Package 'nvidia-visual-profiler' is not installed, so not removed
Package 'nvidia-prime' is not installed, so not removed
Package 'nvidia-common' is not installed, so not removed
Package 'nvidia-331' is not installed, so not removed
Package 'nvidia-331-dev' is not installed, so not removed
Package 'nvidia-331-updates' is not installed, so not removed
Package 'nvidia-331-updates-dev' is not installed, so not removed
Package 'nvidia-331-updates-uvm' is not installed, so not removed
Package 'nvidia-331-uvm' is not installed, so not removed
Package 'nvidia-340' is not installed, so not removed
Package 'nvidia-340-dev' is not installed, so not removed
Package 'nvidia-340-updates' is not installed, so not removed
Package 'nvidia-340-updates-dev' is not installed, so not removed
Package 'nvidia-340-uvm' is not installed, so not removed
Package 'nvidia-opencl-icd-340' is not installed, so not removed
Package 'nvidia-libopencl1-331' is not installed, so not removed
Package 'nvidia-libopencl1-331-updates' is not installed, so not removed
Package 'nvidia-libopencl1-340' is not installed, so not removed
Package 'nvidia-libopencl1-340-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-331' is not installed, so not removed
Package 'nvidia-opencl-icd-331-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-340-updates' is not installed, so not removed
Package 'nvidia-304' is not installed, so not removed
Package 'nvidia-304-dev' is not installed, so not removed
Package 'nvidia-304-updates' is not installed, so not removed
Package 'nvidia-304-updates-dev' is not installed, so not removed
Package 'nvidia-384' is not installed, so not removed
Package 'nvidia-384-dev' is not installed, so not removed
Package 'nvidia-compute-utils-390' is not installed, so not removed
Package 'nvidia-compute-utils-410' is not installed, so not removed
Package 'nvidia-compute-utils-415' is not installed, so not removed
Package 'nvidia-compute-utils-418' is not installed, so not removed
Package 'nvidia-compute-utils-430' is not installed, so not removed
Package 'nvidia-current' is not installed, so not removed
Package 'nvidia-current-dev' is not installed, so not removed
Package 'nvidia-dkms-390' is not installed, so not removed
Package 'nvidia-dkms-410' is not installed, so not removed
Package 'nvidia-dkms-415' is not installed, so not removed
Package 'nvidia-dkms-418' is not installed, so not removed
Package 'nvidia-dkms-430' is not installed, so not removed
Package 'nvidia-driver-390' is not installed, so not removed
Package 'nvidia-driver-410' is not installed, so not removed
Package 'nvidia-driver-415' is not installed, so not removed
Package 'nvidia-driver-418' is not installed, so not removed
Package 'nvidia-driver-430' is not installed, so not removed
Package 'nvidia-headless-390' is not installed, so not removed
Package 'nvidia-headless-410' is not installed, so not removed
Package 'nvidia-headless-415' is not installed, so not removed
Package 'nvidia-headless-418' is not installed, so not removed
Package 'nvidia-headless-430' is not installed, so not removed
Package 'nvidia-headless-no-dkms-390' is not installed, so not removed
Package 'nvidia-headless-no-dkms-410' is not installed, so not removed
Package 'nvidia-headless-no-dkms-415' is not installed, so not removed
Package 'nvidia-headless-no-dkms-418' is not installed, so not removed
Package 'nvidia-headless-no-dkms-430' is not installed, so not removed
Package 'nvidia-kernel-common-390' is not installed, so not removed
Package 'nvidia-kernel-common-410' is not installed, so not removed
Package 'nvidia-kernel-common-415' is not installed, so not removed
Package 'nvidia-kernel-common-418' is not installed, so not removed
Package 'nvidia-kernel-common-430' is not installed, so not removed
Package 'nvidia-kernel-source-390' is not installed, so not removed
Package 'nvidia-kernel-source-410' is not installed, so not removed
Package 'nvidia-kernel-source-415' is not installed, so not removed
Package 'nvidia-kernel-source-418' is not installed, so not removed
Package 'nvidia-kernel-source-430' is not installed, so not removed
Package 'nvidia-libopencl1-304' is not installed, so not removed
Package 'nvidia-libopencl1-304-updates' is not installed, so not removed
Package 'nvidia-libopencl1-384' is not installed, so not removed
Package 'nvidia-opencl-icd-304' is not installed, so not removed
Package 'nvidia-opencl-icd-304-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-384' is not installed, so not removed
Package 'nvidia-settings' is not installed, so not removed
Package 'nvidia-utils-390' is not installed, so not removed
Package 'nvidia-utils-410' is not installed, so not removed
Package 'nvidia-utils-415' is not installed, so not removed
Package 'nvidia-utils-418' is not installed, so not removed
Package 'nvidia-utils-430' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libnvidia-cfg1-430 libnvidia-common-430 libnvidia-decode-430 libnvidia-decode-430:i386 libnvidia-encode-430
  libnvidia-encode-430:i386 libnvidia-fbc1-430 libnvidia-fbc1-430:i386 libnvidia-gl-430 libnvidia-gl-430:i386
  libnvidia-ifr1-430 libnvidia-ifr1-430:i386 libxnvctrl0 pkg-config screen-resolution-extra
  xserver-xorg-video-nvidia-430
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```[COLOR=#000000]
should i now do sudo apt autoremove?
i could not find any [/COLOR][COLOR=#000000]/etc/modprobe.d/blacklist.conf
and in fact found no modprobe.

the xorg file you mentioned might not exist does not,
[/COLOR]```
jdosio@2io-01:~$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
mv: cannot stat '/etc/X11/xorg.conf': No such file or directory

```[COLOR=#000000]
grub menu is encountered after reboot correct? i am not quite sure about any of this so im being very cautious not to do something dumb 
what exactly is [/COLOR][COLOR=#000000]NOMODESET?
will find out how to reach grub menu will report back with more info in a moment.[/COLOR]

---

### Post by oldfred on 2019-08-31
If you only have Ubuntu, you have to get to grub menu. With only one install, it just automatically loads that.
If UEFI, you press escape key right after UEFI/BIOS screen.
IF BIOS install, you press & hold shift key until grub menu appears.

But if UEFI, best to have fast boot in UEFI off, as if on, you may not have time to press any key. Then you usually can do a full cold boot, not warm reboot to get it to do a normal boot and give time to press keys.

I show all these files for blacklisting.

```
fred@bionic-z97:~$ ls -l /etc/modprobe.d
total 44
-rw-r--r-- 1 root root 2507 Jul 30  2015 alsa-base.conf
-rw-r--r-- 1 root root  154 Jan  8  2018 amd64-microcode-blacklist.conf
-rw-r--r-- 1 root root  325 Jan 28  2018 blacklist-ath_pci.conf
-rw-r--r-- 1 root root 1667 Nov 12  2018 blacklist.conf
-rw-r--r-- 1 root root  210 Jan 28  2018 blacklist-firewire.conf
-rw-r--r-- 1 root root  697 Jan 28  2018 blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 Jul 30  2015 blacklist-modem.conf
lrwxrwxrwx 1 root root   41 May  4  2018 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root  583 Jan 28  2018 blacklist-rare-network.conf
-rw-r--r-- 1 root root  127 Feb  7  2017 dkms.conf
-rw-r--r-- 1 root root  154 May  3  2018 intel-microcode-blacklist.conf
-rw-r--r-- 1 root root  347 Jan 28  2018 iwlwifi.conf

```

---

### Post by jdosio on 2019-08-31
i do only have ubuntu, should i reinstall the driver before i go to grub menu?
could i do this through grub-customizer?

found a place in grub-customizer where the the "quiet splash" you mentioned appears but not sure if it is used for other stuff(see pic)

---

### Post by oldfred on 2019-08-31
I do not know Grub-Customizer.
It does create its own versions of grub's scripts, so then you are not running standard grub2.

---


---
title: "NVidia driver no longer loading after kernel update"
date: 2020-01-19
forum: Installation &amp; Upgrades
---

### Post by barbablu on 2020-01-19
My desktop suddenly started to load in low resolution.  I have an NVidia graphics card:
```

[COLOR=#202124][FONT=Roboto]lspci -v [/FONT][/COLOR]
...
[COLOR=#202124][FONT=Roboto]VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1) (prog-if 00 [VGA controller])[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]    Subsystem: Gigabyte Technology Co., Ltd GF116 [GeForce GTX 550 Ti][/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]    Flags: bus master, fast devsel, latency 0, IRQ 12[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]    Memory at f6000000 (32-bit, non-prefetchable) [size=32M][/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]    Memory at e0000000 (64-bit, prefetchable) [size=128M][/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]    Memory at ec000000 (64-bit, prefetchable) [size=64M][/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]    I/O ports at bf00 [size=128][/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K][/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]    Capabilities: <access denied>[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]    Kernel modules: nvidiafb, nouveau[/FONT][/COLOR]

```

But the NVidia card would not load:

```

[COLOR=#202124][FONT=Roboto]$ cat /var/log/gpu-manager.log[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]log_file: /var/log/gpu-manager.log[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]can't access /run/u-d-c-nvidia-was-loaded file[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]can't access /opt/amdgpu-pro/bin/amdgpu-pro-px[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Looking for nvidia modules in /lib/modules/5.3.0-26-generic/updates/dkms[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Looking for amdgpu modules in /lib/modules/5.3.0-26-generic/updates/dkms[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is nvidia loaded? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Was nvidia unloaded? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is nvidia blacklisted? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is intel loaded? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is radeon loaded? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is radeon blacklisted? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is amdgpu loaded? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is amdgpu blacklisted? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is amdgpu versioned? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is amdgpu pro stack? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is nouveau loaded? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is nouveau blacklisted? yes[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is nvidia kernel module available? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is amdgpu kernel module available? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Vendor/Device Id: 10de:1244[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]BusID "PCI:1@0:0:0"[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is boot vga? yes[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]The device is not bound to any driver.[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Error : Failed to open /dev/dri[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Error : Failed to open /dev/dri[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Error : Failed to open /dev/dri[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Error : Failed to open /dev/dri[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Does it require offloading? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]last cards number = 1[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Has amd? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Has intel? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Has nvidia? yes[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]How many cards? 1[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Has the system changed? No[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Single card detected[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Nothing to do
[/FONT][/COLOR]
```

My kernel is

```

[COLOR=#202124][FONT=Roboto]$ uname -a[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Linux nerone 5.3.0-26-generic #28~18.04.1-Ubuntu SMP Wed Dec 18 16:40:14 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux[/FONT][/COLOR]

```

I tried to no avail [COLOR=#202124][FONT=Roboto]to purge old packages including NVidea drivers as suggested in [/FONT][/COLOR][https://askubuntu.com/questions/59443/how-can-i-revert-back-from-an-upgrade-to-the-proposed-repository/229663#229663](https://askubuntu.com/questions/59443/how-can-i-revert-back-from-an-upgrade-to-the-proposed-repository/229663#229663)

My NVidia packages are in the 390 range:
```

dpkg -l | grep -i nvidia
ii  libnvidia-cfg1-390:amd64 390.116-0ubuntu0.18.04.1 amd64 NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-390 390.116-0ubuntu0.18.04.1 all  Shared files used by the NVIDIA libraries
ii  libnvidia-compute-390:amd64 390.116-0ubuntu0.18.04.1    amd64    NVIDIA libcompute package
ii  libnvidia-compute-390:i386  390.116-0ubuntu0.18.04.1    i386 NVIDIA libcompute package
ii  libnvidia-decode-390:amd64  390.116-0ubuntu0.18.04.1    amd64    NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-390:i386 390.116-0ubuntu0.18.04.1    i386 NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-390:amd64  390.116-0ubuntu0.18.04.1    amd64    NVENC Video Encoding runtime library
ii  libnvidia-encode-390:i386 390.116-0ubuntu0.18.04.1    i386 NVENC Video Encoding runtime library
ii  libnvidia-fbc1-390:amd64  390.116-0ubuntu0.18.04.1    amd64    NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-390:i386   390.116-0ubuntu0.18.04.1    i386 NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-390:amd64    390.116-0ubuntu0.18.04.1    amd64    NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-390:i386 390.116-0ubuntu0.18.04.1    i386 NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-390:amd64  390.116-0ubuntu0.18.04.1    amd64    NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-390:i386   390.116-0ubuntu0.18.04.1    i386 NVIDIA OpenGL-based Inband Frame Readback runtime library
rc  nvidia-304  304.132-0ubuntu0.16.04.2    amd64    NVIDIA legacy binary driver - version 304.132
ii  nvidia-367  375.82-0ubuntu3   amd64    Transitional package for nvidia-375
ii  nvidia-375  384.130-0ubuntu0.16.04.1    amd64    Transitional package for nvidia-384
ii  nvidia-384  390.116-0ubuntu0.18.04.1    amd64    Transitional package for nvidia-driver-390
ii  nvidia-compute-utils-390  390.116-0ubuntu0.18.04.1    amd64    NVIDIA compute utilities
rc  nvidia-current  304.132-0ubuntu0.16.04.2    amd64    Transitional package for nvidia-current
ii  nvidia-dkms-390 390.116-0ubuntu0.18.04.1    amd64    NVIDIA DKMS package
ii  nvidia-driver-390 390.116-0ubuntu0.18.04.1    amd64    NVIDIA driver metapackage
ii  nvidia-headless-no-dkms-390 390.116-0ubuntu0.18.04.1    amd64    NVIDIA headless metapackage - no DKMS
ii  nvidia-kernel-common-390  390.116-0ubuntu0.18.04.1    amd64    Shared files used with the kernel module
ii  nvidia-kernel-source-390  390.116-0ubuntu0.18.04.1    amd64    NVIDIA kernel source package
rc  nvidia-opencl-icd-304 304.132-0ubuntu0.16.04.2    amd64    NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-367 375.39-0ubuntu0.16.04.1 amd64    Transitional package for nvidia-opencl-icd-375
rc  nvidia-opencl-icd-384 390.77-0ubuntu0.18.04.1 amd64    Transitional package for nvidia-headless-390
ii  nvidia-prime    0.8.8.2 all  Tools to enable NVIDIA's Prime
ii  nvidia-settings 390.77-0ubuntu0.18.04.1 amd64    Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-390  390.116-0ubuntu0.18.04.1    amd64    NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-390   390.116-0ubuntu0.18.04.1    amd64    NVIDIA binary Xorg driver

```

I rebooted and chose to use an earlier kernel and all worked!

```

[COLOR=#202124][FONT=Roboto]uname -a[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Linux nerone 5.0.0-37-generic #40~18.04.1-Ubuntu SMP Thu Nov 14 12:06:39 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]cat /var/log/gpu-manager.log[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]log_file: /var/log/gpu-manager.log[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]can't access /opt/amdgpu-pro/bin/amdgpu-pro-px[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Looking for nvidia modules in /lib/modules/5.0.0-37-generic/updates/dkms[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Found nvidia module: nvidia-modeset.ko[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Looking for amdgpu modules in /lib/modules/5.0.0-37-generic/updates/dkms[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is nvidia loaded? yes[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Was nvidia unloaded? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is nvidia blacklisted? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is intel loaded? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is radeon loaded? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is radeon blacklisted? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is amdgpu loaded? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is amdgpu blacklisted? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is amdgpu versioned? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is amdgpu pro stack? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is nouveau loaded? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is nouveau blacklisted? yes[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is nvidia kernel module available? yes[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is amdgpu kernel module available? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Vendor/Device Id: 10de:1244[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]BusID "PCI:1@0:0:0"[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Is boot vga? yes[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Skipping "/dev/dri/card0", driven by "nvidia-drm"[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Skipping "/dev/dri/card0", driven by "nvidia-drm"[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Skipping "/dev/dri/card0", driven by "nvidia-drm"[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Skipping "/dev/dri/card0", driven by "nvidia-drm"[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Does it require offloading? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]last cards number = 1[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Has amd? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Has intel? no[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Has nvidia? yes[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]How many cards? 1[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Has the system changed? No[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Single card detected[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Nothing to do[/FONT][/COLOR]

```

So I decided to change my boot options to use the earlier kernel.

Find the boot options available:
```

[COLOR=#202124][FONT=Roboto]sudo grep -Ei 'submenu|menuentry ' /boot/grub/grub.cfg | sed -re "s/(.? )'([^']+)'.*/\1 \2/"[/FONT][/COLOR]

```

[COLOR=#202124][FONT=Roboto]In my case I wanted the "advanced" top-level option (option 1, which immediately follows the default 0 for "ubuntu") and third submenu (ie, option 2)[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]thus I changed the boot default:
[/FONT][/COLOR]```

[COLOR=#202124][FONT=Roboto]sudo nano /etc/default/grub
[/FONT][/COLOR]
```
[COLOR=#202124][FONT=Roboto]from[/FONT][/COLOR]
```

[COLOR=#202124][FONT=Roboto]GRUB_DEFAULT=0[/FONT][/COLOR]

```
[COLOR=#202124][FONT=Roboto]to[/FONT][/COLOR]
```

[COLOR=#202124][FONT=Roboto]GRUB_DEFAULT="1>2"[/FONT][/COLOR]

```
[COLOR=#202124][FONT=Roboto]then [/FONT][/COLOR]
```

[COLOR=#202124][FONT=Roboto]sudo update-grub[/FONT][/COLOR]

```
[COLOR=#202124][FONT=Roboto]finally reboot
[/FONT][/COLOR]
All fine now. Looking forward to further Linux kernel updates that might address the issue.

Or maybe there is a better work-around or fix?

---

### Post by CatKiller on 2020-01-19
The shim between the kernel and the binary blob is specific to each kernel version. If you install the driver through the package manager that shim generally gets automatically rebuilt by DKMS. If you install from elsewhere, such as the file from Nvidia's website, then it doesn't.

Purging all the nvidia stuff and then installing the driver package should cause the shim to be built for the kernels you have installed. I got upgraded to 5.3 the other day and didn't have any problems, but I'm using a newer driver from the PPA.

---

### Post by cedara2 on 2020-01-20
Thanks for that post, I had a similar problem this weekend, as the PC wouldn't recognise the monitor anymore and the profile in the graphical side of nvidia-settings was gone. Via nvidia-settings and Terminal I found that it couldn't find the registry key anymore. To be able to search for a proper solution I purged the nvidia driver (from the packages) and went back to nouveau for now. However, I need the proprietary driver for some games though. At some point, I do have to reinstall them.

---

### Post by CelticWarrior on 2020-01-20
Please open Additional Drivers and install the recommended version as listed there. Do not install using the Nvidia binary or you will having this same problem in each kernel version update.

---

### Post by barbablu on 2020-01-26
Thank you, @CatKiller, about the tip on DKMS.  I had not realised that some code is compiled during the installation of NVidia drives.

I have re-installed the NVidia drives from scratch using the commands:

```

sudo apt --purge autoremove nvidia*
ubuntu-drivers list
sudo apt install nvidia-driver-390

```

The feedback in the terminal showed that the DKMS build worked for the Linux kernel 5.0 and some sanity testing was successful.  Instead the build failed for kernel 5.3 and a log file generated:
/var/crash/nvidia-kernel-source-390.0.crash

```

ProblemType: Package
DKMSBuildLog:
 DKMS make.log for nvidia-390.116 for kernel 5.3.0-26-generic (x86_64)
 Sat 18 Jan 13:03:50 GMT 2020
 make[1]: Entering directory '/usr/src/linux-headers-5.3.0-26-generic'
 test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
 echo >&2;                            \
 echo >&2 "  ERROR: Kernel configuration is invalid.";        \
 echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
 echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
 echo >&2 ;                            \
 /bin/false)

```

Maybe some incompatability between the NVidia drivers and latest Linux in the repo?

My repo sources are:
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ bionic main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ bionic universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic universe
deb http://gb.archive.ubuntu.com/ubuntu/ bionic-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ bionic multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://gb.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
#deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu bionic-security main restricted
deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu quantal partner

```

Maybe the outcome will change with the next Linux/NVidia software update.

---

### Post by CatKiller on 2020-01-26
> **barbablu said:**
> The feedback in the terminal showed that the DKMS build worked for the Linux kernel 5.0 and some sanity testing was successful.  Instead the build failed for kernel 5.3 and a log file generated:

So, we've identified where the problem is. It's disappointing that kind of problem got through. 

I'd recommend trying the [graphics drivers PPA](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa). You can't use newer than the 390 branch with that card, but the PPA has a marginally newer version than the one in the standard repositories (390.129 vs 390.116) and the packaging is done by different people. Their install scripts might be able to handle the change better - I didn't have any problem going from 5.0 to 5.3 with my PPA driver, but mine's the 440 branch.

Otherwise you could wait on the 5.0 kernel till the 5.3 gets an update again that makes it work with the nvidia package from the standard repository; official packages aren't supposed to break each other. Hopefully they won't let that state continue for long.

---

### Post by barbablu on 2020-01-29
Good news: I updated my system a few minutes ago and received NVidia 390 packages that went through the DKMS build fine.  I can now start in full resolution under the latest kernel I have, 5.3!

---

### Post by CatKiller on 2020-01-29
> **barbablu said:**
> Good news: I updated my system a few minutes ago and received NVidia 390 packages that went through the DKMS build fine.  I can now start in full resolution under the latest kernel I have, 5.3!

Awesome :)

---

### Post by aldaran2 on 2020-05-09
Hello everyone,
I had a similar problem after a system upgrade. Nvidia drivers and Xserver login were broken (except for Ubuntu on wayland which does not use the nvidia drivers). The only working combination of nvidia driver and kernel for me was to purge all nvidia drivers, install newest kernel and newest Nvidia driver from ppa.

Working solution:
nvidia-driver-440                               440.82-0ubuntu0~0.18.04.1  
linux-image-5.3.0-51-generic                    5.3.0-51.44~18.04.2

Cheers

---


---
title: "Screen resolution after update"
date: 2020-11-19
forum: Installation &amp; Upgrades
---

### Post by loutchoa on 2020-11-19
Hi everyone,

I just ran an update to Ubuntu 18.04, and now I can only access a 1920x1080 resolution for my external monitor.
It was 2540x1440 before the update. I guess some Nvidia stuffs was the source of the problem, but I am definitely not expert in these things.

Cheers,
François

The update log for today:

```
Start-Date: 2020-11-19  09:07:21
Commandline: /usr/bin/unattended-upgrade
Upgrade: firefox:amd64 (82.0.3+build1-0ubuntu0.18.04.1, 83.0+build2-0ubuntu0.18.04.2)
End-Date: 2020-11-19  09:07:26

Start-Date: 2020-11-19  09:07:28
Commandline: /usr/bin/unattended-upgrade
Upgrade: firefox-locale-en:amd64 (82.0.3+build1-0ubuntu0.18.04.1, 83.0+build2-0ubuntu0.18.04.2)
End-Date: 2020-11-19  09:07:29

Start-Date: 2020-11-19  09:07:31
Commandline: /usr/bin/unattended-upgrade
Upgrade: firefox-locale-fr:amd64 (82.0.3+build1-0ubuntu0.18.04.1, 83.0+build2-0ubuntu0.18.04.2)
End-Date: 2020-11-19  09:07:31

Start-Date: 2020-11-19  09:07:33
Commandline: /usr/bin/unattended-upgrade
Upgrade: krb5-locales:amd64 (1.16-2ubuntu0.1, 1.16-2ubuntu0.2)
End-Date: 2020-11-19  09:07:34

Start-Date: 2020-11-19  09:07:36
Commandline: /usr/bin/unattended-upgrade
Upgrade: libk5crypto3:amd64 (1.16-2ubuntu0.1, 1.16-2ubuntu0.2)
End-Date: 2020-11-19  09:07:37

Start-Date: 2020-11-19  09:07:39
Commandline: /usr/bin/unattended-upgrade
Upgrade: libldap-common:amd64 (2.4.45+dfsg-1ubuntu1.7, 2.4.45+dfsg-1ubuntu1.8)
End-Date: 2020-11-19  09:07:40

Start-Date: 2020-11-19  09:07:42
Commandline: /usr/bin/unattended-upgrade
Upgrade: libpq5:amd64 (10.14-0ubuntu0.18.04.1, 10.15-0ubuntu0.18.04.1)
End-Date: 2020-11-19  09:07:42

Start-Date: 2020-11-19  09:07:44
Commandline: /usr/bin/unattended-upgrade
Upgrade: libvncclient1:amd64 (0.9.11+dfsg-1ubuntu1.3, 0.9.11+dfsg-1ubuntu1.4)
End-Date: 2020-11-19  09:07:45

Start-Date: 2020-11-19  09:07:47
Commandline: /usr/bin/unattended-upgrade
Upgrade: vino:amd64 (3.22.0-3ubuntu1.1, 3.22.0-3ubuntu1.2)
End-Date: 2020-11-19  09:07:48

Start-Date: 2020-11-19  09:07:51
Commandline: /usr/bin/unattended-upgrade
Upgrade: libldap-2.4-2:amd64 (2.4.45+dfsg-1ubuntu1.7, 2.4.45+dfsg-1ubuntu1.8)
End-Date: 2020-11-19  09:07:51

Start-Date: 2020-11-19  09:07:53
Commandline: /usr/bin/unattended-upgrade
Upgrade: chromium-browser:amd64 (86.0.4240.75-0ubuntu0.18.04.1, 86.0.4240.198-0ubuntu0.18.04.1), chromium-codecs-ffmpeg-extra:amd64 (86.0.4240.75-0ubuntu0.18.04.1, 86.0.4240.198-0ubuntu0.18.04.1), chromium-browser-l10n:amd64 (86.0.4240.75-0ubuntu0.18.04.1, 86.0.4240.198-0ubuntu0.18.04.1)
End-Date: 2020-11-19  09:07:59

Start-Date: 2020-11-19  09:08:01
Commandline: /usr/bin/unattended-upgrade
Upgrade: libkrb5-3:amd64 (1.16-2ubuntu0.1, 1.16-2ubuntu0.2), libgssapi-krb5-2:amd64 (1.16-2ubuntu0.1, 1.16-2ubuntu0.2), libkrb5support0:amd64 (1.16-2ubuntu0.1, 1.16-2ubuntu0.2)
End-Date: 2020-11-19  09:08:02

Start-Date: 2020-11-19  09:16:09
Commandline: aptdaemon role='role-commit-packages' sender=':1.166'
Install: libnvidia-compute-455:amd64 (455.38-0ubuntu0.18.04.1, automatic), libnvidia-compute-455:i386 (455.38-0ubuntu0.18.04.1, automatic), libnvidia-encode-455:amd64 (455.38-0ubuntu0.18.04.1, automatic), libnvidia-encode-455:i386 (455.38-0ubuntu0.18.04.1, automatic), nvidia-kernel-common-455:amd64 (455.38-0ubuntu0.18.04.1, automatic), xserver-xorg-video-nvidia-455:amd64 (455.38-0ubuntu0.18.04.1, automatic), libnvidia-gl-455:amd64 (455.38-0ubuntu0.18.04.1, automatic), libnvidia-gl-455:i386 (455.38-0ubuntu0.18.04.1, automatic), libnvidia-fbc1-455:amd64 (455.38-0ubuntu0.18.04.1, automatic), libnvidia-fbc1-455:i386 (455.38-0ubuntu0.18.04.1, automatic), libnvidia-decode-455:amd64 (455.38-0ubuntu0.18.04.1, automatic), libnvidia-decode-455:i386 (455.38-0ubuntu0.18.04.1, automatic), libnvidia-cfg1-455:amd64 (455.38-0ubuntu0.18.04.1, automatic), nvidia-utils-455:amd64 (455.38-0ubuntu0.18.04.1, automatic), nvidia-dkms-455:amd64 (455.38-0ubuntu0.18.04.1, automatic), linux-headers-4.15.0-1102-oem:amd64 (4.15.0-1102.113, automatic), linux-oem-headers-4.15.0-1102:amd64 (4.15.0-1102.113, automatic), linux-image-4.15.0-1102-oem:amd64 (4.15.0-1102.113, automatic), nvidia-compute-utils-455:amd64 (455.38-0ubuntu0.18.04.1, automatic), linux-modules-4.15.0-1102-oem:amd64 (4.15.0-1102.113, automatic), libnvidia-ifr1-455:amd64 (455.38-0ubuntu0.18.04.1, automatic), libnvidia-ifr1-455:i386 (455.38-0ubuntu0.18.04.1, automatic), nvidia-driver-455:amd64 (455.38-0ubuntu0.18.04.1, automatic), libnvidia-common-455:amd64 (455.38-0ubuntu0.18.04.1, automatic), libnvidia-extra-455:amd64 (455.38-0ubuntu0.18.04.1, automatic), nvidia-kernel-source-455:amd64 (455.38-0ubuntu0.18.04.1, automatic)
Upgrade: linux-libc-dev:amd64 (4.15.0-123.126, 4.15.0-124.127), libnvidia-compute-435:amd64 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), libnvidia-compute-435:i386 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), libnvidia-encode-435:amd64 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), libnvidia-encode-435:i386 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), nvidia-kernel-common-435:amd64 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), xserver-xorg-video-nvidia-435:amd64 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), libnvidia-gl-435:amd64 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), libnvidia-gl-435:i386 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), grub-common:amd64 (2.02-2ubuntu8.18, 2.02-2ubuntu8.19), libnvidia-fbc1-435:amd64 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), libnvidia-fbc1-435:i386 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), libnvidia-decode-435:amd64 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), libnvidia-decode-435:i386 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), slack-desktop:amd64 (4.11.0, 4.11.1), google-chrome-stable:amd64 (86.0.4240.193-1, 87.0.4280.66-1), gdb:amd64 (8.1-0ubuntu3.2, 8.1.1-0ubuntu1), grub2-common:amd64 (2.02-2ubuntu8.18, 2.02-2ubuntu8.19), libnvidia-cfg1-435:amd64 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), nvidia-utils-435:amd64 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), nvidia-dkms-435:amd64 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), grub-efi-amd64-bin:amd64 (2.02-2ubuntu8.18, 2.02-2ubuntu8.19), nvidia-compute-utils-435:amd64 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), linux-headers-oem:amd64 (4.15.0.1101.105, 4.15.0.1102.106), libnvidia-ifr1-435:amd64 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), libnvidia-ifr1-435:i386 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), nvidia-driver-435:amd64 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), linux-oem:amd64 (4.15.0.1101.105, 4.15.0.1102.106), grub-efi-amd64:amd64 (2.02-2ubuntu8.18, 2.02-2ubuntu8.19), grub-efi-amd64-signed:amd64 (1.93.20+2.02-2ubuntu8.18, 1.93.21+2.02-2ubuntu8.19), gdbserver:amd64 (8.1-0ubuntu3.2, 8.1.1-0ubuntu1), libnvidia-common-435:amd64 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1), linux-image-oem:amd64 (4.15.0.1101.105, 4.15.0.1102.106), nvidia-kernel-source-435:amd64 (435.21-0ubuntu0.18.04.3, 455.38-0ubuntu0.18.04.1)
End-Date: 2020-11-19  09:19:22
```

---

### Post by TheFu on 2020-11-19
Which GPU?  Is it still supported?

I'm using v430 on my 16.04 desktop with a 1030 GPU.
```
$ dpkg -l|grep nvid
ii  nvidia-430      430.64-0ubuntu0~gpu16.04.6     amd64    NVIDIA binary driver - version 430.64

```
Is the nvidia driver actually loaded and being used?
To check that:
```
$ lsmod |grep nvid
nvidia_uvm            819200  0
nvidia_drm             45056  2
nvidia_modeset       1114112  3 nvidia_drm
nvidia              19046400  84 nvidia_uvm,nvidia_modeset
drm_kms_helper        172032  1 nvidia_drm
drm                   401408  5 drm_kms_helper,nvidia_drm
ipmi_msghandler        53248  2 ipmi_devintf,nvidia
```

To get the correct driver, 
```
sudo ubuntu-drivers autoinstall
```
should handle it for nvidia with Ubuntu LTS releases.

If a GPU driver gets changed, a reboot of the OS is required so the OS can load it.

BTW, whenever posting output from a terminal, please, please, please, use code tags. 
[https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code) explains how.

---

### Post by hk42 on 2020-11-19
I too had a strange behaviour after a reboot for update.
no more GUI only text console.
The solution was to reboot the HDMI TV I use as monitor.
HTH

---

### Post by loutchoa on 2020-11-23
Strangely, on a much higher resolution at home, 
no problem, but here at work, still.


```

$ sudo ubuntu-drivers autoinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

```

Anyways, here are the outputs of dpkg and lsmod
```

$ dpkg -l | grep nvid
ii  libnvidia-cfg1-455:amd64                                         455.38-0ubuntu0.18.04.1                          amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-455                                             455.38-0ubuntu0.18.04.1                          all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-410:amd64                                      410.93-0ubuntu0~18.04.1                          amd64        NVIDIA libcompute package
rc  libnvidia-compute-435:amd64                                      455.38-0ubuntu0.18.04.1                          amd64        Transitional package for libnvidia-compute-455
ii  libnvidia-compute-455:amd64                                      455.38-0ubuntu0.18.04.1                          amd64        NVIDIA libcompute package
ii  libnvidia-compute-455:i386                                       455.38-0ubuntu0.18.04.1                          i386         NVIDIA libcompute package
ii  libnvidia-decode-455:amd64                                       455.38-0ubuntu0.18.04.1                          amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-455:i386                                        455.38-0ubuntu0.18.04.1                          i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-455:amd64                                       455.38-0ubuntu0.18.04.1                          amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-455:i386                                        455.38-0ubuntu0.18.04.1                          i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-455:amd64                                        455.38-0ubuntu0.18.04.1                          amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-455:amd64                                         455.38-0ubuntu0.18.04.1                          amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-455:i386                                          455.38-0ubuntu0.18.04.1                          i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-455:amd64                                           455.38-0ubuntu0.18.04.1                          amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-455:i386                                            455.38-0ubuntu0.18.04.1                          i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-455:amd64                                         455.38-0ubuntu0.18.04.1                          amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-455:i386                                          455.38-0ubuntu0.18.04.1                          i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
rc  nvidia-compute-utils-410                                         410.93-0ubuntu0~18.04.1                          amd64        NVIDIA compute utilities
ii  nvidia-compute-utils-455                                         455.38-0ubuntu0.18.04.1                          amd64        NVIDIA compute utilities
rc  nvidia-dkms-410                                                  410.93-0ubuntu0~18.04.1                          amd64        NVIDIA DKMS package
ii  nvidia-dkms-455                                                  455.38-0ubuntu0.18.04.1                          amd64        NVIDIA DKMS package
ii  nvidia-driver-435                                                455.38-0ubuntu0.18.04.1                          amd64        Transitional package for nvidia-driver-455
ii  nvidia-driver-455                                                455.38-0ubuntu0.18.04.1                          amd64        NVIDIA driver metapackage
rc  nvidia-kernel-common-410                                         410.93-0ubuntu0~18.04.1                          amd64        Shared files used with the kernel module
ii  nvidia-kernel-common-455                                         455.38-0ubuntu0.18.04.1                          amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-455                                         455.38-0ubuntu0.18.04.1                          amd64        NVIDIA kernel source package
ii  nvidia-prime                                                     0.8.8.2                                          all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                                                  440.82-0ubuntu0.18.04.1                          amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-455                                                 455.38-0ubuntu0.18.04.1                          amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-455                                    455.38-0ubuntu0.18.04.1                          amd64        NVIDIA binary Xorg driver
$ lsmod | grep nvid
nvidia_uvm            970752  0
nvidia_drm             49152  5
nvidia_modeset       1216512  8 nvidia_drm
nvidia              27656192  448 nvidia_uvm,nvidia_modeset
drm_kms_helper        172032  2 nvidia_drm,i915
drm                   401408  20 drm_kms_helper,nvidia_drm,i915

```

So still wondering...
(Thanks for the tag reference!)

Cheers,
François

---

### Post by CelticWarrior on 2020-11-23
You have a mix of different Nvidia drivers versions.
That is always bad but if it works do not touch it for the moment.
If it breaks then purge all Nvidia drivers and install only the recommended version for your card.

---

### Post by TheFu on 2020-11-23
```
ii  nvidia-driver-435
ii  nvidia-driver-455
```

Plus there are i915 drivers for the Intel GPU.

As said above, I'd remove all the nvidia drivers
```
sudo apt-get remove --purge nvidia*
```
reboot
then install the recommended one (1) using **ubuntu-drivers**. After that, rebooting again will probably be needed.

Note that I used 'apt-get', not 'apt' for the purge.  apt-get supports wildcards which apt does not.

After the first reboot, a GUI may not happen. Don't worry. Just login (may need to change to a different console (use <cntl>-<alt>-F1 or F3 or F6 ... to find alternate consoles) and run the ubuntu-driver tool

---

### Post by loutchoa on 2020-11-30
Back to university, and no real change. Maybe I did something wrong?

After I ran sudo apt-get remove --purge nvidia* and  and sudo ubuntu-drivers autoinstall,
the result of dpkg and lsmod

```

$ dpkg -l | grep nvid
ii  libnvidia-cfg1-455:amd64                                         455.38-0ubuntu0.18.04.1                          amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-455                                             455.38-0ubuntu0.18.04.1                          all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-410:amd64                                      410.93-0ubuntu0~18.04.1                          amd64        NVIDIA libcompute package
rc  libnvidia-compute-435:amd64                                      455.38-0ubuntu0.18.04.1                          amd64        Transitional package for libnvidia-compute-455
ii  libnvidia-compute-455:amd64                                      455.38-0ubuntu0.18.04.1                          amd64        NVIDIA libcompute package
ii  libnvidia-compute-455:i386                                       455.38-0ubuntu0.18.04.1                          i386         NVIDIA libcompute package
ii  libnvidia-decode-455:amd64                                       455.38-0ubuntu0.18.04.1                          amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-455:i386                                        455.38-0ubuntu0.18.04.1                          i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-455:amd64                                       455.38-0ubuntu0.18.04.1                          amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-455:i386                                        455.38-0ubuntu0.18.04.1                          i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-455:amd64                                        455.38-0ubuntu0.18.04.1                          amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-455:amd64                                         455.38-0ubuntu0.18.04.1                          amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-455:i386                                          455.38-0ubuntu0.18.04.1                          i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-455:amd64                                           455.38-0ubuntu0.18.04.1                          amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-455:i386                                            455.38-0ubuntu0.18.04.1                          i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-455:amd64                                         455.38-0ubuntu0.18.04.1                          amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-455:i386                                          455.38-0ubuntu0.18.04.1                          i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-455                                         455.38-0ubuntu0.18.04.1                          amd64        NVIDIA compute utilities
ii  nvidia-dkms-455                                                  455.38-0ubuntu0.18.04.1                          amd64        NVIDIA DKMS package
ii  nvidia-driver-455                                                455.38-0ubuntu0.18.04.1                          amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-455                                         455.38-0ubuntu0.18.04.1                          amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-455                                         455.38-0ubuntu0.18.04.1                          amd64        NVIDIA kernel source package
ii  nvidia-prime                                                     0.8.8.2                                          all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                                                  440.82-0ubuntu0.18.04.1                          amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-455                                                 455.38-0ubuntu0.18.04.1                          amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-455                                    455.38-0ubuntu0.18.04.1                          amd64        NVIDIA binary Xorg driver

$lsmod |grep nvid
nvidia_uvm            970752  0
nvidia_drm             49152  5
nvidia_modeset       1216512  8 nvidia_drm
nvidia              27656192  430 nvidia_uvm,nvidia_modeset
drm_kms_helper        172032  2 nvidia_drm,i915
drm                   401408  20 drm_kms_helper,nvidia_drm,i915

```

And still unable to change the resolution of my monitor to 2560x1440. Actually not completely true. I tried to change it using nvidia-settings. Kind of work but the result looks terrible.
I also played with gtf and xrandr, not sure I understand how it works. Resolution and rate are from Lenovo's (ThinkVision 20-27 2540x1440)

```

$ gtf 2560 1440 60

  # 2560x1440 @ 60.00 Hz (GTF) hsync: 89.40 kHz; pclk: 311.83 MHz
  Modeline "2560x1440_60.00"  311.83  2560 2744 3024 3488  1440 1441 1444 1490  -HSync +Vsync

$ xrandr --newmode "2560x1440_60.00"  311.83  2560 2744 3024 3488  1440 1441 1444 1490  -HSync +Vsync
$ xrandr --addmode DP-5 "2560x1440_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  66
  Current serial number in output stream:  67

```

Completely stuck...
Any help greatly appreciated:-)
François

---

### Post by loutchoa on 2020-12-19
With the local lockdown, I probably won't need a solution before the new year, but still... Maybe someone could point to  Any better location where I could ask? 

Cheers,
François

---


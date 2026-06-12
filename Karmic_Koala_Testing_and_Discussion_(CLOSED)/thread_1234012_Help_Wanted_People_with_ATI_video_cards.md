---
title: "Help Wanted: People with ATI video cards:"
date: 2009-08-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by castrojo on 2009-08-07
Hi everyone, we need help with people with ATI cards who can test the ppa and report bugs, thanks!

[http://www2.bryceharrington.org:8080/drupal/node/86](http://www2.bryceharrington.org:8080/drupal/node/86)

---

### Post by taavikko on 2009-08-07
Just added ppa
via "sudo add-apt-repository ppa:ubuntu-x-swat/kms"

and now upgrading to test packages :)


STICKY this ;)

---

### Post by BwackNinja on 2009-08-07
Huzzah! Added PPA and upgrading

---

### Post by wayne_cat on 2009-08-07
> **whiprush said:**
> Hi everyone, we need help with people with ATI cards who can test the ppa and report bugs, thanks!

[http://www2.bryceharrington.org:8080/drupal/node/86](http://www2.bryceharrington.org:8080/drupal/node/86)

Do you need somebody with an ATI x1600 Mobility?

```
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
    Subsystem: Apple Computer Inc. Device 0080
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 80000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=256]
    Memory at 98300000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at 98320000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Kernel modules: radeon

```

---

### Post by taavikko on 2009-08-07
Aargh, didn't work for me :(

ATI Technologies Inc Mobility Radeon HD 3400 Series
```
taavikko@hp-dv5:~$ lspci -vn -s 01:00.0
01:00.0 0300: 1002:95c4
	Subsystem: 103c:3600
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 5000 [size=256]
	Memory at d2300000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at d2320000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeon
```

If manually added the radeon.modeset=1
```
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-6-generic root=UUID=cf1ccf97-81be-45f0-a53a-91b66924e9c3 ro quiet splash radeon.modeset=1
[    0.000000] Unknown boot option `radeon.modeset=1': ignoring
```

```
[    7.652550] [drm] radeon default to kernel modesetting.
[    7.652550] [drm] radeon kernel modesetting enabled.
[    7.652550] radeon 0000:01:00.0: power state changed by ACPI to D0
[    7.652550] radeon 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.652550] radeon 0000:01:00.0: setting latency timer to 64
[    7.656560] [drm] radeon: Initializing kernel modesetting.
[    7.656560] [drm:radeon_driver_load_kms] *ERROR* Failed to initialize radeon, disabling IOCTL
[    7.656560] radeon 0000:01:00.0: PCI INT A disabled
[    7.656560] radeon: probe of 0000:01:00.0 failed with error -22
```

If I understood correctly, these have to be reported to LP against kernel with added tags.

---

### Post by BwackNinja on 2009-08-07
To get the kernel you have to install it manually, it doesn't just get upgraded.

---

### Post by taavikko on 2009-08-07
> **BwackNinja said:**
> To get the kernel you have to install it manually, it doesn't just get upgraded.

Yes, you have manually instaal the new kernel.

@wayne_cat I believe this is meant for 600/700 series.

---

### Post by BwackNinja on 2009-08-07
This is kernel modesetting with fun DRI2, so this is for r300-r500 (I don't remember if this includes r100 and r200, I think not).

---

### Post by taavikko on 2009-08-07
> **BwackNinja said:**
> This is kernel modesetting with fun DRI2, so this is for r300-r500 (I don't remember if this includes r100 and r200, I think not).

r{1,2,3,4,5}00 chipsets already have 3D (AFAIK). This was meant for r{6,7}00 cards.
kms is for all ati cards.

---

### Post by wayne_cat on 2009-08-07
> **taavikko said:**
> Yes, you have manually instaal the new kernel.

@wayne_cat I believe this is meant for 600/700 series.

Can you attach the file /var/log/dpkg.log to this thread? I'm not sure if I'm using all
needed packages from the new repository ... tested it on my xorg-edgers system.

I have added the new repository ... removed the xorg-edgers packages ... and installed 

the kernel:

```
root@macbook:~# uname -a
Linux macbook 2.6.31-6-generic #25~radeon2-Ubuntu SMP Thu Aug 6 14:38:48 UTC 2009 i686 GNU/Linux
root@macbook:~# 
```xorg ati and radeon

```
root@macbook:~# dpkg -l |grep git20090805.bd03977e
ii  xserver-xorg-video-ati                         1:6.12.99+git20090805.bd03977e-0ubuntu2    X.Org X server -- ATI display driver wrapper
ii  xserver-xorg-video-radeon                      1:6.12.99+git20090805.bd03977e-0ubuntu2    X.Org X server -- ATI Radeon display driver
root@macbook:~# 
```some libdrm packages

```
root@macbook:~# dpkg -l |grep git20090806.d74c67fb
ii  libdrm-intel1                                  2.4.12+git20090806.d74c67fb-0ubuntu1       Userspace interface to intel-specific kernel
ii  libdrm-radeon1                                 2.4.12+git20090806.d74c67fb-0ubuntu1       Userspace interface to radeon-specific kerne
ii  libdrm2                                        2.4.12+git20090806.d74c67fb-0ubuntu1       Userspace interface to kernel DRM services -
root@macbook:~# 

 
```some mesa packages

```
root@macbook:~# dpkg -l |grep git20090805.ac3de85e
ii  libgl1-mesa-dri                                7.6.0~git20090805.ac3de85e-0ubuntu1        A free implementation of the OpenGL API -- D
ii  libgl1-mesa-glx                                7.6.0~git20090805.ac3de85e-0ubuntu1        A free implementation of the OpenGL API -- G
ii  libglu1-mesa                                   7.6.0~git20090805.ac3de85e-0ubuntu1        The OpenGL utility library (GLU)
ii  mesa-utils                                     7.6.0~git20090805.ac3de85e-0ubuntu1        Miscellaneous Mesa GL utilities
root@macbook:~# 

```I have booted the new kernel with  radeon.modeset=1

Result:

- KMS with 1440x900 resolution
- Gnome +Compiz ... works great
- tested a mp4 video with vlc, xine and totem ... no problems
- no other problems since 22 minutes

---

### Post by taavikko on 2009-08-07
Tried reporting via "ubuntu-bug linux" error, not an genuine ubuntu-package :(

But found a bug, new kernel doesn't try to load /usr/lib/dri/r600_dri.so
It reverts directly to software rasterizer 
"(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so"

But if booting to an older kernel with the upgraded packages,
"(II) AIGLX: Loaded and initialized /usr/lib/dri/r600_dri.so"

No kms/compiz no nada :)

Sorry too much output on the log, so paste a snippet here for you :)
```
2009-08-07 18:32:09 startup archives unpack
2009-08-07 18:32:09 upgrade libdrm2 2.4.12-1ubuntu1 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:09 status half-configured libdrm2 2.4.12-1ubuntu1
2009-08-07 18:32:09 status unpacked libdrm2 2.4.12-1ubuntu1
2009-08-07 18:32:09 status half-installed libdrm2 2.4.12-1ubuntu1
2009-08-07 18:32:09 status half-installed libdrm2 2.4.12-1ubuntu1
2009-08-07 18:32:09 status unpacked libdrm2 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:09 status unpacked libdrm2 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:09 upgrade libdrm-intel1 2.4.12-1ubuntu1 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:09 status half-configured libdrm-intel1 2.4.12-1ubuntu1
2009-08-07 18:32:10 status unpacked libdrm-intel1 2.4.12-1ubuntu1
2009-08-07 18:32:10 status half-installed libdrm-intel1 2.4.12-1ubuntu1
2009-08-07 18:32:10 status half-installed libdrm-intel1 2.4.12-1ubuntu1
2009-08-07 18:32:10 status unpacked libdrm-intel1 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:10 status unpacked libdrm-intel1 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:10 install libdrm-radeon1 <none> 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:10 status half-installed libdrm-radeon1 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:10 status unpacked libdrm-radeon1 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:10 status unpacked libdrm-radeon1 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:10 upgrade libgl1-mesa-dri 7.5-1ubuntu1 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:10 status half-configured libgl1-mesa-dri 7.5-1ubuntu1
2009-08-07 18:32:10 status unpacked libgl1-mesa-dri 7.5-1ubuntu1
2009-08-07 18:32:10 status half-installed libgl1-mesa-dri 7.5-1ubuntu1
2009-08-07 18:32:11 status half-installed libgl1-mesa-dri 7.5-1ubuntu1
2009-08-07 18:32:12 status unpacked libgl1-mesa-dri 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:12 status unpacked libgl1-mesa-dri 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:12 upgrade libgl1-mesa-glx 7.5-1ubuntu1 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:12 status half-configured libgl1-mesa-glx 7.5-1ubuntu1
2009-08-07 18:32:12 status unpacked libgl1-mesa-glx 7.5-1ubuntu1
2009-08-07 18:32:12 status half-installed libgl1-mesa-glx 7.5-1ubuntu1
2009-08-07 18:32:12 status half-installed libgl1-mesa-glx 7.5-1ubuntu1
2009-08-07 18:32:13 status unpacked libgl1-mesa-glx 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:13 status unpacked libgl1-mesa-glx 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:13 upgrade libglu1-mesa 7.5-1ubuntu1 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:13 status half-configured libglu1-mesa 7.5-1ubuntu1
2009-08-07 18:32:13 status unpacked libglu1-mesa 7.5-1ubuntu1
2009-08-07 18:32:13 status half-installed libglu1-mesa 7.5-1ubuntu1
2009-08-07 18:32:13 status half-installed libglu1-mesa 7.5-1ubuntu1
2009-08-07 18:32:13 status unpacked libglu1-mesa 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:13 status unpacked libglu1-mesa 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:13 upgrade linux-libc-dev 2.6.31-5.24 2.6.31-6.25~radeon2
2009-08-07 18:32:13 status half-configured linux-libc-dev 2.6.31-5.24
2009-08-07 18:32:13 status unpacked linux-libc-dev 2.6.31-5.24
2009-08-07 18:32:13 status half-installed linux-libc-dev 2.6.31-5.24
2009-08-07 18:32:14 status half-installed linux-libc-dev 2.6.31-5.24
2009-08-07 18:32:14 status unpacked linux-libc-dev 2.6.31-6.25~radeon2
2009-08-07 18:32:14 status unpacked linux-libc-dev 2.6.31-6.25~radeon2
2009-08-07 18:32:14 upgrade mesa-utils 7.5-1ubuntu1 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:14 status half-configured mesa-utils 7.5-1ubuntu1
2009-08-07 18:32:14 status unpacked mesa-utils 7.5-1ubuntu1
2009-08-07 18:32:14 status half-installed mesa-utils 7.5-1ubuntu1
2009-08-07 18:32:14 status triggers-pending man-db 2.5.5-3
2009-08-07 18:32:14 status half-installed mesa-utils 7.5-1ubuntu1
2009-08-07 18:32:14 status half-installed mesa-utils 7.5-1ubuntu1
2009-08-07 18:32:14 status unpacked mesa-utils 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:14 status unpacked mesa-utils 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:14 upgrade xserver-xorg-video-radeon 1:6.12.99+git20090629.f39cafc5-0ubuntu5 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 18:32:14 status half-configured xserver-xorg-video-radeon 1:6.12.99+git20090629.f39cafc5-0ubuntu5
2009-08-07 18:32:14 status unpacked xserver-xorg-video-radeon 1:6.12.99+git20090629.f39cafc5-0ubuntu5
2009-08-07 18:32:14 status half-installed xserver-xorg-video-radeon 1:6.12.99+git20090629.f39cafc5-0ubuntu5
2009-08-07 18:32:15 status half-installed xserver-xorg-video-radeon 1:6.12.99+git20090629.f39cafc5-0ubuntu5
2009-08-07 18:32:15 status half-installed xserver-xorg-video-radeon 1:6.12.99+git20090629.f39cafc5-0ubuntu5
2009-08-07 18:32:15 status unpacked xserver-xorg-video-radeon 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 18:32:15 status unpacked xserver-xorg-video-radeon 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 18:32:15 upgrade xserver-xorg-video-ati 1:6.12.99+git20090629.f39cafc5-0ubuntu5 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 18:32:15 status half-configured xserver-xorg-video-ati 1:6.12.99+git20090629.f39cafc5-0ubuntu5
2009-08-07 18:32:15 status unpacked xserver-xorg-video-ati 1:6.12.99+git20090629.f39cafc5-0ubuntu5
2009-08-07 18:32:15 status half-installed xserver-xorg-video-ati 1:6.12.99+git20090629.f39cafc5-0ubuntu5
2009-08-07 18:32:15 status half-installed xserver-xorg-video-ati 1:6.12.99+git20090629.f39cafc5-0ubuntu5
2009-08-07 18:32:15 status half-installed xserver-xorg-video-ati 1:6.12.99+git20090629.f39cafc5-0ubuntu5
2009-08-07 18:32:15 status unpacked xserver-xorg-video-ati 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 18:32:15 status unpacked xserver-xorg-video-ati 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 18:32:15 trigproc man-db 2.5.5-3 2.5.5-3
2009-08-07 18:32:15 status half-configured man-db 2.5.5-3
2009-08-07 18:32:16 status installed man-db 2.5.5-3
2009-08-07 18:32:16 startup packages configure
2009-08-07 18:32:16 configure libdrm2 2.4.12+git20090806.d74c67fb-0ubuntu1 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:16 status unpacked libdrm2 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:16 status half-configured libdrm2 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:16 status installed libdrm2 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:16 status triggers-pending libc6 2.10.1-0ubuntu5
2009-08-07 18:32:17 configure libdrm-intel1 2.4.12+git20090806.d74c67fb-0ubuntu1 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:17 status unpacked libdrm-intel1 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:17 status half-configured libdrm-intel1 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:17 status installed libdrm-intel1 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:17 configure libdrm-radeon1 2.4.12+git20090806.d74c67fb-0ubuntu1 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:17 status unpacked libdrm-radeon1 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:17 status half-configured libdrm-radeon1 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:17 status installed libdrm-radeon1 2.4.12+git20090806.d74c67fb-0ubuntu1
2009-08-07 18:32:17 configure libgl1-mesa-dri 7.6.0~git20090805.ac3de85e-0ubuntu1 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:17 status unpacked libgl1-mesa-dri 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:17 status half-configured libgl1-mesa-dri 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:17 status installed libgl1-mesa-dri 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:17 configure libgl1-mesa-glx 7.6.0~git20090805.ac3de85e-0ubuntu1 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:17 status unpacked libgl1-mesa-glx 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:17 status half-configured libgl1-mesa-glx 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:17 status installed libgl1-mesa-glx 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:17 configure libglu1-mesa 7.6.0~git20090805.ac3de85e-0ubuntu1 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:17 status unpacked libglu1-mesa 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:17 status half-configured libglu1-mesa 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:17 status installed libglu1-mesa 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:17 configure linux-libc-dev 2.6.31-6.25~radeon2 2.6.31-6.25~radeon2
2009-08-07 18:32:17 status unpacked linux-libc-dev 2.6.31-6.25~radeon2
2009-08-07 18:32:17 status half-configured linux-libc-dev 2.6.31-6.25~radeon2
2009-08-07 18:32:17 status installed linux-libc-dev 2.6.31-6.25~radeon2
2009-08-07 18:32:17 configure mesa-utils 7.6.0~git20090805.ac3de85e-0ubuntu1 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:17 status unpacked mesa-utils 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:17 status half-configured mesa-utils 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:17 status installed mesa-utils 7.6.0~git20090805.ac3de85e-0ubuntu1
2009-08-07 18:32:17 configure xserver-xorg-video-radeon 1:6.12.99+git20090805.bd03977e-0ubuntu2 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 18:32:17 status unpacked xserver-xorg-video-radeon 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 18:32:17 status half-configured xserver-xorg-video-radeon 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 18:32:17 status installed xserver-xorg-video-radeon 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 18:32:17 configure xserver-xorg-video-ati 1:6.12.99+git20090805.bd03977e-0ubuntu2 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 18:32:17 status unpacked xserver-xorg-video-ati 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 18:32:17 status half-configured xserver-xorg-video-ati 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 18:32:17 status installed xserver-xorg-video-ati 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 18:32:18 trigproc libc6 2.10.1-0ubuntu5 2.10.1-0ubuntu5
2009-08-07 18:32:18 status half-configured libc6 2.10.1-0ubuntu5
2009-08-07 18:32:18 status installed libc6 2.10.1-0ubuntu5
2009-08-07 18:34:36 startup archives unpack
2009-08-07 18:34:37 install linux-image-2.6.31-6-generic <none> 2.6.31-6.25~radeon2
2009-08-07 18:34:37 status half-installed linux-image-2.6.31-6-generic 2.6.31-6.25~radeon2
2009-08-07 18:34:49 status unpacked linux-image-2.6.31-6-generic 2.6.31-6.25~radeon2
2009-08-07 18:34:49 status unpacked linux-image-2.6.31-6-generic 2.6.31-6.25~radeon2
2009-08-07 18:34:50 startup packages configure
2009-08-07 18:34:50 configure linux-image-2.6.31-6-generic 2.6.31-6.25~radeon2 2.6.31-6.25~radeon2
2009-08-07 18:34:50 status unpacked linux-image-2.6.31-6-generic 2.6.31-6.25~radeon2
2009-08-07 18:34:50 status half-configured linux-image-2.6.31-6-generic 2.6.31-6.25~radeon2
2009-08-07 18:35:22 status installed linux-image-2.6.31-6-generic 2.6.31-6.25~radeon2
2009-08-07 18:36:37 startup archives unpack
2009-08-07 18:36:37 install linux-headers-2.6.31-6 <none> 2.6.31-6.25~radeon2
2009-08-07 18:36:37 status half-installed linux-headers-2.6.31-6 2.6.31-6.25~radeon2
2009-08-07 18:36:41 status unpacked linux-headers-2.6.31-6 2.6.31-6.25~radeon2
2009-08-07 18:36:41 status unpacked linux-headers-2.6.31-6 2.6.31-6.25~radeon2
2009-08-07 18:36:41 install linux-headers-2.6.31-6-generic <none> 2.6.31-6.25~radeon2
2009-08-07 18:36:41 status half-installed linux-headers-2.6.31-6-generic 2.6.31-6.25~radeon2
2009-08-07 18:36:43 status unpacked linux-headers-2.6.31-6-generic 2.6.31-6.25~radeon2
2009-08-07 18:36:43 status unpacked linux-headers-2.6.31-6-generic 2.6.31-6.25~radeon2
2009-08-07 18:36:44 startup packages configure
2009-08-07 18:36:44 configure linux-headers-2.6.31-6 2.6.31-6.25~radeon2 2.6.31-6.25~radeon2
2009-08-07 18:36:44 status unpacked linux-headers-2.6.31-6 2.6.31-6.25~radeon2
2009-08-07 18:36:44 status half-configured linux-headers-2.6.31-6 2.6.31-6.25~radeon2
2009-08-07 18:36:44 status installed linux-headers-2.6.31-6 2.6.31-6.25~radeon2
2009-08-07 18:36:44 configure linux-headers-2.6.31-6-generic 2.6.31-6.25~radeon2 2.6.31-6.25~radeon2
2009-08-07 18:36:44 status unpacked linux-headers-2.6.31-6-generic 2.6.31-6.25~radeon2
2009-08-07 18:36:44 status half-configured linux-headers-2.6.31-6-generic 2.6.31-6.25~radeon2
2009-08-07 18:36:44 status installed linux-headers-2.6.31-6-generic 2.6.31-6.25~radeon2
2009-08-07 19:06:42 startup archives unpack
2009-08-07 19:06:58 upgrade xserver-xorg-video-ati 1:6.12.99+git20090805.bd03977e-0ubuntu2 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 19:06:58 status half-configured xserver-xorg-video-ati 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 19:06:58 status unpacked xserver-xorg-video-ati 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 19:06:58 status half-installed xserver-xorg-video-ati 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 19:06:58 status triggers-pending man-db 2.5.5-3
2009-08-07 19:06:58 status half-installed xserver-xorg-video-ati 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 19:06:58 status half-installed xserver-xorg-video-ati 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 19:06:58 status unpacked xserver-xorg-video-ati 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 19:06:58 status unpacked xserver-xorg-video-ati 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 19:06:58 trigproc man-db 2.5.5-3 2.5.5-3
2009-08-07 19:06:58 status half-configured man-db 2.5.5-3
2009-08-07 19:06:59 status installed man-db 2.5.5-3
2009-08-07 19:07:00 startup packages configure
2009-08-07 19:07:00 configure xserver-xorg-video-ati 1:6.12.99+git20090805.bd03977e-0ubuntu2 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 19:07:00 status unpacked xserver-xorg-video-ati 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 19:07:00 status half-configured xserver-xorg-video-ati 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 19:07:00 status installed xserver-xorg-video-ati 1:6.12.99+git20090805.bd03977e-0ubuntu2
2009-08-07 19:59:57 startup archives unpack
2009-08-07 19:59:57 upgrade libnautilus-extension1 1:2.27.4-0ubuntu4 1:2.27.4-0ubuntu5
2009-08-07 19:59:57 status half-configured libnautilus-extension1 1:2.27.4-0ubuntu4
2009-08-07 19:59:57 status unpacked libnautilus-extension1 1:2.27.4-0ubuntu4
2009-08-07 19:59:57 status half-installed libnautilus-extension1 1:2.27.4-0ubuntu4
2009-08-07 19:59:58 status half-installed libnautilus-extension1 1:2.27.4-0ubuntu4
2009-08-07 19:59:58 status unpacked libnautilus-extension1 1:2.27.4-0ubuntu5
2009-08-07 19:59:58 status unpacked libnautilus-extension1 1:2.27.4-0ubuntu5
2009-08-07 19:59:58 upgrade nautilus-data 1:2.27.4-0ubuntu4 1:2.27.4-0ubuntu5
2009-08-07 19:59:58 status half-configured nautilus-data 1:2.27.4-0ubuntu4
2009-08-07 20:00:02 status unpacked nautilus-data 1:2.27.4-0ubuntu4
2009-08-07 20:00:02 status half-installed nautilus-data 1:2.27.4-0ubuntu4
2009-08-07 20:00:02 status triggers-pending hicolor-icon-theme 0.10-2
2009-08-07 20:00:02 status half-installed nautilus-data 1:2.27.4-0ubuntu4
2009-08-07 20:00:02 status triggers-pending shared-mime-info 0.60-2
2009-08-07 20:00:02 status half-installed nautilus-data 1:2.27.4-0ubuntu4
2009-08-07 20:00:02 status half-installed nautilus-data 1:2.27.4-0ubuntu4
2009-08-07 20:00:03 status unpacked nautilus-data 1:2.27.4-0ubuntu5
2009-08-07 20:00:03 status unpacked nautilus-data 1:2.27.4-0ubuntu5
2009-08-07 20:00:03 upgrade nautilus 1:2.27.4-0ubuntu4 1:2.27.4-0ubuntu5
2009-08-07 20:00:03 status half-configured nautilus 1:2.27.4-0ubuntu4
2009-08-07 20:00:03 status unpacked nautilus 1:2.27.4-0ubuntu4
2009-08-07 20:00:03 status half-installed nautilus 1:2.27.4-0ubuntu4
2009-08-07 20:00:03 status triggers-pending man-db 2.5.5-3
2009-08-07 20:00:03 status half-installed nautilus 1:2.27.4-0ubuntu4
2009-08-07 20:00:03 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2009-08-07 20:00:03 status half-installed nautilus 1:2.27.4-0ubuntu4
2009-08-07 20:00:03 status half-installed nautilus 1:2.27.4-0ubuntu4
2009-08-07 20:00:04 status unpacked nautilus 1:2.27.4-0ubuntu5
2009-08-07 20:00:04 status unpacked nautilus 1:2.27.4-0ubuntu5
2009-08-07 20:00:04 upgrade network-manager-gnome 0.7.1.git.3.0461fff8-0ubuntu2 0.8~a~git.20090805t131328.d1edfce-0ubuntu1
2009-08-07 20:00:04 status half-configured network-manager-gnome 0.7.1.git.3.0461fff8-0ubuntu2
2009-08-07 20:00:04 status unpacked network-manager-gnome 0.7.1.git.3.0461fff8-0ubuntu2
2009-08-07 20:00:04 status half-installed network-manager-gnome 0.7.1.git.3.0461fff8-0ubuntu2
2009-08-07 20:00:04 status half-installed network-manager-gnome 0.7.1.git.3.0461fff8-0ubuntu2
2009-08-07 20:00:04 status half-installed network-manager-gnome 0.7.1.git.3.0461fff8-0ubuntu2
2009-08-07 20:00:04 status half-installed network-manager-gnome 0.7.1.git.3.0461fff8-0ubuntu2
2009-08-07 20:00:04 status unpacked network-manager-gnome 0.8~a~git.20090805t131328.d1edfce-0ubuntu1
2009-08-07 20:00:04 status unpacked network-manager-gnome 0.8~a~git.20090805t131328.d1edfce-0ubuntu1
2009-08-07 20:00:04 trigproc hicolor-icon-theme 0.10-2 0.10-2
2009-08-07 20:00:04 status half-configured hicolor-icon-theme 0.10-2
2009-08-07 20:00:08 status installed hicolor-icon-theme 0.10-2
2009-08-07 20:00:08 trigproc shared-mime-info 0.60-2 0.60-2
2009-08-07 20:00:08 status half-configured shared-mime-info 0.60-2
2009-08-07 20:00:09 status installed shared-mime-info 0.60-2
2009-08-07 20:00:09 trigproc man-db 2.5.5-3 2.5.5-3
2009-08-07 20:00:09 status half-configured man-db 2.5.5-3
2009-08-07 20:00:09 status installed man-db 2.5.5-3
2009-08-07 20:00:09 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2009-08-07 20:00:09 status half-configured desktop-file-utils 0.15-2ubuntu1
2009-08-07 20:00:09 status installed desktop-file-utils 0.15-2ubuntu1
2009-08-07 20:00:10 startup packages configure
2009-08-07 20:00:10 configure libnautilus-extension1 1:2.27.4-0ubuntu5 1:2.27.4-0ubuntu5
2009-08-07 20:00:10 status unpacked libnautilus-extension1 1:2.27.4-0ubuntu5
2009-08-07 20:00:10 status half-configured libnautilus-extension1 1:2.27.4-0ubuntu5
2009-08-07 20:00:10 status installed libnautilus-extension1 1:2.27.4-0ubuntu5
2009-08-07 20:00:10 status triggers-pending libc6 2.10.1-0ubuntu5
2009-08-07 20:00:10 configure nautilus-data 1:2.27.4-0ubuntu5 1:2.27.4-0ubuntu5
2009-08-07 20:00:10 status unpacked nautilus-data 1:2.27.4-0ubuntu5
2009-08-07 20:00:10 status half-configured nautilus-data 1:2.27.4-0ubuntu5
2009-08-07 20:00:11 status installed nautilus-data 1:2.27.4-0ubuntu5
2009-08-07 20:00:11 configure nautilus 1:2.27.4-0ubuntu5 1:2.27.4-0ubuntu5
2009-08-07 20:00:11 status unpacked nautilus 1:2.27.4-0ubuntu5
2009-08-07 20:00:11 status half-configured nautilus 1:2.27.4-0ubuntu5
2009-08-07 20:00:11 status installed nautilus 1:2.27.4-0ubuntu5
2009-08-07 20:00:11 configure network-manager-gnome 0.8~a~git.20090805t131328.d1edfce-0ubuntu1 0.8~a~git.20090805t131328.d1edfce-0ubuntu1
2009-08-07 20:00:11 status unpacked network-manager-gnome 0.8~a~git.20090805t131328.d1edfce-0ubuntu1
2009-08-07 20:00:12 status unpacked network-manager-gnome 0.8~a~git.20090805t131328.d1edfce-0ubuntu1
2009-08-07 20:00:12 status unpacked network-manager-gnome 0.8~a~git.20090805t131328.d1edfce-0ubuntu1
2009-08-07 20:00:12 status half-configured network-manager-gnome 0.8~a~git.20090805t131328.d1edfce-0ubuntu1
2009-08-07 20:00:12 status installed network-manager-gnome 0.8~a~git.20090805t131328.d1edfce-0ubuntu1
2009-08-07 20:00:12 trigproc libc6 2.10.1-0ubuntu5 2.10.1-0ubuntu5
2009-08-07 20:00:12 status half-configured libc6 2.10.1-0ubuntu5
2009-08-07 20:00:12 status installed libc6 2.10.1-0ubuntu5

```

---

### Post by wayne_cat on 2009-08-07
> **taavikko said:**
> Tried reporting via "ubuntu-bug linux" error, not an genuine ubuntu-package :(

But found a bug, new kernel doesn't try to load /usr/lib/dri/r600_dri.so
It reverts directly to software rasterizer 
"(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so"

But if booting to an older kernel with the upgraded packages,
"(II) AIGLX: Loaded and initialized /usr/lib/dri/r600_dri.so"

No kms/compiz no nada :)


edit: thank you for the dpkg list ... It seems that we have the same packages on our systems

My card uses a different module :(

```
root@macbook:/var/log# grep AIGLX Xorg.0.log
(==) AIGLX enabled
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
root@macbook:/var/log# 

```maybe your problem is something for the mailing list ... like this:

[http://www.mail-archive.com/ubuntu-x-swat@lists.launchpad.net/msg12585.html](http://www.mail-archive.com/ubuntu-x-swat@lists.launchpad.net/msg12585.html)

---

### Post by descendent87 on 2009-08-07
> **taavikko said:**
> Aargh, didn't work for me :(

ATI Technologies Inc Mobility Radeon HD 3400 Series
```
taavikko@hp-dv5:~$ lspci -vn -s 01:00.0
01:00.0 0300: 1002:95c4
    Subsystem: 103c:3600
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=256]
    Memory at d2300000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at d2320000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeon
```If manually added the radeon.modeset=1
```
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-6-generic root=UUID=cf1ccf97-81be-45f0-a53a-91b66924e9c3 ro quiet splash radeon.modeset=1
[    0.000000] Unknown boot option `radeon.modeset=1': ignoring
``````
[    7.652550] [drm] radeon default to kernel modesetting.
[    7.652550] [drm] radeon kernel modesetting enabled.
[    7.652550] radeon 0000:01:00.0: power state changed by ACPI to D0
[    7.652550] radeon 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.652550] radeon 0000:01:00.0: setting latency timer to 64
[    7.656560] [drm] radeon: Initializing kernel modesetting.
[    7.656560] [drm:radeon_driver_load_kms] *ERROR* Failed to initialize radeon, disabling IOCTL
[    7.656560] radeon 0000:01:00.0: PCI INT A disabled
[    7.656560] radeon: probe of 0000:01:00.0 failed with error -22
```If I understood correctly, these have to be reported to LP against kernel with added tags.

Getting the same errors with a HD3200, have you filed a bug report?
```
ubuntu@ubuntu-desktop:/$ lspci -vn -s 01:05.0
01:05.0 0300: 1002:9610
    Subsystem: 1458:d000
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at ee00 [size=256]
    Memory at fdfe0000 (32-bit, non-prefetchable) [size=64K]
    Memory at fde00000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel modules: radeon
```

---

### Post by MALEADt on 2009-08-07
looking at the blogpost and the ppa, this is for testing a KMS enabled ddx, which only works for <=r500 (kms ready dmr introduced in 2.6.31, staging driver though thus should be enabled manually, hence the kernel in the ppa). r600 and r700 have no drm with kms in any kernel yet (2.6.32 normally).

---

### Post by jerrylamos on 2009-08-07
Using PPA [https://edge.launchpad.net/~apw/+archive/red](https://edge.launchpad.net/~apw/+archive/red) with whatever has been put into it to date is functional on ATI Radeon Mobility 7500 so far.

Do note that video graphics performance has been slowing down steadily since jaunty.  Part of this is no doubt early level karmic with not all of the code installed & running.  DRI? whatever that is.

Using jaunty as base, KMS off, karmic A2 radeon 4% slower, with PPA 30% slower.

With KMS, PPA 41% slower.

GtkPerf from Synaptic measuring video graphics performance on 1.5 mHz P4 on IBM Thinkpad T40 ATI Radeon Mobility 7500

```

GtkPerf0.40,		         jaunty, karmic_A2, A3_PPA_red, A3_PPA_modeset=1	
GtkEntrytime:_____________		0.13	0.04	0.15	0.16	
GtkComboBoxtime:________		1.78	2.76	4.32	4.38	
GtkComboBoxEntrytime:___		1.08	1.56	1.79	1.75	
GtkSpinButtontime:________		0.32	0.77	0.93	0.97	
GtkProgressBartime:_______		0.86	0.71	0.70	0.73	
GtkToggleButtontime:______		0.35	0.66	0.76	0.83	
GtkCheckButtontime:______		0.31	0.28	0.29	0.28	
GtkRadioButtontime:_______		0.60	0.39	0.39	0.39	
GtkTextViewAddtexttime:___		1.29	1.15	1.26	1.50	
GtkTextViewScrolltime:_____		0.51	0.41	0.42	0.47	
GtkDrawingAreaLinestime:__		1.74	1.41	1.99	1.98	
GtkDrawingAreaCirclestime:_		1.34	0.93	1.41	1.98	
GtkDrawingAreaTexttime:___		1.78	1.24	1.20	1.56	
GtkDrawingAreaPixbufstime:		0.44	0.68	0.69	0.70	
	---					
Total_______	time:___________	12.54	13.02	16.30	17.67	
Slower than jaunty:______________   ___          4%      30%     41%

```

Jerry

---

### Post by Slug71 on 2009-08-08
Installed the Kernel but where do i add 'radeon.modeset=1'?

---

### Post by taavikko on 2009-08-08
> **MALEADt said:**
> looking at the blogpost and the ppa, this is for testing a KMS enabled ddx, which only works for <=r500 (kms ready dmr introduced in 2.6.31, staging driver though thus should be enabled manually, hence the kernel in the ppa). r600 and r700 have no drm with kms in any kernel yet (2.6.32 normally).

Take a look for a better explanation than mine,
[http://www.phoronix.com/scan.php?page=news_item&px=NzQyNg](http://www.phoronix.com/scan.php?page=news_item&px=NzQyNg)
Those changes have been pushed on the ppa.

the upgraded packages from the ppa, intorudced the r600_dri.so shared object rather than reverting to software rasterizer on OpenGL

This is running the new kernel with upgraded packages,
```
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.6-devel
OpenGL shading language version string: 1.20

```

This again, older kernel with upgraded packages
```
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RV620 95C4) 20090101  TCL
OpenGL version string: 1.4 Mesa 7.6-devel

```


Slug, append it to the boot stanza in grub.
but that isn't AFAIK necessary, it's been enabled by default.

---

### Post by Slug71 on 2009-08-08
Not sure what i did but now i cannot get into X.

I installed the -6 Kernel, the xorg-video-ati and xorg-video-radeon. Did all from the -5 Kernel. 
Now i cannot get into X on either Kernel. Something about X11.

---

### Post by wayne_cat on 2009-08-08
> **Slug71 said:**
> Not sure what i did but now i cannot get into X.

I installed the -6 Kernel, the xorg-video-ati and xorg-video-radeon. Did all from the -5 Kernel. 
Now i cannot get into X on either Kernel. Something about X11.

```
sudo grep EE /var/log/Xorg.0.log
```

---

### Post by Slug71 on 2009-08-08
> **wayne_cat said:**
> ```
sudo grep EE /var/log/Xorg.0.log
```

Doesnt work, get no such file or directory.

the error i get is 'Could not generate /etc/X11/xorg.conf.failsafe for vesa driver.

---

### Post by taavikko on 2009-08-08
Xorg.0.log (that's a zero in between) doesn't require sudo to be viewed or grep'ped.

Try removing xorg.conf altogether that hardware is automatically detected and adjusted.

---

### Post by BwackNinja on 2009-08-08
@taavikko

on [https://edge.launchpad.net/~ubuntu-x-swat/+archive/kms](https://edge.launchpad.net/~ubuntu-x-swat/+archive/kms) in the mesa package description, it specifically says "Enable r600 driver (Don't expect it to work)" so I doubt the testing is really for r600 yet, and according to [http://www.botchco.com/agd5f/?p=47](http://www.botchco.com/agd5f/?p=47) it isn't the right drm branch for r600 3D to be working.

@Slug71

Disable usplash and it should work

---

### Post by taavikko on 2009-08-08
> **BwackNinja said:**
> @taavikko

on [https://edge.launchpad.net/~ubuntu-x-swat/+archive/kms](https://edge.launchpad.net/~ubuntu-x-swat/+archive/kms) in the mesa package description, it specifically says "Enable r600 driver (Don't expect it to work)" so I doubt the testing is really for r600 yet, and according to [http://www.botchco.com/agd5f/?p=47](http://www.botchco.com/agd5f/?p=47) it isn't the right drm branch for r600 3D to be working.


Didn't expected it to work :) wishful dreaming...
But so it seems that agd5f's commits havent been merged to master branch yet (libdrm)
so let's just wait.

though it seems funny that r600_dri.so is being used when starting with older kernel, and the new kernel doesn't use it it, loads swrast directly.
when it used to check for r66_dri.so if not found, then reverting to swrast.

though, there's no immediate drawback while using the updated packages from ppa, compared to official repo. (except video playback via smplayer (had to change -vo from xv to x11)

---

### Post by Slug71 on 2009-08-08
> **BwackNinja said:**
> @taavikko

@Slug71

Disable usplash and it should work

I have. I installed Plymouth and it removed usplash.

---

### Post by BwackNinja on 2009-08-08
> **Slug71 said:**
> I have. I installed Plymouth and it removed usplash.

Ok then, I'd check if you've got any "vga=0x###" or "vga=###" in your grub line because kms doesn't play nice with framebuffers (it has its own). Otherwise, if it doesn't get to gdm, then I'd check /var/log/gdm/:0.log (you need root privileges to view it).

---

### Post by Slug71 on 2009-08-08
> **wayne_cat said:**
> ```
sudo grep EE /var/log/Xorg.0.log
```

Ok, gives me:

> (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load /usr/lib/xorg/modules/drivers/radeon_drv.so
(EE) Failed to load module "radeon"(loader failed,7)
(EE) No drivers available.

Perhaps it has something to do with that 'xorg-video-radeon' that i installed.

---

### Post by Slug71 on 2009-08-08
> **BwackNinja said:**
> Ok then, I'd check if you've got any "vga=0x###" or "vga=###" in your grub line because kms doesn't play nice with framebuffers (it has its own). Otherwise, if it doesn't get to gdm, then I'd check /var/log/gdm/:0.log (you need root privileges to view it).

Yeh im not getting to gdm, everything is cli.

---

### Post by wayne_cat on 2009-08-08
> **Slug71 said:**
> Ok, gives me:



Perhaps it has something to do with that 'xorg-video-radeon' that i installed.


do you get the same results if you run these 2 commands?

```
root@macbook:~# ls -la /usr/lib/xorg/modules/drivers/radeon_drv.so
-rw-r--r-- 1 root root 944980 2009-08-06 11:44 /usr/lib/xorg/modules/drivers/radeon_drv.so
``````
root@macbook:~# md5sum /usr/lib/xorg/modules/drivers/radeon_drv.so
c366d2720adebff07d4dfaa13541de98  /usr/lib/xorg/modules/drivers/radeon_drv.so
```

---

### Post by taavikko on 2009-08-08
Reported my issue: [https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/410821](https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/410821)

---

### Post by maKA28 on 2009-08-08
> **Slug71 said:**
> Ok, gives me:



Perhaps it has something to do with that 'xorg-video-radeon' that i installed.

I get the exact same issue on a fresh install. Upgraded to 2.6.31-6 kernel and all updates from ppa (xserver-xorg-video-ati,xserver-xorg-video-radeon, libdrm2...)

```
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load /usr/lib/xorg/modules/drivers//radeon_drv.so
(EE) Failed to load module "radeon" (loader failed, 7)
```

hash matches exactly with the previous post.

```
maka@maka-laptop:/usr/lib/xorg/modules/drivers$ md5sum /usr/lib/xorg/modules/drivers/radeon_drv.so
c366d2720adebff07d4dfaa13541de98  /usr/lib/xorg/modules/drivers/radeon_drv.so
```


resolution went down to 1024 x 768, supposed to be 1280 x 800 and compiz doesn't work.

---

### Post by maKA28 on 2009-08-08
> **maKA28 said:**
> I get the exact same issue on a fresh install. Upgraded to 2.6.31-6 kernel and all updates from ppa (xserver-xorg-video-ati,xserver-xorg-video-radeon, libdrm2...)

```
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load /usr/lib/xorg/modules/drivers//radeon_drv.so
(EE) Failed to load module "radeon" (loader failed, 7)
```

hash matches exactly with the previous post.

```
maka@maka-laptop:/usr/lib/xorg/modules/drivers$ md5sum /usr/lib/xorg/modules/drivers/radeon_drv.so
c366d2720adebff07d4dfaa13541de98  /usr/lib/xorg/modules/drivers/radeon_drv.so
```


resolution went down to 1024 x 768, supposed to be 1280 x 800 and compiz doesn't work.

Got it fixed, seemed there were two more updates (libdrm-radeon1 (2.4.12+git20090806.d74c67fb-0ubuntu1), and libgl1-mesa-dri (7.6.0~git20090805.ac3de85e-0ubuntu1)) which I needed to do. Only problem now is compiz not working.

---

### Post by wayne_cat on 2009-08-08
> **maKA28 said:**
> Got it fixed, seemed there were two more updates (libdrm-radeon1 (2.4.12+git20090806.d74c67fb-0ubuntu1), and libgl1-mesa-dri (7.6.0~git20090805.ac3de85e-0ubuntu1)) which I needed to do. Only problem now is compiz not working.

which ATI card do you have?

---

### Post by maKA28 on 2009-08-08
> **wayne_cat said:**
> which ATI card do you have?

ATI X1400 Mobile (Thinkpad T60)

---

### Post by jerrylamos on 2009-08-08
> **Slug71 said:**
> Installed the Kernel but where do i add 'radeon.modeset=1'?
On the initial grub menu, do 
e
then down twice to the line that starts with linux then push the end key
at the end of the line should be quiet splash
add
radeon.modeset=1 
then Ctrl-X to boot.

That's a temporary change.  It would have to be repeated after every boot if you want KMS.  To change it permanently, try in Applications Terminal
sudo gedit /etc/default/grub
then add radeon.modeset=1 just after quiet
save

then do 
sudo update-grub
then reboot....

Good luck, Jerry

---

### Post by maKA28 on 2009-08-08
Ran a couple of benchmark test (tried to mimic what Phoronix did for the intel cards), not very impressed a large drop in performance.

Test machine: Thinkpad T60 
Processor: Intel Core 2 CPU T7200 @ 2.00GHz (Total Cores: 2)
Memory: 2012MB
Graphics: ATI Radeon Mobility X1400 128MB

First bar on all images was the ATI KMS kernel + updates from the ppa, second bar is a clean Alpha 3 install.

[IMG]http://i31.tinypic.com/dw98yh.jpg[/IMG]

[IMG]http://i28.tinypic.com/2jewyet.jpg[/IMG]

[IMG]http://i28.tinypic.com/24qnyj5.jpg[/IMG]

[IMG]http://i26.tinypic.com/20zrard.jpg[/IMG]

[IMG]http://i27.tinypic.com/eriow0.jpg[/IMG]

[IMG]http://i30.tinypic.com/f2ld34.jpg[/IMG]

[IMG]http://i27.tinypic.com/351bar4.jpg[/IMG]

---

### Post by DougieFresh4U on 2009-08-08
Where can I find the .6 kernel? I looked in the kernel ppa-main and didn't see it?
Thanks

---

### Post by wayne_cat on 2009-08-09
> **DougieFresh4U said:**
> Where can I find the .6 kernel? I looked in the kernel ppa-main and didn't see it?
Thanks

[https://edge.launchpad.net/~ubuntu-x-swat/+archive/kms](https://edge.launchpad.net/~ubuntu-x-swat/+archive/kms)

This is not an official kernel ... it is a special build for the KMS tests with ATI card

---

### Post by Slug71 on 2009-08-09
> **maKA28 said:**
> Got it fixed, seemed there were two more updates (libdrm-radeon1 (2.4.12+git20090806.d74c67fb-0ubuntu1), and libgl1-mesa-dri (7.6.0~git20090805.ac3de85e-0ubuntu1)) which I needed to do. Only problem now is compiz not working.

I disabled the PPA before i rebooted though. Is there a way to enable it with in cli now so i can do those other updates?

---

### Post by wayne_cat on 2009-08-09
> **Slug71 said:**
> I disabled the PPA before i rebooted though. Is there a way to enable it with in cli now so i can do those other updates?

do you still have this file in /etc/apt/sources.list.d

```
/etc/apt/sources.list.d# more ubuntu-x-swat-kms-karmic.list
deb http://ppa.launchpad.net/ubuntu-x-swat/kms/ubuntu karmic main

```maybe there is a "#" at the beginning of the line ... remove it to activate the source again

---

### Post by DougieFresh4U on 2009-08-09
> **wayne_cat said:**
> [https://edge.launchpad.net/~ubuntu-x-swat/+archive/kms](https://edge.launchpad.net/~ubuntu-x-swat/+archive/kms)

This is not an official kernel ... it is a special build for the KMS tests with ATI card

Yes, thank you for link. 
I have the ATI Radeon HD3200. Was wondering if there was any love for my graphics.:confused:

---

### Post by taavikko on 2009-08-09
> **DougieFresh4U said:**
> Yes, thank you for link. 
I have the ATI Radeon HD3200. Was wondering if there was any love for my graphics.:confused:

there isnt much for my "hd3450"

---

### Post by Kazade on 2009-08-09
> **DougieFresh4U said:**
> Yes, thank you for link. 
I have the ATI Radeon HD3200. Was wondering if there was any love for my graphics.:confused:

I tried to enable KMS a little while ago and it failed and then killed all acceleration on the HD3200... this chipset always seems cause problems with any new features for some reason (it was one of the last of the R600s to get 2D acceleration too coz it corrupted text all over the place).

---

### Post by Slug71 on 2009-08-09
> **wayne_cat said:**
> do you still have this file in /etc/apt/sources.list.d

```
/etc/apt/sources.list.d# more ubuntu-x-swat-kms-karmic.list
deb http://ppa.launchpad.net/ubuntu-x-swat/kms/ubuntu karmic main

```maybe there is a "#" at the beginning of the line ... remove it to activate the source again

If i put ```
/etc/apt/sources.list.d
``` in terminal i get, > is a directory

---

### Post by taavikko on 2009-08-09
> **Slug71 said:**
> If i put ```
/etc/apt/sources.list.d
``` in terminal i get,

Slug, use
```
sudo add-apt-repository ppa:ubuntu-x-swat/kms
```
this adds the ppa to sources.list.d/ubuntu-x-swat-kms-karmic.list
which then contains
```
deb http://ppa.launchpad.net/ubuntu-x-swat/kms/ubuntu karmic main
```

---

### Post by taavikko on 2009-08-09
> **wayne_cat said:**
> do you still have this file in /etc/apt/sources.list.d

```
/etc/apt/sources.list.d# more ubuntu-x-swat-kms-karmic.list
deb http://ppa.launchpad.net/ubuntu-x-swat/kms/ubuntu karmic main

```maybe there is a "#" at the beginning of the line ... remove it to activate the source again

That's a little confusing since you'r using root which displays # instead of $ and your $PWD is /etc/apt/sources.list.d/ 
and using more command to display the content of a file.

---

### Post by Slug71 on 2009-08-09
> **taavikko said:**
> Slug, use
```
sudo add-apt-repository ppa:ubuntu-x-swat/kms
```
this adds the ppa to sources.list.d/ubuntu-x-swat-kms-karmic.list
which then contains
```
deb http://ppa.launchpad.net/ubuntu-x-swat/kms/ubuntu karmic main
```

@taavikko,

Ive already done that but it doesnt seem to be activating the repo. 

If i run ```
sudo apt-get update
```, i dont see anything from that repo popping up.??

---

### Post by taavikko on 2009-08-09
What does say
```
cat /etc/apt/{sources.list,sources.list.d/ubuntu-x-swat-kms-karmic.list}
```

and what does the ```
sudo aptitude update
```
say.

---

### Post by ranch hand on 2009-08-09
OK, I have 6 versions of 9.10 installed.  I have a Radeon HD 2400 PRO card.  I would be happy to do this.

Someone is going to haveto point me to a guide to installing the kernal.  I tried with another kernal a while back and, believe me, I did not do it right.

I have an OS to burn (clean install A3).  There has got to be a good set of directions for compiling that I have not found.

---

### Post by wayne_cat on 2009-08-09
> **ranch hand said:**
> OK, I have 6 versions of 9.10 installed.  I have a Radeon HD 2400 PRO card.  I would be happy to do this.

Someone is going to haveto point me to a guide to installing the kernal.  I tried with another kernal a while back and, believe me, I did not do it right.

I have an OS to burn (clean install A3).  There has got to be a good set of directions for compiling that I have not found.

Quite simple ... add the repository and then:

```
apt-get install linux-headers-2.6.31-6-generic
apt-get install linux-image-2.6.31-6-generic

```

edit: you have to run "apt-get update" after adding the repository ... the you can install the kernel

---

### Post by ranch hand on 2009-08-09
WELL, that sounds easy enough even for me.

Thanks.

---

### Post by Slug71 on 2009-08-09
> **taavikko said:**
> What does say
```
cat /etc/apt/{sources.list,sources.list.d/ubuntu-x-swat-kms-karmic.list}
```

No such file or directory.

> **taavikko said:**
> and what does the ```
sudo aptitude update
```
say.

Not hitting the 'ubuntu-x-swat/kms' repo.

---

### Post by taavikko on 2009-08-09
> **Slug71 said:**
> No such file or directory.
Not hitting the 'ubuntu-x-swat/kms' repo.

Ok,
```
ls -lR /etc/apt/
```
Also the content of the sources.list would be nice to see if something is in the way.

but let's check the packages too
```
apt-cache policy libdrm2 libgl1-mesa-{dri,glx} xserver-xorg-video-ati
```


Don't put the foil hat too tight, these commands will not give up any information that would discriminate you on anything ;)

---

### Post by ranch hand on 2009-08-09
Slug71

gksudo gedit /etc/apt/sources.list

This sould solve the problem after another apt-get update.

---

### Post by Slug71 on 2009-08-09
> **taavikko said:**
> Ok,
```
ls -lR /etc/apt/
```
Also the content of the sources.list would be nice to see if something is in the way.

/etc/apt/:
apt.conf.d
secring.gpg
sources.list
sources.list.d
trustdb.gpg
trustdb.gpg
trustdb.gpg~

/etc/apt/apt.conf.d:
00trustcdrom
01autoremove
01ubuntu
05aptitude
10periodic
15update-stamp
20archive
20packagekit
50unattended-upgrades
70debconf
99update-notifier

/etc/apt/sources.list.d
ubuntu-x-swat-kms-karmic.list
ubuntu-x-swat-kms-karmic.list.save


> **taavikko said:**
> but let's check the packages too
```
apt-cache policy libdrm2 libgl1-mesa-{dri,glx} xserver-xorg-video-ati
```

libdrm2:
   Installed:2.4.12-1ubuntu1
   Candidate:2.4.12-1ubuntu1
   Version table:
***2.4.12-1ubuntu1 0
      500 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
      100 /var/lib/dpkg/status
xserver-xorg-video-ati
    Installed: 1:6.12.99+git20090805.bd03977e-0ubuntu2
    Candidate: 1:6.12.99+git20090805.bd03977e-0ubuntu2
    Version table:
***1:6.12.99+git20090805.bd03977e-0ubuntu2 0
      100 /var/lib/dpkg/status
   1:6.12.99+git20090629.f39cafc5-0ubuntu5 0
      500 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
W: Unable to locate package libg11-mesa-dri
W: Unable to locate package libg11-mesa-glx

---

### Post by wayne_cat on 2009-08-09
this is what you need from the repository to test KMS on ATI


```
libdrm2                         2.4.12+git20090806.d74c67fb-0ubuntu1
libdrm-intel1                   2.4.12+git20090806.d74c67fb-0ubuntu1
libdrm-radeon1                  2.4.12+git20090806.d74c67fb-0ubuntu1
libgl1-mesa-dri                 7.6.0~git20090805.ac3de85e-0ubuntu1
libgl1-mesa-glx                 7.6.0~git20090805.ac3de85e-0ubuntu1
libglu1-mesa                    7.6.0~git20090805.ac3de85e-0ubuntu1
linux-libc-dev                  2.6.31-6.25~radeon2
mesa-utils                      7.6.0~git20090805.ac3de85e-0ubuntu1
xserver-xorg-video-radeon       1:6.12.99+git20090805.bd03977e-0ubuntu2
xserver-xorg-video-ati          1:6.12.99+git20090805.bd03977e-0ubuntu2
linux-image-2.6.31-6-generic    2.6.31-6.25~radeon2
linux-headers-2.6.31-6          2.6.31-6.25~radeon2
linux-headers-2.6.31-6-generic  2.6.31-6.25~radeon2
```

---

### Post by ranch hand on 2009-08-09
Well, just apt-get installed the sucker, did the upgrades through synaptic.  Going to reboot and see what the damages are.

---

### Post by ranch hand on 2009-08-09
Sucker booted up.

Can't enable effects.

Installed compizconfig-settings-manager, emerald, and compiz-fusion-pluggins-unsupported, in hopes that may make a difference.

Can't enable effects.

Went through the Compiz settings and set some things like the cube business and so forth.  Does nothing.  This is an improvement.

Normally this locks the system up tighter than a bank vault.

This does not bother me because I have seen the results of working compiz and really do not like it.  However we are supposed to be testing.

So, if anyone has a suggestion of what to try next, let me know and I will.  I haven't broken anything today.  Where is the fun in that?

---

### Post by wayne_cat on 2009-08-09
> **ranch hand said:**
> Sucker booted up.

Can't enable effects.

Installed compizconfig-settings-manager, emerald, and compiz-fusion-pluggins-unsupported, in hopes that may make a difference.

Can't enable effects.

Went through the Compiz settings and set some things like the cube business and so forth.  Does nothing.  This is an improvement.

Normally this locks the system up tighter than a bank vault.

This does not bother me because I have seen the results of working compiz and really do not like it.  However we are supposed to be testing.

So, if anyone has a suggestion of what to try next, let me know and I will.  I haven't broken anything today.  Where is the fun in that?

let's start with a simple investigation ... errors in Xorg.0.log?

```
grep EE /var/log/Xorg.0.log
```and your ATI card

```
lspci |grep VGA
```

---

### Post by ranch hand on 2009-08-09
> **wayne_cat said:**
> let's start with a simple investigation ... errors in Xorg.0.log?

```
grep EE /var/log/Xorg.0.log
```and your ATI card

```
lspci |grep VGA
```
```

ken@ken-desktop:~$ grep EE /var/log/Xorg.0.log
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) open /dev/fb0: No such file or directory
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
(EE) RADEON(0): Acceleration initialization failed

```
and
```

ken@ken-desktop:~$ lspci |grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]

```
I should add that I do not have the proprietary driver "activated".  Tried to do that and it acts like it downloads but still claims it isn't activated.  When I scroll the page though it acts weird (ripples - glad I don't get seasick).

---

### Post by plun on 2009-08-09
Compiz-check can be used..

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

I had Metacitys composite enabled which broke Compiz.


```
plun@plun-laptop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc M22 [Mobility Radeon X300]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


```

---

### Post by wayne_cat on 2009-08-09
> **ranch hand said:**
> ```

ken@ken-desktop:~$ grep EE /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) open /dev/fb0: No such file or directory
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
(EE) RADEON(0): Acceleration initialization failed

```and
```

ken@ken-desktop:~$ lspci |grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]

```I should add that I do not have the proprietary driver "activated".  Tried to do that and it acts like it downloads but still claims it isn't activated.  When I scroll the page though it acts weird (ripples - glad I don't get seasick).
 
I think this card is not supported ... there is no xserver-xorg-video-radeonhd in the ppa

---

### Post by ranch hand on 2009-08-09
That has been my experience with this card, not supported.

It does fine on the generic driver.

I will quit banging my head on this thing for something that I really dislike anyway.

It would be nice if i could find a 3D cad for linux that worked.  I do own a pencil though. And paper!

These work better in the Blacksmith shop anyway.  That is usually where you deal with costumer designs.  Better than 3D cad would be people that believed in physics.

---

### Post by jerrylamos on 2009-08-09
Installed PPA according to first comment in this thread on a Compaq Presario 3.33 gHz Celeron with ATI Radeon Xpress 200.

Using GtkPerf video graphics test from Synaptic
Comparing nomodeset 11.44 seconds to modeset=1 was 27.49, well over twice as slow with KMS.

```

GtkPerf0.40Aug0922:05:262009					
karmic.A3.RadeonXpress2001:6.12.99+git20090805.bd03977e-0					
	                	nomodeset	Modeset=1		
GtkEntrytime:____________		0.12	0.11	-8%	
GtkComboBoxtime:________		2.33	5.64	142%	
GtkComboBoxEntrytime:___		1.66	3.25	96%	
GtkSpinButtontime:_______		0.43	1.74	305%	
GtkProgressBartime:______		0.37	3.34	803%	
GtkToggleButtontime:_____		0.45	1.98	340%	
GtkCheckButtontime:______		0.29	0.71	145%	
GtkRadioButtontime:______		0.45	1.03	129%	
GtkTextViewAddtexttime:__		0.84	1.16	38%	
GtkTextViewScrolltime:____		0.45	1.24	176%	
GtkDrawingAreaLinestime:_		1.33	2.07	56%	
GtkDrawingAreaCirclestime:		1.17	2.63	125%	
GtkDrawingAreaTexttime:__		1.33	2.33	75%	
GtkDrawingAreaPixbufstime:		0.21	0.25	19%	
	---				
Total	time:	                    11.44    27.49  140%	 slower

```

That's a bigger slowdown than I saw on Intel i845 and even intel i830.

Should I post a bug on this PPA?

Thanks, Jerry

---

### Post by wayne_cat on 2009-08-09
Not bad ... now look at this :biggrin:

```
                                        Standard                        KMS

GtkEntry - time:                        0,04                            0,07
GtkComboBox - time:                     0,60                            5,04
GtkComboBoxEntry - time:                0,58                            3,71
GtkSpinButton - time:                   0,06                            2,59
GtkProgressBar - time:                  0,02                            5,23
GtkToggleButton - time:                 0,07                            2,94
GtkCheckButton - time:                  0,05                            0,31
GtkRadioButton - time:                  0,12                            1,12
GtkTextView - Add text - time:          0,27                            0,79
GtkTextView - Scroll - time:            0,11                            0,24
GtkDrawingArea - Lines - time:          1,32                            2,24
GtkDrawingArea - Circles - time:        1,25                            3,08
GtkDrawingArea - Text - time:           1,29                            2,52
GtkDrawingArea - Pixbufs - time:        0,24                            0,24
 ---
                                        Total time:  6,04               Total time: 30,12
```

---

### Post by taavikko on 2009-08-10
Aargh, that's not an easy task to downgrade packages...
will test again when/if they pull the adf5g's branch for more support for 600/700 series.

---

### Post by shakaran on 2009-08-10
And the worse result at the moment...

```
$ gtkperf 

(gtkperf:6595): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkperf:6595): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
GtkPerf 0.40 - Starting testing: Mon Aug 10 16:26:02 2009

GtkEntry - time:  0,07
GtkComboBox - time:  6,34
GtkComboBoxEntry - time:  3,87
GtkSpinButton - time:  2,69
GtkProgressBar - time:  3,36
GtkToggleButton - time:  1,43
GtkCheckButton - time:  0,80
GtkRadioButton - time:  1,14
GtkTextView - Add text - time:  2,00
GtkTextView - Scroll - time:  1,73
GtkDrawingArea - Lines - time:  2,60
GtkDrawingArea - Circles - time:  4,04
GtkDrawingArea - Text - time:  4,36
GtkDrawingArea - Pixbufs - time:  0,64
 --- 
Total time: 35,06
```

I filled a couple of bugs for r300.

---

### Post by BwackNinja on 2009-08-10
```

GtkEntry - time:  0.07
GtkComboBox - time:  1.54
GtkComboBoxEntry - time:  1.00
GtkSpinButton - time:  0.54
GtkProgressBar - time:  0.46
GtkToggleButton - time:  0.30
GtkCheckButton - time:  0.27
GtkRadioButton - time:  0.89
GtkTextView - Add text - time:  0.50
GtkTextView - Scroll - time:  0.02
GtkDrawingArea - Lines - time:  4.79
GtkDrawingArea - Circles - time: 12.18
GtkDrawingArea - Text - time:  2.71
GtkDrawingArea - Pixbufs - time:  0.42
 --- 
Total time: 25.69

```

My times really aren't that bad, I just seem to fail at drawing lines and circles...?

---

### Post by jerrylamos on 2009-08-15
karmic A4 CD booted to black screen hang on this Compaq Presario 3.33 gHz Celeron ati radeon Xpress 200.

Managed to get CD up with Driver "vesa", did an install, booted O.K. with "vesa". 

Installed the PPA that's in the first posting in this thread and booted O.K.

Apparently A4 doesn't use ati driver 1:6.12.99+git20090805 which boots O.K.

Jerry

---

### Post by shakaran on 2009-08-18
Wow! Drastically better today!

```
$  gtkperf 

(gtkperf:20884): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkperf:20884): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
GtkPerf 0.40 - Starting testing: Tue Aug 18 14:50:18 2009

GtkEntry - time:  0,08
GtkComboBox - time:  2,66
GtkComboBoxEntry - time:  1,77
GtkSpinButton - time:  0,44
GtkProgressBar - time:  0,37
GtkToggleButton - time:  0,43
GtkCheckButton - time:  0,34
GtkRadioButton - time:  0,39
GtkTextView - Add text - time:  1,97
GtkTextView - Scroll - time:  0,42
GtkDrawingArea - Lines - time:  1,57
GtkDrawingArea - Circles - time:  1,83
GtkDrawingArea - Text - time:  1,56
GtkDrawingArea - Pixbufs - time:  0,19
 --- 
Total time: 14,02
```

---

### Post by plun on 2009-08-18
> **shakaran said:**
> Wow! Drastically better today!

[/CODE]

Yup, new fixed driver yesterday.
[https://lists.ubuntu.com/archives/karmic-changes/2009-August/006499.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/006499.html)

Without Compiz:

```
GtkRadioButton - time:  0.47
GtkTextView - Add text - time:  1.24
GtkTextView - Scroll - time:  0.25
GtkDrawingArea - Lines - time:  2.15
GtkDrawingArea - Circles - time:  1.93
GtkDrawingArea - Text - time:  1.34
GtkDrawingArea - Pixbufs - time:  0.16
 --- 
Total time: 10.77
```

With Compiz

```
GtkRadioButton - time:  0.98
GtkTextView - Add text - time:  4.54
GtkTextView - Scroll - time:  0.75
GtkDrawingArea - Lines - time:  5.52
GtkDrawingArea - Circles - time:  5.49
GtkDrawingArea - Text - time:  3.84
GtkDrawingArea - Pixbufs - time:  0.64
 --- 
Total time: 28.69

```

Dell Laptop X300 graphic chip


--

---

### Post by shakaran on 2009-08-18
Yeah! I am seeing nice work here ;)

---

### Post by Kazade on 2009-08-18
Has anyone had any success with KMS on an HD3200 yet?

I tried to update using the X.org Edgers PPA, but then I couldn't get past the GDM (X kept restarting) and that was without KMS! I've got everything back to the Karmic defaults now, but whenever I try radeon.modeset=1 it:

a.) Doesn't work
b.) Kills all acceleration

I'm dying to see a glimpse of KMS even if it is buggy and slow :(

---

### Post by rv65 on 2009-09-16
I have a Dell Lattiude D610 with a Mobile X300 and it can't access a GUI. If I run GDM the /var/run/dbus/system_bus_socket has no such file or directory. The new GDM seems to have broken it. Any ideas?

---

### Post by Slug71 on 2009-09-17
Should be about time with an updated PPA of the latest Kernel build.

---

### Post by Amaranth on 2009-09-17
> **rv65 said:**
> I have a Dell Lattiude D610 with a Mobile X300 and it can't access a GUI. If I run GDM the /var/run/dbus/system_bus_socket has no such file or directory. The new GDM seems to have broken it. Any ideas?

That is a completely separate problem that has several other threads in this forum that tell you how to fix it.

---

### Post by screaminj3sus on 2009-09-18
Link in OP is down, I have an ati card and am running karmic, what is this PPA for exactly?

---

### Post by chienmort on 2009-09-18
The link seems to have a problem today. :popcorn::popcorn:

---

### Post by Slug71 on 2009-09-18
> **screaminj3sus said:**
> Link in OP is down, I have an ati card and am running karmic, what is this PPA for exactly?

Hopefully its being updated with the latest Kernel? :)

---


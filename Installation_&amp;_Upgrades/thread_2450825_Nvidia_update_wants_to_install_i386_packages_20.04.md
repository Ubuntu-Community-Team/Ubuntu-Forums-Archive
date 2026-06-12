---
title: "Nvidia update wants to install i386 packages 20.04"
date: 2020-09-21
forum: Installation &amp; Upgrades
---

### Post by jejeman on 2020-09-21
I've received update for Nvidia properity driver 450 (440->450), and it wants to install i386 packages, also for X11 packages as well. Looks to me the whole i386 stack is going to be installed.
Kernel update is also arrived.

I don't have any i386 packages installed on my system. I don't understand why it wants to install i386 packages, along amd64. Is this normal?

Here is the list of packages to be installed or upgraded
```
The following NEW packages will be installed:
  gcc-10-base:i386 libatomic1:i386 libbsd0:i386 libc6:i386 libcrypt1:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386 libffi7:i386 libgcc-s1:i386
  libgl1:i386 libgl1-mesa-dri:i386 libglapi-mesa:i386 libglvnd0:i386 libglx-mesa0:i386 libglx0:i386 libidn2-0:i386
  libllvm10:i386 libnvidia-cfg1-450 libnvidia-common-450 libnvidia-compute-450 libnvidia-compute-450:i386 libnvidia-decode-450
  libnvidia-decode-450:i386 libnvidia-encode-450 libnvidia-encode-450:i386 libnvidia-extra-450 libnvidia-fbc1-450
  libnvidia-fbc1-450:i386 libnvidia-gl-450 libnvidia-gl-450:i386 libnvidia-ifr1-450 libnvidia-ifr1-450:i386 libpciaccess0:i386
  libsensors5:i386 libstdc++6:i386 libtinfo6:i386 libunistring2:i386 libvulkan1:i386 libwayland-client0:i386 libx11-6:i386
  libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-randr0:i386
  libxcb-sync1:i386 libxcb1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxshmfence1:i386
  libxxf86vm1:i386 libzstd1:i386 linux-headers-5.4.0-48 linux-headers-5.4.0-48-lowlatency linux-image-5.4.0-48-lowlatency
  linux-modules-5.4.0-48-lowlatency mesa-vulkan-drivers:i386 nvidia-compute-utils-450 nvidia-dkms-450 nvidia-driver-450
  nvidia-kernel-common-450 nvidia-kernel-source-450 nvidia-utils-450 python3-click xserver-xorg-video-nvidia-450 zlib1g:i386
The following packages will be upgraded:
  libnvidia-cfg1-440 libnvidia-common-440 libnvidia-compute-440 libnvidia-decode-440 libnvidia-encode-440 libnvidia-extra-440
  libnvidia-fbc1-440 libnvidia-gl-440 libnvidia-ifr1-440 linux-headers-lowlatency linux-image-lowlatency linux-libc-dev
  linux-lowlatency nvidia-compute-utils-440 nvidia-dkms-440 nvidia-driver-440 nvidia-kernel-common-440
  nvidia-kernel-source-440 nvidia-utils-440 ubuntu-drivers-common xserver-xorg-video-nvidia-440

```

---

### Post by CatKiller on 2020-09-21
You do generally want the 32-bit libraries with the Nvidia driver, yes. Steam and most games are 32-bit, so they need the 32-bit libraries to work.

---

### Post by jejeman on 2020-09-22
If I ever decide to install Steam, I will not mind to install i386 packages.
But, I want to know why all of the sudden update wants to install them?
I have Nvidia driver since I've installed the system, and it didn't needed any 32bit libraries.
Why is Nvidia 450 connected to them? I don't see any other package in this update that would cause this dependency.

---


---
title: "amdgpu failed installation"
date: 2022-01-19
forum: Installation &amp; Upgrades
---

### Post by dominbdg on 2022-01-19
Hello,
I have below issue, I'm using latest Ubuntu 20.4 version and I'm trying to install official amdgpu drivers from AMD website.
I have installed amdgpu-installer and used it as below:

amdgpu-install --opencl=rocr --vulkan=pro --usecase=graphics -y

I'm getting below errors about unmet dependencies:


```
linux-headers-5.13.0-27-generic is already the newest version (5.13.0-27.29~20.04.1).
linux-headers-5.13.0-27-generic set to manually installed.
linux-modules-extra-5.13.0-27-generic is already the newest version (5.13.0-27.29~20.04.1).
linux-modules-extra-5.13.0-27-generic set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 amdgpu-lib : Depends: libwayland-amdgpu-client0 but it is not going to be installed
              Depends: libwayland-amdgpu-server0 but it is not going to be installed
              Depends: libgbm1-amdgpu but it is not going to be installed
              Depends: libegl1-amdgpu-mesa but it is not going to be installed
              Depends: libegl1-amdgpu-mesa-drivers but it is not going to be installed
              Depends: xserver-xorg-amdgpu-video-amdgpu but it is not going to be installed
 amdgpu-lib32 : Depends: libwayland-amdgpu-client0:i386
                Depends: libwayland-amdgpu-server0:i386
                Depends: libgbm1-amdgpu:i386
                Depends: libegl1-amdgpu-mesa:i386
                Depends: libegl1-amdgpu-mesa-drivers:i386
 vulkan-amdgpu-pro : Depends: libwayland-amdgpu-client0 but it is not going to be installed
 vulkan-amdgpu-pro:i386 : Depends: libwayland-amdgpu-client0:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages. 

```

I think that this is related maybe with apt source repositories which I don't have.

Can someone help me with my issue ?

---

### Post by TheFu on 2022-01-19
> **dominbdg said:**
>  
Can someone help me with my issue ?

We don't install GPU drivers downloaded from the vendor in Linux.  That's a Windows thing, not Linux.  We use the drivers available in the repos ... or for AMD, included in the kernel already.  It's a dependency management thing since GPU drivers are tightly coupled to the exact kernel.

---

### Post by QIII on 2022-01-19
If you are running an AMD GPU and you see anything, the kernel module TheFu is talking about is loaded and running.

Would you please post the results of 

```
lsmod | grep amdgpu
```

That should show several lines indicating that the amdgpu module is loaded, somewhat like this:

```
lsmod | grep amdgpu
amdgpu               6008832  211
amd_iommu_v2           20480  1 amdgpu
amd_sched              32768  1 amdgpu
amdttm                 98304  1 amdgpu
amdkcl                 24576  3 amd_sched,amdttm,amdgpu
drm_kms_helper        184320  1 amdgpu
drm                   491520  23 drm_kms_helper,amd_sched,amdttm,amdgpu,amdkcl
i2c_algo_bit           16384  2 igb,amdgpu


```

With AMD, the only time you would need to download anything is if you want the proprietary AMDGPU-PRO overlay, which is rarely needed for most users.

I have AMDGPU-PRO installed, but it is not properly a kernel module, so it doesn't show here.

---


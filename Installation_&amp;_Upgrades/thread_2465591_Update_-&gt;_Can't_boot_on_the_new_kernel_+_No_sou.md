---
title: "Update -&gt; Can't boot on the new kernel + No sound on HDMI output"
date: 2021-08-06
forum: Installation &amp; Upgrades
---

### Post by antoine-even on 2021-08-06
Hello 

It seems i'm not the only one to have problem with the new kernel on ubuntu 20.04 LTS

> **mippi said:**
> I have exactly the same problem. It comes from new kernel and GPU driver....

Yesterday after update & upgrade, I was an unattended-upgrades during the night. 
I did boot one time on the new kernel (5.11 i think) but i had **no sound on the HDMI** output of my GPU (radeaon R7 240 : admgpu driver, not the radeon driver)

I decided to reboot to see if my sound will go back and it was very strange after i reboot, **the system didn't start**. didn't see plymouth or anything, just look like i was frozen.  
At boot now i saw the grub menu and i can boot with the previous kernel and it works perfectly fine. 

What can i do to resolve the problem ?

---

### Post by antoine-even on 2021-08-06
Maybe it can help 

```
Start-Date: 2021-08-03  23:19:34
Commandline: apt upgrade
Requested-By: antoine (1000)
Install: libllvm12:amd64 (1:12.0.0-3ubuntu1~20.04.3, automatic)
Upgrade: libdrm-nouveau2:amd64 (2.4.102-1ubuntu1~20.04.1, 2.4.105-3~20.04.1), xserver-common:amd64 (2:1.20.9-2ubuntu1.2~20.04.2, 2:1.20.11-1ubuntu1~20.04.2), xserver-xorg-core:amd64 (2:1.20.9-2ubuntu1.2~20.04.2, 2:1.20.11-1ubuntu1~20.04.2), libegl-mesa0:amd64 (20.2.6-0ubuntu0.20.04.1, 21.0.3-0ubuntu0.2~20.04.1), libglapi-mesa:amd64 (20.2.6-0ubuntu0.20.04.1, 21.0.3-0ubuntu0.2~20.04.1), xserver-xorg-legacy:amd64 (2:1.20.9-2ubuntu1.2~20.04.2, 2:1.20.11-1ubuntu1~20.04.2), libxatracker2:amd64 (20.2.6-0ubuntu0.20.04.1, 21.0.3-0ubuntu0.2~20.04.1), libgbm1:amd64 (20.2.6-0ubuntu0.20.04.1, 21.0.3-0ubuntu0.2~20.04.1), xserver-xephyr:amd64 (2:1.20.9-2ubuntu1.2~20.04.2, 2:1.20.11-1ubuntu1~20.04.2), libdrm-amdgpu1:amd64 (2.4.102-1ubuntu1~20.04.1, 2.4.105-3~20.04.1), xwayland:amd64 (2:1.20.9-2ubuntu1.2~20.04.2, 2:1.20.11-1ubuntu1~20.04.2), libdrm2:amd64 (2.4.102-1ubuntu1~20.04.1, 2.4.105-3~20.04.1), libgl1-mesa-dri:amd64 (20.2.6-0ubuntu0.20.04.1, 21.0.3-0ubuntu0.2~20.04.1), libdrm-intel1:amd64 (2.4.102-1ubuntu1~20.04.1, 2.4.105-3~20.04.1), libdrm-radeon1:amd64 (2.4.102-1ubuntu1~20.04.1, 2.4.105-3~20.04.1), mesa-vdpau-drivers:amd64 (20.2.6-0ubuntu0.20.04.1, 21.0.3-0ubuntu0.2~20.04.1), mesa-vulkan-drivers:amd64 (20.2.6-0ubuntu0.20.04.1, 21.0.3-0ubuntu0.2~20.04.1), wireless-regdb:amd64 (2020.11.20-0ubuntu1~20.04.1, 2021.07.14-0ubuntu1~20.04.1), mesa-va-drivers:amd64 (20.2.6-0ubuntu0.20.04.1, 21.0.3-0ubuntu0.2~20.04.1), libglx-mesa0:amd64 (20.2.6-0ubuntu0.20.04.1, 21.0.3-0ubuntu0.2~20.04.1), libdrm-common:amd64 (2.4.102-1ubuntu1~20.04.1, 2.4.105-3~20.04.1)
End-Date: 2021-08-03  23:19:46

Start-Date: 2021-08-05  00:16:42
Commandline: /usr/bin/unattended-upgrade
Install: linux-image-5.11.0-25-generic:amd64 (5.11.0-25.27~20.04.1, automatic), linux-modules-extra-5.11.0-25-generic:amd64 (5.11.0-25.27~20.04.1, automatic), linux-modules-5.11.0-25-generic:amd64 (5.11.0-25.27~20.04.1, automatic), linux-headers-5.11.0-25-generic:amd64 (5.11.0-25.27~20.04.1, automatic), linux-hwe-5.11-headers-5.11.0-25:amd64 (5.11.0-25.27~20.04.1, automatic)
Upgrade: linux-headers-generic-hwe-20.04:amd64 (5.8.0.63.71~20.04.45, 5.11.0.25.27~20.04.10), linux-image-generic-hwe-20.04:amd64 (5.8.0.63.71~20.04.45, 5.11.0.25.27~20.04.10), linux-generic-hwe-20.04:amd64 (5.8.0.63.71~20.04.45, 5.11.0.25.27~20.04.10)
End-Date: 2021-08-05  00:17:35

Start-Date: 2021-08-05  22:04:32
Commandline: apt upgrade
Requested-By: antoine (1000)
Upgrade: openvpn:amd64 (2.4.7-1ubuntu2.20.04.2, 2.4.7-1ubuntu2.20.04.3)
End-Date: 2021-08-05  22:04:36


```

GPU
```
Graphics:  Device-1: AMD Oland PRO [Radeon R7 240/340] driver: amdgpu v: kernel 
           Display: x11 server: X.Org 1.20.11 driver: ati,vesa unloaded: fbdev,modesetting,radeon 
           resolution: 1920x1080~60Hz 
           OpenGL: renderer: AMD OLAND (DRM 3.38.0 5.8.0-63-generic LLVM 12.0.0) v: 4.6 Mesa 21.0.3 
```

No Prob with this kernell 
```
Linux ubuntu 5.8.0-63-generic #71~20.04.1-Ubuntu SMP Thu Jul 15 17:46:08 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```

---


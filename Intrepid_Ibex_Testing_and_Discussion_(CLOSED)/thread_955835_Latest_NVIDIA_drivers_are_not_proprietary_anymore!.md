---
title: "Latest NVIDIA drivers are not proprietary anymore!"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by forumache on 2008-10-22
at least this is what System|Administration|Hardware Drivers is telling me: "no proprietary drivers are in use on this system"

ok, atheros wireless is supported now by ath5k instead of madwifi. great, no proprietary drivers here.
but nvidia? nvidia? it's 100% proprietary! And it is in use because I have Desktop Effects activated.

So, my question is: why is nvidia not reported as a proprietary driver? can you check the "Hardware Drivers" to see if nvidia is displayed there?

Thanks!

P.S. Sorry for the eye-catching/misleading title ;)

---

### Post by xak on 2008-10-22
If you have installed the driver from NVIDIA's website or by using Envy they will not be recognized by Ubuntu's Restricted Driver manager.

---

### Post by forumache on 2008-10-22
> **xak said:**
> If you have installed the driver from NVIDIA's website or by using Envy they will not be recognized by Ubuntu's Restricted Driver manager.

I didn't do that.

Although I like to tinker with Linux (my other box is a Gentoo box and my work computer is a CentOS), I use Ubuntu like it was intended (i.e. like a newbie). I want to see the way Ubuntu presents itself to the new Linux users (doing this since Dapper Drake).

So no, the easy answer was not the right one ;)

---

### Post by xak on 2008-10-22
> **forumache said:**
> So no, the easy answer was not the right one ;)

Could you provide us with more information on how to replicate the issue?  Is this on Intrepid?  Beta release?  Daily build?  What are your hardware specs?  What version NVIDIA driver installed?  What type of NVIDIA graphics card?  Could you post the outputs of the following commands:
```
lspci | grep -i vga
```
```
lsmod | grep -i nvidia
```

---

### Post by forumache on 2008-10-22
Thanks xak, I attached here all the info I thought important.
Maybe some other nvidia users can check if on their system jockey shows that nvidia is restricted.

Intrepid, upgraded from Hardy at around Alpha 6, up to date.
AMD64 3500 (in 32bit mode), nVidia 6200

lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

lsmod | grep -i nvidia
nvidia               6900560  36 
agpgart                42184  2 nvidia,amd64_agp
i2c_core               31892  2 nvidia,i2c_nforce2

dan@shuttle:~$ apt-cache policy nvidia-177-kernel-source
nvidia-177-kernel-source:
  Installed: 177.80-0ubuntu2
  Candidate: 177.80-0ubuntu2
  Version table:
 *** 177.80-0ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
        100 /var/lib/dpkg/status

dan@shuttle:~$ apt-cache policy nvidia-glx-177
nvidia-glx-177:
  Installed: 177.80-0ubuntu2
  Candidate: 177.80-0ubuntu2
  Version table:
 *** 177.80-0ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
        100 /var/lib/dpkg/status

dan@shuttle:~$ grep -i nvidia /var/log/Xorg.0.log
(--) PCI:*(0@1:0:0) nVidia Corporation NV44A [GeForce 6200] rev 161, Mem @ 0xfa000000/0, 0xe0000000/0, 0xfb000000/0, BIOS @ 0x????????/131072
(II) Module glx: vendor="NVIDIA Corporation"
(II) NVIDIA GLX Module  177.80  Wed Oct  1 15:06:06 PDT 2008
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
(II) NVIDIA dlloader X Driver  177.80  Wed Oct  1 14:45:01 PDT 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) NVIDIA(0): Creating default Display subsection in Screen section
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "RandRRotation" "True"
(**) NVIDIA(0): Option "DynamicTwinView" "False"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 (NV44) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.a2.03.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:1:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(0): Samsung SyncMaster (DFP-0): 155.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled

---


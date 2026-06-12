---
title: "[HELP] Ubuntu 20.04 nvidia purple screen (Tried Everything)"
date: 2020-09-29
forum: Installation &amp; Upgrades
---

### Post by dazholmes1 on 2020-09-29
So i've installed a fresh copy of ubuntu with rufus my mb is eufi i've disabled secure boot and fast boot ive tried using legacy mode to fix this also my drives are ahci,
so i can install and run ubuntu fine but soon as i install nvidia drivers my ubuntu wont boot it boots into a purple screen and nothing happens i then have to ctrl+alt+f1 and remove nvidia then add nomodeset to grub 
I've literally spent 3 days trying to figure out what's happening and i cant find the fix i've tried every post i've found and none have worked for me! im trying to move onto linux permanently but this has stopped me.

My card is rtx 2080 latest driver version is 450
```

daz@taw:~$ nvidia-smi
Tue Sep 29 21:39:35 2020       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 450.66       Driver Version: 450.66       CUDA Version: 11.0     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  GeForce RTX 2080    Off  | 00000000:01:00.0  On |                  N/A |
| 28%   38C    P8     6W / 215W |    187MiB /  7973MiB |      2%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      1070      G   /usr/lib/xorg/Xorg                 35MiB |
|    0   N/A  N/A      1661      G   /usr/lib/xorg/Xorg                 45MiB |
|    0   N/A  N/A      1864      G   /usr/bin/gnome-shell               87MiB |
+-----------------------------------------------------------------------------+
```


i tried this with secure boot on/off i also added the mok keys after installing!


```
daz@taw:~$ dmesg | grep nvidia
[    0.595212] nvidia-gpu 0000:01:00.3: enabling device (0000 -> 0002)
[    2.646343] nvidia: loading out-of-tree module taints kernel.
[    2.646349] nvidia: module license 'NVIDIA' taints kernel.
[    2.657294] nvidia-nvlink: Nvlink Core is being initialized, major device number 239
[    2.658115] nvidia 0000:01:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=io+mem
[    2.772652] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  450.66  Wed Aug 12 19:37:58 UTC 2020
[    2.775412] [drm] [nvidia-drm] [GPU ID 0x00000100] Loading driver
[    2.775413] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:01:00.0 on minor 0
[    3.008466] audit: type=1400 audit(1601411954.059:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe" pid=865 comm="apparmor_parser"
[    3.008468] audit: type=1400 audit(1601411954.059:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe//kmod" pid=865 comm="apparmor_parser"


```

---

### Post by CelticWarrior on 2020-09-29
Welcome.

How did you install the Nvidia drivers?

---

### Post by dazholmes1 on 2020-09-29
I&#8217;ve tried via terminal also via additional drivers also tried via nvidia website and manually installing I get the same problem either way it&#8217;s either purple screen or a black screen I&#8217;ve looked on google loads who have 2080 card having same issues some managed to fix it but I&#8217;m unsuccessful

ok im not sure if installing the driver directly from nvidia has helped but now i can access nvidia-settings which i couldn't before!

---

### Post by Herman on 2020-10-10
Thanks, this thread helped me. I have an nvidia GeForce GTS 250 graphics card. Since upgrading to 20.04 I have only had one monitor with poor resolution.
Reinstalling the proprietary nvidia driver from 'Additional Drivers' didn't help. I still couldn't access nvidia settings either, it only had a plain empty white dialog box.
Following this thread I have downloaded from nvidia's site, booted into recovery mode from GRUB and installed the nvidia driver and now both monitors are working correctly.

---


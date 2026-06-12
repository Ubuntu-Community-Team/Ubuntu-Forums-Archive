---
title: "NVIDIA GTX 1070 support problems after upgrading to 24.04"
date: 2024-06-01
forum: Installation &amp; Upgrades
---

### Post by ship22 on 2024-06-01
I went through several versions to finally get current with 24.04, and my second monitor stopped working. It worked on prior version and still works on windows so I'm ruling out physical and connection issues, leaving driver support. I tried installing the unbutu drivers for nvidia (nvidia-driver-545 appears to be recommended by the OS) and it fails every time. I tried purging, autoremove, reinstalling about half a dozen times with no success. It fails to configure the driver no matter what I do. 

I tried installing the latest driver package for linux from Nvidia's website (550) and it installed ok and when I reboot, the second monitor activates, just before it displays "Oh no, somewhen when wrong" and the system freezes completely.

Any advice that doesn't appear to be on any webpages I can find to make this go?

---

### Post by ubfan1 on 2024-06-01
There is a problem with the Nvidia 545 and 550 drivers on Ubuntu 22.04.  Try the 535 driver.  The ubuntu-drivers list should offer the 535 and 470.  The graphics-drivers ppa might offer the 545, but the 550 I'd installed from the PPA has now been pulled, and my Software&Updates/additional drivers tab show a "manual install". I'd suggest clean out all Nvidia packages and try the 535 from the standard repos, either ubuntu-drivers or the Additional drivers selection.  The 6.8 kernel needs the gcc-13, so check that you have that too.

---

### Post by ship22 on 2024-06-02
> **ubfan1 said:**
> There is a problem with the Nvidia 545 and 550 drivers on Ubuntu 22.04.  Try the 535 driver.  The ubuntu-drivers list should offer the 535 and 470.  The graphics-drivers ppa might offer the 545, but the 550 I'd installed from the PPA has now been pulled, and my Software&Updates/additional drivers tab show a "manual install". I'd suggest clean out all Nvidia packages and try the 535 from the standard repos, either ubuntu-drivers or the Additional drivers selection.  The 6.8 kernel needs the gcc-13, so check that you have that too.

Thank you very much for the response. I removed 545 and tried purging 550 but I keep getting this error:

2024-06-02T12:28:05.866240-04:00 demon kernel: NVRM: API mismatch: the client has the version 535.154.05, but
2024-06-02T12:28:05.866249-04:00 demon kernel: NVRM: this kernel module has the version 550.78.  Please
2024-06-02T12:28:05.866250-04:00 demon kernel: NVRM: make sure that this kernel module and all NVIDIA driver
2024-06-02T12:28:05.866251-04:00 demon kernel: NVRM: components have the same version.

I tried installing dkms with --force but it didn't seem to resolve this. Any recommendations on how to address this? The system isn't crashing on boot anymore but the second monitor still isn't being detected so I suspect it isn't using the driver at all.

thank you again.

---

### Post by #&amp;thj^% on 2024-06-02
Always best to "first" remove and purge nVidia drivers before installing a new one.
And best to stay within the Repos for drivers and not from Nvidia's site, unless you know the risks.

As far as troubles with nvidia driver 545 or 550, I'm un-aware of any problems with those;
```
 nvidia-smi
Sun Jun  2 11:18:37 2024       
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 550.78                 Driver Version: 550.78         CUDA Version: 12.4     |
|-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce RTX 3050 ...    Off |   00000000:01:00.0  On |                  N/A |
| N/A   31C    P8              4W /   60W |      49MiB /   4096MiB |     22%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+
                                                                                         
+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI        PID   Type   Process name                              GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|    0   N/A  N/A      2111      G   /usr/lib/xorg/Xorg                             45MiB |
+-----------------------------------------------------------------------------------------+

```
I'm currently on Oracular 24.10 and that's not a suggestion to you, but a reference to the stability of the drivers.
At least on my end...

Rant over now, but please show all the below:
```
 dkms status

```
and:
```
 cat /proc/driver/nvidia/version

```
And:
```

cat /sys/module/nvidia/version
```
Finally:
```
 dpkg -l nvidia-*|grep ^ii

```

---

### Post by ship22 on 2024-06-03
dkms status
nvidia/535.154.05, 6.8.0-31-generic, x86_64: installed (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!)

cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  550.78  Sun Apr 14 06:35:45 UTC 2024
GCC version:  gcc version 13.2.0 (Ubuntu 13.2.0-23ubuntu4) 

cat /sys/module/nvidia/version
550.78


dpkg -l nvidia-*|grep ^ii
ii  nvidia-compute-utils-535              535.154.05-0ubuntu1           amd64        NVIDIA compute utilities
ii  nvidia-dkms-535                       535.154.05-0ubuntu1           amd64        NVIDIA DKMS package
ii  nvidia-driver-535                     535.154.05-0ubuntu1           amd64        NVIDIA driver metapackage
ii  nvidia-firmware-535-535.154.05        535.154.05-0ubuntu1           amd64        Firmware files used by the kernel module
ii  nvidia-kernel-common-535              535.154.05-0ubuntu1           amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-535              535.154.05-0ubuntu1           amd64        NVIDIA kernel source package
ii  nvidia-prime                          0.8.17.2                      all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                       510.47.03-0ubuntu4            amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-535                      535.154.05-0ubuntu1           amd64        NVIDIA driver support binaries

One thing looks really odd... does the GTX 1070 have an amd processor? My system is on intel.

cat /proc/cpuinfo 
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 158
model name    : Intel(R) Core(TM) i7-7700K CPU @ 4.20GHz

Thank you again for your help and any tips you might have.

cheers!

---

### Post by ship22 on 2024-06-03
nvidia-smi
Failed to initialize NVML: Driver/library version mismatch
NVML library version: 535.154

lspci|grep -i nvidia
02:00.0 VGA compatible controller: NVIDIA Corporation GP104 [GeForce GTX 1070] (rev a1)
02:00.1 Audio device: NVIDIA Corporation GP104 High Definition Audio Controller (rev a1)

---

### Post by #&amp;thj^% on 2024-06-03
Most of the packages come in named "AMD" it'sjust how they do things.

You still have leftovers from the nVidia.com binary, and that's mucking things up.

This is the problem:
```
cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module 550.78 Sun Apr 14 06:35:45 UTC 2024
GCC version: gcc version 13.2.0 (Ubuntu 13.2.0-23ubuntu4)

cat /sys/module/nvidia/version
550.78

```
Please try a purge all nvidia, and paste that back here to see first.
```
 sudo apt -s autoremove --purge nvidia*

```
This is a dry run only, it will just show what will happen if we remove the safety flag

Before you did anything, you first needed to run this:
```
 sudo bash NVIDIA-Linux-x86_64-XXX.XX.run --uninstall

```
in a 'init3" session

---

### Post by ship22 on 2024-06-03
Yes, agreed. I've tried the purge and removal multiple times and 550.78 refuses to leave. 

when I try the apt purge, it seems like the system doesn't think the 550 drivers are even installed. Running the NVIDIA driver script with --uninstall just returns the message "There are no Nvidia drivers installed"

This is the output from "sudo apt -s autoremove --purge nvidia*" and grepping for 550

Package 'nvidia-firmware-550-server-550.40.07' is not installed, so not removed
Package 'nvidia-firmware-550-server-550.54.14' is not installed, so not removed
Package 'nvidia-firmware-550-server-550.67' is not installed, so not removed
Package 'nvidia-firmware-550-server-550.78' is not installed, so not removed
Package 'nvidia-compute-utils-550' is not installed, so not removed
Package 'nvidia-dkms-550' is not installed, so not removed
Package 'nvidia-kernel-source-550' is not installed, so not removed
Package 'nvidia-kernel-common-550' is not installed, so not removed
Package 'nvidia-firmware-550-550.78' is not installed, so not removed
Package 'nvidia-dkms-550-open' is not installed, so not removed
Package 'nvidia-kernel-source-550-open' is not installed, so not removed
Package 'nvidia-driver-550' is not installed, so not removed
Package 'nvidia-utils-550' is not installed, so not removed
Package 'nvidia-driver-550-open' is not installed, so not removed
Package 'nvidia-firmware-550-550.40.07' is not installed, so not removed
Package 'nvidia-firmware-550-550.54.14' is not installed, so not removed
Package 'nvidia-firmware-550-550.67' is not installed, so not removed
Package 'nvidia-headless-550' is not installed, so not removed
Package 'nvidia-headless-no-dkms-550' is not installed, so not removed
Package 'nvidia-headless-550-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-550-open' is not installed, so not removed

any idea how to put a stake in the heart of 550?

---

### Post by ubfan1 on 2024-06-03
dpkg -l |grep nvidia   and see if any 550 packages are left.  Many start with lib...  and there's xserver and screen packages too.  purge those also, if any are found, hopefully as depencencies they'd be removed, but....

---

### Post by #&amp;thj^% on 2024-06-03
> **ship22 said:**
> 
any idea how to put a stake in the heart of 550?
Not yet, with our normal checks>> nothing shows any "550" 
```
dpkg -l nvidia-*|grep ^ii
ii nvidia-compute-utils-535 535.154.05-0ubuntu1 amd64 NVIDIA compute utilities
ii nvidia-dkms-535 535.154.05-0ubuntu1 amd64 NVIDIA DKMS package
ii nvidia-driver-535 535.154.05-0ubuntu1 amd64 NVIDIA driver metapackage
ii nvidia-firmware-535-535.154.05 535.154.05-0ubuntu1 amd64 Firmware files used by the kernel module
ii nvidia-kernel-common-535 535.154.05-0ubuntu1 amd64 Shared files used with the kernel module
ii nvidia-kernel-source-535 535.154.05-0ubuntu1 amd64 NVIDIA kernel source package
ii nvidia-prime 0.8.17.2 all Tools to enable NVIDIA's Prime
ii nvidia-settings 510.47.03-0ubuntu4 amd64 Tool for configuring the NVIDIA graphics driver
ii nvidia-utils-535 535.154.05-0ubuntu1 amd64 NVIDIA driver support binaries

```
I'll have to try to recreate what you have on your hands now.
BTW: Have you checked in 
```
cd  /etc/X11 && ls
```
Mine looks like below:
```
app-defaults             xinit                              Xsession
cursors                  xkb                                Xsession.d
default-display-manager  xorg.conf.d                        Xsession.options
fonts                    xorg.conf.nvidia-xconfig-original  xsm
ja_JP.eucJP              Xreset                             XvMCConfig
ja_JP.UTF-8              Xreset.d                           Xwrapper.config
rgb.txt                  Xresources

```
And I use a lot of newer drivers as well, then back to older version for comparisons.

---


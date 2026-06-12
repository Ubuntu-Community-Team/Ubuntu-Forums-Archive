---
title: "NVIDIA driver installed by fails to load"
date: 2019-02-13
forum: Installation &amp; Upgrades
---

### Post by utah777 on 2019-02-13
I am having problems with NVIDIA driver after system upgrade. On Ubuntu 14.04 machine with GeForce G 105M video card I have NVIDIA driver installed but it seems to fail to load. Some additional information:


```

18:58:14 ~$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                               0.7-2ubuntu1                                         amd64        Interface for toggling the power on nVidia Optimus video cards
ii  nvidia-340                                                  340.107-0ubuntu0~gpu14.04.1                          amd64        NVIDIA binary driver - version 340.107
ii  nvidia-opencl-icd-340                                       340.107-0ubuntu0~gpu14.04.1                          amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                                0.6.2.1                                              amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             415.27-0ubuntu0~gpu14.04.1                           amd64        Tool for configuring the NVIDIA graphics driver

```

```
18:48:32 ~$ lsmod | grep nouveau
18:49:18 ~$ lsmod | grep nvidia
18:49:34 ~$ 

```


```
18:50:18 ~$ inxi -G
Graphics:  Card: NVIDIA G98M [GeForce G 105M] X.Org: 1.15.1 drivers: fbdev,vesa,nouveau Resolution: 1280x720@0.0hz 
           GLX Renderer: N/A GLX Version: N/A

```

```
18:50:24 ~$ nvidia-settings


ERROR: Unable to load info from any available system

```

```
18:54:05 ~$ glxgears
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't get an RGB, Double-buffered visual

```

```
18:54:31 ~$ cat /var/log/Xorg.0.log | grep nvidia
[     7.319] (II) LoadModule: "nvidia"
[     7.326] (WW) Warning, couldn't open module nvidia
[     7.326] (II) UnloadModule: "nvidia"
[     7.326] (II) Unloading nvidia
[     7.326] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     7.326] (==) Matched nvidia as autoconfigured driver 0
[     7.326] (II) LoadModule: "nvidia"
[     7.327] (WW) Warning, couldn't open module nvidia
[     7.327] (II) UnloadModule: "nvidia"
[     7.327] (II) Unloading nvidia
[     7.327] (EE) Failed to load module "nvidia" (module does not exist, 0)

19:12:48 ~$ cat /var/log/Xorg.0.log | grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     7.441] Initializing built-in extension MIT-SCREEN-SAVER
[     7.568] (EE) NVIDIA: Failed to initialize the NVIDIA kernel module. Please see the
[     7.568] (EE) NVIDIA:     system's kernel log for additional error messages and
[     7.568] (EE) NVIDIA:     consult the NVIDIA README for details.
[     7.569] (EE) No devices detected.
[     7.587] (EE) NVIDIA: Failed to initialize the NVIDIA kernel module. Please see the
[     7.587] (EE) NVIDIA:     system's kernel log for additional error messages and
[     7.587] (EE) NVIDIA:     consult the NVIDIA README for details.
[     7.587] (EE) [drm] KMS not enabled
[     7.587] (EE) open /dev/dri/card0: No such file or directory
[     7.588] (EE) open /dev/dri/card0: No such file or directory
[     7.588] (EE) open /dev/fb0: No such file or directory
[     7.589] (EE) open /dev/fb0: No such file or directory
[     7.589] (EE) Screen 0 deleted because of no matching config section.
[     7.589] (EE) Screen 0 deleted because of no matching config section.
[     8.511] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)


```

What I have tried so far:

Ctrl-Alt-F1

```
sudo service lightdm stop
sudo apt-get purge nvidia*
sudo reboot now

sudo apt-get install nvidia-340 nvidia-settings
sudo nvidia-xconfig
sudo update-initramfs -u
sudo reboot now
```

That did not work (see the outputs above)
Any help on loading NVIDIA driver is highly appreciated!

---

### Post by him610 on 2019-02-13
Did you try installing from Settings>Additional Drivers?
It will usually display available alternatives, including Nvidia drivers, that can be installed.

---

### Post by utah777 on 2019-02-13
> **him610 said:**
> Did you try installing from Settings>Additional Drivers?
It will usually display available alternatives, including Nvidia drivers, that can be installed.


I tried 

```
07:41:37 ~$ sudo ubuntu-drivers devices
[sudo] password for sergey: 
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
vendor   : NVIDIA Corporation
modalias : pci:v000010DEd000006F1sv00001043sd00001AB2bc03sc00i00
model    : G98M [GeForce G 105M]
driver   : nvidia-340 - third-party free recommended
driver   : nvidia-304 - third-party free
driver   : xserver-xorg-video-nouveau - distro free builtin


07:42:15 ~$ sudo ubuntu-drivers autoinstall

```

Results are the same

---

### Post by him610 on 2019-02-15
This what my ubuntu-drivers devices looks like:
```

sudo ubuntu-drivers devices
[sudo] password for hugh: 
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001187sv00001462sd00002848bc03sc00i00
vendor   : NVIDIA Corporation
model    : GK104 [GeForce GTX 760]
driver   : nvidia-driver-390 - distro non-free recommended
driver   : nvidia-340 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

```

The nvidia drivers listed here are non-free while yours are third-party free

---

### Post by utah777 on 2019-02-16
Do you mean possible solution to the problem is having non-free drivers?
How do I enable them, just in case, because I don't have any?

```

20:32:31 ~$ sudo ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
model    : G98M [GeForce G 105M]
modalias : pci:v000010DEd000006F1sv00001043sd00001AB2bc03sc00i00
vendor   : NVIDIA Corporation
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-340 - third-party free recommended
driver   : nvidia-304 - third-party free

```

---

### Post by CatKiller on 2019-02-16
The drivers from the PPA get described as open source. They aren't.

I wouldn't run nvidia-xconfig.

If it were mine, I'd purge all the nvidia stuff, remove anything that's been created in /etc/X11 and try again.

Look in the output from the install to see if there are any problems. Apparently 340 is the last version to support that device.

---

### Post by utah777 on 2019-02-16
> **CatKiller said:**
> The drivers from the PPA get described as open source. They aren't.

I wouldn't run nvidia-xconfig.

If it were mine, I'd purge all the nvidia stuff, remove anything that's been created in /etc/X11 and try again.

Look in the output from the install to see if there are any problems. Apparently 340 is the last version to support that device.

1. Removed /etc/X11/xorg.conf
```
21:43:38 ~$ ls /etc/X11/
app-defaults                      fluxbox  xinit             Xresources        Xwrapper.config
core                              fonts    xkb               Xsession
cursors                           openbox  xorg.conf.backup  Xsession.d
default-display-manager           rgb.txt  Xreset            Xsession.options
default-display-manager.dpkg-tmp  X        Xreset.d          xsm

```

2. Purged anything related to NVIDIA
3. Rebooted
4. Reinstalled NVIDIA 340 without running `nvidia-xconfig`, no installation errors
5. Rebooted

Still no luck.

---

### Post by CatKiller on 2019-02-16
OK, that seems to be a good place to start from. It's a shame it didn't put up any errors to give us a clue about where it failed.

IIRC, what the install script should have done, and what the driver needs, is to have the nvidia kernel module loaded in the initramfs and conflicting modules blacklisted. I'm typing on my phone, so I can't check the exact list or location, but I'm sure you can find it or someone else can chime in. You'll want to make sure those have been done. You can also try modprobe nvidia to see if it loads OK or gives a useful error message.

I've never used any of the mobile nvidia GPUs, but my impression is that they can be somewhat temperamental.

---

### Post by utah777 on 2019-02-16
> **CatKiller said:**
> OK, that seems to be a good place to start from. It's a shame it didn't put up any errors to give us a clue about where it failed.

IIRC, what the install script should have done, and what the driver needs, is to have the nvidia kernel module loaded in the initramfs and conflicting modules blacklisted. I'm typing on my phone, so I can't check the exact list or location, but I'm sure you can find it or someone else can chime in. You'll want to make sure those have been done. You can also try modprobe nvidia to see if it loads OK or gives a useful error message.

I've never used any of the mobile nvidia GPUs, but my impression is that they can be somewhat temperamental.

Per your suggestion:


```
22:45:56 ~$ sudo modprobe nvidia
modprobe: ERROR: could not insert 'nvidia_340': Exec format error

```

Just in case, I want to remind, the root of the problem is system upgrade. Everything worked fine, including NVIDIA drivers, until the latest upgrade. I rolled the kernel back since then, but it did not help.

---

### Post by jeremy31 on 2019-02-16
Exec format error, post results for ```
modinfo nvidia
```

---

### Post by utah777 on 2019-02-16
> **jeremy31 said:**
> Exec format error, post results for ```
modinfo nvidia
```


```
22:54:08 ~$ sudo modinfo nvidia
modinfo: ERROR: Module nvidia not found.



```

---

### Post by jeremy31 on 2019-02-16
Lets try ```
modinfo nvidia_340
```

---

### Post by utah777 on 2019-02-16
> **jeremy31 said:**
> Lets try ```
modinfo nvidia_340
```

```

23:03:11 ~$ sudo modinfo nvidia_340
filename:       /lib/modules/3.13.0-161-generic/updates/dkms/nvidia_340.ko
alias:          char-major-195-*
version:        340.107
supported:      external
license:        NVIDIA
alias:          pci:v000010DEd00000E00sv*sd*bc04sc80i00*
alias:          pci:v000010DEd00000AA3sv*sd*bc0Bsc40i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        drm
vermagic:       3.13.0-161-generic SMP mod_unload modversions 
parm:           NVreg_Mobile:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_RemapLimit:int
parm:           NVreg_UpdateMemoryTypes:int
parm:           NVreg_InitializeSystemMemoryAllocations:int
parm:           NVreg_UsePageAttributeTable:int
parm:           NVreg_MapRegistersEarly:int
parm:           NVreg_RegisterForACPIEvents:int
parm:           NVreg_CheckPCIConfigSpace:int
parm:           NVreg_EnablePCIeGen3:int
parm:           NVreg_EnableMSI:int
parm:           NVreg_MemoryPoolSize:int
parm:           NVreg_RegistryDwords:charp
parm:           NVreg_RmMsg:charp
parm:           NVreg_AssignGpus:charp



```

---

### Post by jeremy31 on 2019-02-16
Check ```
dmesg | grep nvidia
```
Hopefully it will show the reason for exec format error

---

### Post by utah777 on 2019-02-16
> **jeremy31 said:**
> Check ```
dmesg | grep nvidia
```
Hopefully it will show the reason for exec format error

```

23:13:13 ~$ sudo dmesg | grep nvidia
[    2.923582] nvidia: version magic '3.13.0-161-generic SMP mod_unload modversions ' should be '3.13.0-161-generic SMP mod_unload modversions retpoline '
[    5.057740] nvidia: version magic '3.13.0-161-generic SMP mod_unload modversions ' should be '3.13.0-161-generic SMP mod_unload modversions retpoline '
[ 3908.171413] nvidia: version magic '3.13.0-161-generic SMP mod_unload modversions ' should be '3.13.0-161-generic SMP mod_unload modversions retpoline '
[ 3927.282364] nvidia: version magic '3.13.0-161-generic SMP mod_unload modversions ' should be '3.13.0-161-generic SMP mod_unload modversions retpoline '

```

---

### Post by jeremy31 on 2019-02-16
Do you have all updates installed?

---

### Post by utah777 on 2019-02-16
> **jeremy31 said:**
> Do you have all updates installed?

I ran:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

which caused me the problem.

After that I downgraded the kernel to 3.13.0-161 and ran after all the installs and reinstalls:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by utah777 on 2019-02-16
it seems to be related to the outdated gcc compiler issue identified by this thread 

[https://bugs.launchpad.net/ubuntu/+source/gcc-4.8/+bug/1750937](https://bugs.launchpad.net/ubuntu/+source/gcc-4.8/+bug/1750937)

The key to understanding this was running:

```

23:13:13 ~$ sudo dmesg | grep nvidia
[    2.923582] nvidia: version magic '3.13.0-161-generic SMP mod_unload modversions ' should be '3.13.0-161-generic SMP mod_unload modversions retpoline '
[    5.057740] nvidia: version magic '3.13.0-161-generic SMP mod_unload modversions ' should be '3.13.0-161-generic SMP mod_unload modversions retpoline '
[ 3908.171413] nvidia: version magic '3.13.0-161-generic SMP mod_unload modversions ' should be '3.13.0-161-generic SMP mod_unload modversions retpoline '
[ 3927.282364] nvidia: version magic '3.13.0-161-generic SMP mod_unload modversions ' should be '3.13.0-161-generic SMP mod_unload modversions retpoline '

```


The solution was upgrading gcc to version 5 and reinstalling NVIDIA drivers after that.

Thanks all for giving a helping hand!!!

---


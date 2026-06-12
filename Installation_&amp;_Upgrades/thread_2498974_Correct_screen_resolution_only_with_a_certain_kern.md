---
title: "Correct screen resolution only with a certain kernel"
date: 2024-07-06
forum: Installation &amp; Upgrades
---

### Post by alfredino on 2024-07-06
Hi

I have an IdeaPad 5G-14Q8X05 with SoC Snapdragon 8cx gen 2 with [limited ubuntu-linux support]("https://bugzilla.kernel.org/show_bug.cgi?id=218512"). However, I was able to install ubuntu arm 24.04 and mate desktop. All worked well with the following kernel:

```
6.8.0-11-generic #11-Ubuntu SMP PREEMPT_DYNAMIC Wed Feb 14 02:53:31 UTC 2024 aarch64 aarch64 aarch64 GNU/Linux

```

```
xrandr 
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 1920 x 1200
Virtual-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00 +
   1920x1080     60.00* 
   1600x1200     60.00  
   1680x1050     59.95    59.88  
   1400x1050     59.98    59.95  
   1600x900      60.00  
   1280x1024     60.02  
   1440x900      59.89    59.90  
   1280x960      60.00  
   1366x768      59.79    60.00  
   1360x768      60.02  
   1280x800      59.81    59.91  
   1280x768      59.87    59.99  
   1280x720      60.00  
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94 

```

After upgrading the kernel with ```
apt-get install --install-recommends linux-generic-hwe-24.04

```

```
6.8.0-36-generic #36-Ubuntu SMP PREEMPT_DYNAMIC Mon Jun 10 13:20:23 UTC 2024 aarch64 aarch64 aarch64 GNU/Linux

apt list --installed | grep linux-image


WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


linux-image-6.8.0-11-generic/now 6.8.0-11.11 arm64 [installed,local]
linux-image-6.8.0-36-generic/noble-updates,noble-security,now 6.8.0-36.36 arm64 [installed,automatic]
linux-image-generic-hwe-24.04/noble-updates,noble-security,now 6.8.0-36.36 arm64 [installed,automatic]

```

I have a screen resolution problem:

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected primary 1024x768+0+0 0mm x 0mm
       1024x768       0.00* 

```
The session is x11
```
loginctl show-session c2 -p Type
Type=x11

```and there are no additional drivers to install

```
sudo ubuntu-drivers install
All the available drivers are already installed.

```
Do you have any suggestions?
Thank you

---

### Post by currentshaft on 2024-07-06
You didn't "upgrade" the kernel, you installed Hardware Enablement Kernel (HWE).

Why did you run "apt-get install --install-recommends linux-generic-hwe-24.04"? What problem were you trying to solve?

---

### Post by alfredino on 2024-07-07
> **currentshaft said:**
> You didn't "upgrade" the kernel, you installed Hardware Enablement Kernel (HWE).

Why did you run "apt-get install --install-recommends linux-generic-hwe-24.04"? What problem were you trying to solve?

Since the kernel is old (February 2024), I tried installing a newer version. From the [official documentation]("https://ubuntu.com/kernel/lifecycle"):
[I]The Ubuntu LTS enablement, or Hardware Enablement (HWE), stack provides the **newer kernel** and X11 display support for existing Ubuntu LTS releases. That stack can be enabled manually, but may also be pre-enabled with an Ubuntu LTS release.

[/I]I can go back to the [standard kernel]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") with:```
[COLOR=#333333][FONT=monospace]sudo apt install --install-recommends linux-generic[/FONT][/COLOR]
```[COLOR=#333333][FONT=monospace] 

[/FONT][/COLOR]What do you suggest to do?
Thank you

P.S.
I went back with the above command, however the 6.8.0-36-generic kernel still has problems
```
dpkg --list | egrep -i --color 'linux-image|linux-headers|linux-modules' | awk '{ print $2 }'
linux-headers-6.8.0-11
linux-headers-6.8.0-11-generic
linux-headers-6.8.0-36
linux-headers-6.8.0-36-generic
linux-headers-generic
linux-image-6.8.0-11-generic
linux-image-6.8.0-36-generic
linux-image-generic
linux-modules-6.8.0-11-generic
linux-modules-6.8.0-36-generic
linux-modules-extra-6.8.0-11-generic
linux-modules-extra-6.8.0-36-generic
```

---


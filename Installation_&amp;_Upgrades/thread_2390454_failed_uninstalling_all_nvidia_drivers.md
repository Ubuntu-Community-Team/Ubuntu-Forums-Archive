---
title: "failed uninstalling all nvidia drivers"
date: 2018-04-29
forum: Installation &amp; Upgrades
---

### Post by shome on 2018-04-29
My system: ubuntu 1604 64 bit, i7, titan x, multiboot with 14.04 and windows

I need to reinstall nvidia drivers on 16.04. I had unsuccessfully tried to install various versions of nvidia drivers from 384, 390, 396. 

So I tried to remove existing nvidia installation using :

```
sudo ap-get remove --purge nvidia-*. 
```

However when I search I found many nvidia files in /. How do I remove them. Is it safe to remove all of them?


```
./etc/apparmor.d/abstractions/nvidia
./lib/firmware/nvidia
./lib/modules/4.4.0-109-generic/kernel/drivers/video/fbdev/nvidia
./lib/modules/4.4.0-109-generic/kernel/drivers/video/fbdev/nvidia/nvidiafb.ko
./lib/modules/4.4.0-109-generic/kernel/drivers/net/ethernet/nvidia
./lib/modules/4.4.0-47-generic/kernel/drivers/video/fbdev/nvidia
./lib/modules/4.4.0-47-generic/kernel/drivers/video/fbdev/nvidia/nvidiafb.ko
./lib/modules/4.4.0-47-generic/kernel/drivers/net/ethernet/nvidia
./lib/modules/4.4.0-121-generic/kernel/drivers/video/fbdev/nvidia
./lib/modules/4.4.0-121-generic/kernel/drivers/video/fbdev/nvidia/nvidiafb.ko
./lib/modules/4.4.0-121-generic/kernel/drivers/net/ethernet/nvidia
./var/lib/app-info/icons/ubuntu-xenial-main/64x64/nvidia-settings_nvidia-settings.png
./usr/local/share/OpenCV/samples/gpu/opticalflow_nvidia_api.cpp
./usr/local/share/OpenCV/samples/gpu/cascadeclassifier_nvidia_api.cpp
./usr/src/linux-headers-4.4.0-121/drivers/video/fbdev/nvidia
./usr/src/linux-headers-4.4.0-121/drivers/net/ethernet/nvidia
./usr/src/linux-headers-4.4.0-47/drivers/video/fbdev/nvidia
./usr/src/linux-headers-4.4.0-47/drivers/net/ethernet/nvidia
./usr/src/linux-headers-4.4.0-109/drivers/video/fbdev/nvidia
./usr/src/linux-headers-4.4.0-109/drivers/net/ethernet/nvidia
./usr/src/linux-headers-4.4.0-109-generic/include/config/net/vendor/nvidia.h
./usr/src/linux-headers-4.4.0-109-generic/include/config/fb/nvidia.h
./usr/src/linux-headers-4.4.0-109-generic/include/config/fb/nvidia
./usr/src/linux-headers-4.4.0-47-generic/include/config/net/vendor/nvidia.h
./usr/src/linux-headers-4.4.0-47-generic/include/config/fb/nvidia.h
./usr/src/linux-headers-4.4.0-47-generic/include/config/fb/nvidia
./usr/src/linux-headers-4.4.0-121-generic/include/config/net/vendor/nvidia.h
./usr/src/linux-headers-4.4.0-121-generic/include/config/fb/nvidia.h
./usr/src/linux-headers-4.4.0-121-generic/include/config/fb/nvidia
./usr/lib/python3/dist-packages/NvidiaDetector/__pycache__/nvidiadetector.cpython-35.pyc
./usr/lib/python3/dist-packages/NvidiaDetector/nvidiadetector.py
./usr/lib/nvidia-367
./usr/lib/nvidia-367/libnvidia-fbc.so.1
./usr/lib/nvidia-367/libnvidia-wfb.so.1
./usr/lib/nvidia
./usr/lib/x86_64-linux-gnu/dri/nvidia_drv_video.so
./usr/lib/x86_64-linux-gnu/directfb-1.2-9/gfxdrivers/libdirectfb_nvidia.so
./usr/bin/nvidia-detector
./usr/lib32/nvidia-367
./usr/lib32/nvidia-367/libnvidia-fbc.so.1
./usr/lib32/nvidia-367/libnvidia-wfb.so.1
./usr/share/doc/linux-firmware/licenses/LICENCE.nvidia.gz
./usr/share/screen-resolution-extra/nvidia-polkit.py
./usr/share/screen-resolution-extra/nvidia-prime.py
./usr/share/apport/package-hooks/source_nvidia-graphics-drivers-352.py
./usr/share/apport/package-hooks/source_nvidia-graphics-drivers-352-updates.py
./usr/share/apport/package-hooks/source_nvidia-graphics-drivers-304-updates.py
./usr/share/apport/package-hooks/source_nvidia-graphics-drivers-340-updates.py
./usr/share/apport/package-hooks/source_nvidia-graphics-drivers-304.py
./usr/share/apport/package-hooks/source_nvidia-graphics-drivers-340.py
./usr/share/app-install/desktop/nvidia-driver-185.desktop
./usr/share/app-install/desktop/nvidia-driver-173.desktop
./usr/share/app-install/desktop/nvidia-settings:nvidia-settings.desktop
./usr/share/app-install/desktop/nvidia-driver-96.desktop
./usr/share/app-install/icons/nvidia-settings.png

```

---

### Post by skyproud on 2018-04-29
Hello, have you executed your commands in the recovery mode when uninstalling nvidia drivers? You may enter the recovery mode in the grub menu.

---

### Post by oldfred on 2018-04-29
It looks like you need to purge old kernels. Run this without the -s after testing it with the -s.
 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image
-s is simulate so you can see what it will do, then run without -s
sudo apt-get -s autoremove 

      
 nVidia Must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

### Post by shome on 2018-04-30
Thanks oldfred for replying i have been struggling for nearly two days now.

To begin with I was facing the ubuntu login loop problem. So I need to reinstall nvidia drivers. I have uninstalled the existing drivers using your method as below: I removed old kernels using sudo apt-get autoremove before uninstalling the nvidia driver

sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Then I try to install nvidia-390(it supports linux 64bits (mine is ubuntu 16.04,64bit) and gtx titanx)

I use :sudo apt-get install nvidia-390

But it gets back login loop. I tried all suggestions from various forms. [COLOR=#000000][FONT=amp]I have tried with multiple drivers: 384, 390, 396. I keep getting the same message. [/FONT][/COLOR]The results from various command are as below: Some which seemed to be important are marked in bold 

cat .xsession-errors:
**Xlib: extension "GLX" missing onn display ":0"**
Xlib: extension "GLX" missing onn display ":0"
**OpenConnection:connect:No such file or directory**

Output of dpkg -l | grep glx:

libgl1-mesa-glx:amd64
libgl1-mesa-glx:i386
libswt-glx-gtk-3-jni
libxcb-glx0:amd64
libxcb-glx0:i386
libxcb-glx0-dev:amd64

                        [COLOR=#000000][FONT=amp]lspci -vk | grep -iA15 vga|grep Kernel gives:

**Kernel modules: nvidiafb, nouveau, nvidia-390,nvidia-390-drm**

However nouveau is blacklisted in /etc/modprobe.d/blacklist.conf

There is another file generated by nvidia called "**nvidia-graphics-drivers.conf**" which blacklists
nouveau, lbm--[COLOR=#000000][FONT=amp]nouveau, nvidia-current[/FONT][/COLOR], nvidia-173,nvidia-96, nvidia-current-updates, [/FONT][/COLOR][COLOR=#000000][FONT=amp]nvidia-173-updates, [COLOR=#000000][FONT=amp]nvidia-96-updates,[/FONT][/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=amp]nvidia-390-updates,
It sets options nvidia_390_drv modeset=0


[COLOR=#000000][FONT=amp]Output of 
lsmod | egrep -i 'nvidia|nouveau|video'[/FONT][/COLOR]: 
video 40960 0

[/FONT][/COLOR][COLOR=#000000][FONT=amp]sudo lshw -n -c video gives:

*-display UNCLAIMED
description: VGA compatible controller
vendor NVIDIA corporation [10E]
...
configuartion: latency=0[/FONT][/COLOR]

---

### Post by oldfred on 2018-04-30
Not familar with Titan nVidia card.
Is it this? Which worked. 
[https://www.phoronix.com/scan.php?page=article&item=nvidia-titan-x&num=1](https://www.phoronix.com/scan.php?page=article&item=nvidia-titan-x&num=1)

This shows newest driver should be correct for Titan.
[https://www.geforce.com/drivers](https://www.geforce.com/drivers)

If you add ppa, you get the very newest drivers also.

 #What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia 

 # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 

 Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices

If you do install a new driver, be sure to purge again before hand.

---

### Post by shome on 2018-04-30
the titan x card is as shown in [https://www.phoronix.com/scan.php?pa...-titan-x&num=1]("https://www.phoronix.com/scan.php?page=article&item=nvidia-titan-x&num=1")

the drivers 390,396, 384 all support the titanx card as shown in nvidia drivers: supported devices

dpkg -l | grep -i nvidia gives:

bbswitch-dkms
libcuda1-390
nvidia-390 : 390.48
nvidia-opencl-icd-390
nvidia-prime
nvidia-settings

dkms status gives:

bbswitch,0.8,4.4.0-122-generic, x86_64: installed
nvidia-390,390.48,4.4.0-122-generic,x86_64:installed

lsmod | grep nvidia  gave no ouput

ls -la .Xauthority

-rw------ 1 user user .Xauthority

ls -la .Iceauthority

-rw------ 1 user user .Iceauthority


the ppa is already added which suggested three drivers: 396, 390,384: I tried all three after purging the previous one(sudo apt-get remove --purge)
But all of them gave in xsession.errors :
**Xlib: extension "GLX" missing onn display ":0"**

---

### Post by oldfred on 2018-04-30
I am confused on bbswitch. I thought that was just for bumblebee and laptops with switchable graphics. And newer nVidia did not need bumblebee.

I have before suggested removing that, but it kept getting installed, so did not seem to solve issue.
But I might try removing it.

 sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms 


I have this in my notes from at least a couple of years ago.

 Bumblebee may not be required with nVidia Optimus which is installed automatically with newest nVidia driver.
Bumblebee has been depreciated in favor of nvidia-prime
Bumblebee - allows both nVidia & Intel to be used, nVidia Prime was just nVidia, but now updated:

---

### Post by shome on 2018-05-02
I tried reinstalling nvidia.

Then I tried sudo dpkg-reconfigure nvidia-90 to regnerate ko filesas advised in [https://devtalk.nvidia.com/default/topic/996318/ubuntu-16-04-stuck-in-login-loop-after-attempting-to-install-nvidia-linux-x86_64-375-39-run/](https://devtalk.nvidia.com/default/topic/996318/ubuntu-16-04-stuck-in-login-loop-after-attempting-to-install-nvidia-linux-x86_64-375-39-run/)
It still says that : extension "GLX" missing pn display 0

---

### Post by oldfred on 2018-05-02
Do not know that error.
One fix for a laptop user was to add bumblebee, which I thought now was not used.
Another had two video cards and no UEFI/BIOS setting to control which was in use.
Check that monitor cable is correct.

       #What is installed
dkms status

---


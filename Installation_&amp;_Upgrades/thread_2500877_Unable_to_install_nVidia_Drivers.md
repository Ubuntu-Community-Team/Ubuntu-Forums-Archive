---
title: "Unable to install nVidia Drivers"
date: 2024-09-14
forum: Installation &amp; Upgrades
---

### Post by prasanedirisinghe on 2024-09-14
It has been noted that my machine stuck middle of the work and uninstalled **nouveau **standard drivers thinking I should install nvidia compatible drivers for my graphic card gforce 550 ti. I tried installing different nvidia versions 525 , 470 , 390 but im not getting the drivers intalled. and im using ubuntu pro

sudo bash -c "echo 'blacklist nouveau' > /etc/modprobe.d/blacklist-nouveau.conf"
sudo bash -c "echo 'options nouveau modeset=0' >> /etc/modprobe.d/blacklist-nouveau.conf"


sudo update-initramfs -u


sudo lshw -c video | grep 'configuration'

configuration: latency=0       configuration: driver=i915 latency=0       configuration: depth=32 resolution=1024,768

lspci | grep -i nvidia
01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF116 High Definition Audio Controller (rev a1)



sudo apt install nvidia-driver-<version>


nvidia-smi
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.

---

### Post by Bashing-om on 2024-09-14
Hello asanedirisinghe - Welcome to the Forums :D

As a 1st step please post back - between code tags to maintain the formatting - the output of terminal command:
```

dpkg -l | grep -i nvidia

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

see here what there is to do.

[INDENT]All in the process
[/INDENT]

---

### Post by prasanedirisinghe on 2024-09-16
```
HD3:~$ dpkg -l | grep -i nvidia
rc  libnvidia-compute-390:amd64                    390.157-0ubuntu7                         amd64        NVIDIA libcompute package
rc  libnvidia-compute-390:i386                     390.157-0ubuntu7                         i386         NVIDIA libcompute package
ii  libnvidia-compute-470:amd64                    470.256.02-0ubuntu0.24.04.1              amd64        NVIDIA libcompute package
ii  libnvidia-compute-470:i386                     470.256.02-0ubuntu0.24.04.1              i386         NVIDIA libcompute package
rc  libnvidia-gl-470:amd64                         470.256.02-0ubuntu0.24.04.1              amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
rc  libnvidia-gl-470:i386                          470.256.02-0ubuntu0.24.04.1              i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD



```

---

### Post by prasanedirisinghe on 2024-09-16
My machine stuck at least few times a day, if I uninstall **nouveau** drivers machine doesnt stuck. help me to find the suitable drivers as I tried many versions

---

### Post by Bashing-om on 2024-09-16
prasanedirisinghe - Ouch

That card takes the 390 version driver:
[https://www.nvidia.com/en-us/drivers/details/196213/](https://www.nvidia.com/en-us/drivers/details/196213/)

Unfortunately no longer supported in the latest release.
And Nvida no longer supports the 390 version driver:
[https://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases](https://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases)

What release are you running ?
Older releases still have the driver (UN-supported)

[INDENT]all good things come to an end
[/INDENT]

---


---
title: "Can't upgrade nvidia driver"
date: 2017-09-29
forum: Installation &amp; Upgrades
---

### Post by geomcd1949 on 2017-09-29
Trying to upgrade nvidia driver from 381.22 to 384.90 using Software & Updates > Additional Drivers. When I click the radio button for the 384.90 driver, then click Apply Changes, nothing happens for a few seconds, then the radio button for 381.22 becomes the lit button, then nothing happens.

16.04.03 LTS

Also, when using Software Updater, I cannot change the "Download from:" location in Ubuntu Software. I highlight a different server but it does not appear in the block -- the existing server remains there.

---

### Post by Bashing-om on 2017-09-29
geomcd1949; hello -

The 384 version driver is not in the standard software repository.

Now to not help in breaking your system - why do you think the 384 driver is of value to you ?

IF we are to continue to pursue installing 384; please show us the hardware we are working with:
```

lspci -k|grep -iEA5 'vga|3d'

```

As yes, there is a way to install the 384 version driver in xenial .

[INDENT][INDENT]maybe yes
[INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by geomcd1949 on 2017-09-29
I'm an old man who aspires to be an Ubuntu snob with the latest and best.

 lspci -k|grep -iEA5 'vga|3d'
01:00.0 VGA compatible controller: NVIDIA Corporation GK104GL [Quadro K4200] (rev a1)
    Subsystem: NVIDIA Corporation GK104GL [Quadro K4200]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_381, nvidia_381_drm
01:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)
    Subsystem: NVIDIA Corporation GK104 HDMI Audio Controller

Actually, I use Lightworks for video editing and the benchmark numbers I get are lower than Windows users with roughly comparable equipment, and the standard response of LWKS Forum is to make sure to use the latest drivers.

Thanks!

---

### Post by Bashing-om on 2017-09-29
geomcd1949; Yepper :)

confirmed you want that 384 driver:
[http://www.nvidia.com/download/driverResults.aspx/123918/en-us](http://www.nvidia.com/download/driverResults.aspx/123918/en-us)

so you get that driver from our PPA:
```

sudo apt purge nvidia*
sudo rm /etc/X11/Xorg.conf ##in the event that this file does exist
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo ubuntu-drivers autoinstall
sudo apt full-upgrade
sudo reboot

```
Where I do expect the system to choose and install the 384 version driver .

Once up from the reboot confirm the driver installed:
```

dpkg -l | grep -i nvidia

```


[INDENT][INDENT]all better now
[/INDENT][/INDENT]

---

### Post by geomcd1949 on 2017-09-29
dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                   0.8-3ubuntu1                                             amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcg:amd64                                     3.1.0013-2                                               amd64        Nvidia Cg core runtime library
ii  libcggl:amd64                                   3.1.0013-2                                               amd64        Nvidia Cg Opengl runtime library
ii  libcuda1-384                                    384.90-0ubuntu0~gpu16.04.1                               amd64        NVIDIA CUDA runtime library
ii  nvidia-384                                      384.90-0ubuntu0~gpu16.04.1                               amd64        NVIDIA binary driver - version 384.90
ii  nvidia-opencl-icd-384                           384.90-0ubuntu0~gpu16.04.1                               amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                    0.8.2                                                    amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                 384.90-0ubuntu0~gpu16.04.1                               amd64        Tool for configuring the NVIDIA graphics driver

Bashing-om -- I'm very grateful. Can you tell me why this latest driver wouldn't update in the way I updated every other driver in the last six years? It's a little confusing.

Thanks very much for the help. Much appreciated.

~George

---

### Post by Bashing-om on 2017-09-29
geomcd1949; Sure :)

375 driver is available
[https://packages.ubuntu.com/search?keywords=nvidia-375&searchon=names&suite=xenial&section=all](https://packages.ubuntu.com/search?keywords=nvidia-375&searchon=names&suite=xenial&section=all)

384 driver does not exist:
[https://packages.ubuntu.com/search?keywords=nvidia-384&searchon=names&suite=xenial&section=all](https://packages.ubuntu.com/search?keywords=nvidia-384&searchon=names&suite=xenial&section=all)

But :
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
these folks ( across a lot of domains ) work very close with nvidia to provide us with the latest - Tested ! - drivers.

so you got that driver from the PPA . And as a bonus ubuntu will keep that driver updated ; as it is under the management of the package manager .

[INDENT]'buntu
[INDENT][INDENT][INDENT]all things are possible[/INDENT][/INDENT][/INDENT][/INDENT]

---


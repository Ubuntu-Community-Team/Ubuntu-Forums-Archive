---
title: "command for installing nvidia drivers after i successfully mount it from usb device"
date: 2017-08-13
forum: Installation &amp; Upgrades
---

### Post by eze88 on 2017-08-13
I'm running ubuntu lts 16.04 server edition, managed to mount the usb thumb drive containing the nvidia drivers but not sure what's the command to install or run the drivers

pls advise

---

### Post by Bashing-om on 2017-08-13
eze88; Hello ; 

You are doing it the hard way . Even nvidia says do not do it on linux:
> 
Note that many Linux distributions provide their own packages of the NVIDIA Linux Graphics Driver in the distribution's native package management format. This may interact better with the rest of your distribution's framework, and you may want to use this rather than NVIDIA's official package.


From the installed system terminal run:
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```
the system will install the latest driver from the software repository :)

[INDENT][INDENT]'buntu makes it easy
[/INDENT][/INDENT]

---

### Post by eze88 on 2017-08-13
I did use the following command and though it update and run but certain files say it couldn't be fetch

> sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

Also i'm not able to run "nvidia-smi" to check on the Nvdia driver version

It always display nvidia-smi couldn't be found

---

### Post by Bashing-om on 2017-08-13
eze88; Well then !

driver did not install ?
post back between code tags the outputs of terminal commands:
```

uname -r
lspci -nnk | grep -iA3 vga
dpkg -l | grep -i nvidia*
sudo lshw -C video
cat /var/log/gpu-manager.log

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We see what the story is and what we can do .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by eze88 on 2017-08-13
I run the following command, it show the following highlighted in red

uname -r   [COLOR=#ff0000] Display 4.4.0-87-generic[/COLOR]
lspci -nnk | grep -iA3 vga  [COLOR=#ff0000]display Usage: Ispci [<switches>][/COLOR]
dpkg -l | grep -i nvidia* [COLOR=#ff0000]display dpkg query no matches found [/COLOR]


When i run sudo lshw -C video it shows the following

---

### Post by Bashing-om on 2017-08-13
eze88 ; Humm ..

You have lost me . 
We are in the install correct ?? Not from the installer !
for your reference, my outputs:
> 
sysop@x1604:~$ uname -r
4.4.0-91-generic

sysop@x1604:~$ lspci -nnk | grep -iA3 vga
06:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK208 [GeForce GT 710B] [10de:128b] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:2712]
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nouveau, nvidia_375_drm, nvidia_375
06:00.1 Audio device [0403]: NVIDIA Corporation GK208 HDMI/DP Audio Controller [10de:0e0f] (rev a1)
	Subsystem: eVga.com. Corp. GK208 HDMI/DP Audio Controller [3842:2712]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

sysop@x1604:~$ dpkg -l | grep -i nvidia*
ii  bbswitch-dkms                               0.8-3ubuntu1                               amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-375                                375.82-0ubuntu0~gpu16.04.1                 amd64        NVIDIA CUDA runtime library
ii  nvidia-375                                  375.82-0ubuntu0~gpu16.04.1                 amd64        NVIDIA binary driver - version 375.82
ii  nvidia-opencl-icd-375                       375.82-0ubuntu0~gpu16.04.1                 amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.8.2                                      amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             384.59-0ubuntu0~gpu16.04.1                 amd64        Tool for configuring the NVIDIA graphics driver

sysop@x1604:~$ sudo lshw -C video
[sudo] password for sysop: 
  *-display               
       description: VGA compatible controller
       product: GK208 [GeForce GT 710B]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:29 memory:fb000000-fbffffff memory:d8000000-dfffffff memory:e6000000-e7ffffff ioport:4c00(size=128) memory:fc000000-fc07ffff
sysop@x1604:~$ 

If yours is not similar, we do need to find out why not .

Do you have a connection to our repo ?
what results:
```

ping -c3 8.8.8.8
ping -c3 archive.ubuntu.com

```

Is your system compromised ?

[INDENT][INDENT]which way did he go George
[/INDENT][/INDENT]

---


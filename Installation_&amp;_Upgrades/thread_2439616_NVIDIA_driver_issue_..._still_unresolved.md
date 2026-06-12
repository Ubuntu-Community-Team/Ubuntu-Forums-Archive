---
title: "NVIDIA driver issue ... still unresolved"
date: 2020-03-30
forum: Installation &amp; Upgrades
---

### Post by py-ohayo on 2020-03-30
Hello,

In order to be able to work on **TensorFlow** (further **TF**) with GPU support, we should install the **NVIDIA drivers**.
In addition to the **NVIDIA drivers**, the operation of **TF** also requires the installation of **CUDA** and **cuDNN**.
For the correct functioning of all these tools it is necessary to pay attention to versions of each tool.
For example, according to this link, the latest version of **TF** ([COLOR=#ff0000]v. 2.1.0[/COLOR]) works well with version [COLOR=#ff0000]10.1[/COLOR] of **CUDA**:
[https://www.tensorflow.org/install/source#gpu](https://www.tensorflow.org/install/source#gpu)
On the other hand, according to another link, version [COLOR=#ff0000]10.1[/COLOR] of **CUDA** requires version [COLOR=#ff0000]418[/COLOR] of **NVIDIA drivers**:
[https://docs.nvidia.com/deeplearning/sdk/cudnn-support-matrix/index.html#cudnn-cuda-hardware-versions](https://docs.nvidia.com/deeplearning/sdk/cudnn-support-matrix/index.html#cudnn-cuda-hardware-versions)
So if I want to use the latest version of **TF**, I need to install these versions of the tools:
TF - 2.1.0
CUDA - 10.1
NVIDIA drivers - 418
Installing NVIDIA drivers should be the first step in the installation sequence for all of these tools.
And precisely, on this first step (i.e. installation of NVIDIA drivers) it gets stuck.
When I point to version [COLOR=#ff0000]418[/COLOR] in "Additional Drivers", nothing happens. Then when I run [FONT=courier new]nvidia-smi[/FONT], it says that it is not possible to communicate with **NVIDIA drivers**:
```
pavel@ALABAMA:~$ nvidia-smi
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.
```
Also the **"Settings/About"** window says that I still have ***Intel UHD Graphics***:

[IMG]https://i.postimg.cc/NFKrKkfq/overview.png[/IMG]
However when I point to the [COLOR=#ff0000]440[/COLOR] version in "Additional Drivers", something runs for a few seconds. Then when I run [FONT=courier new]nvidia-smi[/FONT], output is different:
```
pavel@ALABAMA:~$ nvidia-smi
No devices were found

```
So, here my questions:
[LIST=1]
[*]why I can't install version [COLOR=#ff0000]418[/COLOR] of **NVIDIA drivers** ... at least the same way as I did it for [COLOR=#ff0000]440[/COLOR] 
[*]why despite installation of version [COLOR=#ff0000]440[/COLOR], [FONT=courier new]nvidia-smi[/FONT] says that [COLOR=#0000ff]*No devices were found*[/COLOR]. 
[/LIST]
Thank you in advance ?
Pavel.

---

### Post by CelticWarrior on 2020-03-30
1. 418 is probably deprecated; install the newest version recommended for your own Nvidia graphics card.

2. Probably because you have Secure Boot enabled in UEFI.

Furthermore, it's better to install CUDA from the official Ubuntu repositories instead of using Nvidia binaries. Once you have a working Nvidia driver (again, from the repos), the proper CUDA version for that driver shpould be correctly picked up.

---

### Post by py-ohayo on 2020-03-30
Thanks.
> 1. 418 is probably deprecated; install the newest version recommended for your own Nvidia graphics card.

But according to 2nd link from my 1st message, the last version (i.e. [COLOR=#ff0000]440[/COLOR]) "matches" CUDA [COLOR=#ff0000]10.2[/COLOR].
And according to the 1st link, there are no TensorFlow versions which correspond to CUDA [COLOR=#ff0000]10.2[/COLOR] (at least if I understood it correctly).
So if I continue with [COLOR=#ff0000]440[/COLOR] (assuming I can successfully install it), I probably won't be able to use TensorFlow with GPU support.

> 2. Probably because you have Secure Boot enabled in UEFI.
No.
But I didn't reboot Ubuntu ... probably should do it ?

> Furthermore, it's better to install CUDA from the official Ubuntu repositories instead of using Nvidia binaries.
The method I've just used for installing [COLOR=#ff0000]440[/COLOR] (i.e. switching to [COLOR=#ff0000]440[/COLOR] in "Additional Drivers") ... what happened exactly ... Ubuntu picked any [COLOR=#ff0000]440[/COLOR] version of **NVIDIA driver** from somewhere on my computer ... and that [COLOR=#ff0000]440[/COLOR] version isn't the same that we can find on NVIDIA website ?

---

### Post by webaake on 2020-03-30
In theory they are the same if they have the same initial version number. In practice they differ a bit. For my Nvidia I use this repo, and have for years:

[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

What Nvidia card do you have?

---

### Post by CatKiller on 2020-03-30
A couple of points:

For each version of CUDA, there is a minimum driver version that adds support for it. That driver version is included in the CUDA repositories for completeness, but is never updated. The next version of CUDA will include a driver that enables it in *that* version's repository. 

Using CUDA from Nvidia's repository with a driver from either Ubuntu's repository or the graphics drivers PPA works perfectly fine. There's a metapackage that will install the CUDA stuff from Nvidia's repository but not the driver, so you can carry on using whichever driver you have without conflicts. You just need the driver you're using to be new enough to support at least the version of CUDA that you want to use. 

Doing this on an Optimus machine makes it **way** more complicated.

Edit to correct phone-induced typo.

---

### Post by ubfan1 on 2020-03-30
Check your BIOS/UEFI settings for video hardware and select "Discrete" -- that should then force the Nvidia drivers to be used.  Once you get the nvidia-smi working, then go for the CUDA/DNN/Tensorflow installations, and skip any further Nvidia driver offers.

---

### Post by py-ohayo on 2020-03-30
> **webaake said:**
> In theory they are the same if they have the same initial version number. In practice they differ a bit. For my Nvidia I use this repo, and have for years:

[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

What Nvidia card do you have?

Here is my NVIDIA card:
```
pavel@ALABAMA:~$ lspci | grep -i nvidia
01:00.0 3D controller: NVIDIA Corporation GP107M [GeForce GTX 1050 Mobile] (rev a1)

```

For installing from this repo one should proceed this way ?
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
```

and then 
[FONT=courier new]sudo apt-get install {name_of_driver_package}[/FONT]

Correct ?

---

### Post by py-ohayo on 2020-03-30
> **CatKiller said:**
> A couple of points:
For each version of CUDA, there is a minimum driver version that adds support for it. That driver version is included in the CUDA repositories for completeness, but is never updated. The next version of CUDA will include a driver that enables it in *that* version's repository. 

Using CUDA from Nvidia's repository with a driver from either Ubuntu's repository or the graphics drivers PPA works perfectly fine. There's a metapackage that will install the CUDA stuff from Nvidia's repairing repository but not the driver, so you can carry on using whichever driver you have without conflicts. You just need the driver you're using to be new enough to support at least the version of CUDA that you want to use. 

Doing this on an Optimus machine makes it **way** more complicated.

Well, because I can probably not use [COLOR=#ff0000]440[/COLOR] because it matches only **CUDA 10.2** ... taking into account the fact that (at least at this time) no version of **TensorFlow** is compatible with **CUDA 10.2**.
So, I have to do efforts to install [COLOR=#ff0000]418[/COLOR] ... as it's the highest driver version that matches **CUDA 10.1** ... and this last one obviously matches **TensorFlow 2.1.0**. Right ?

---

### Post by py-ohayo on 2020-03-30
> **ubfan1 said:**
> Check your BIOS/UEFI settings for video hardware and select "Discrete" -- .
Can you please elaborate on how to do this?

---

### Post by py-ohayo on 2020-03-30
I just restarted the computer.
Didn't help: graphics is still **Intel® UHD Graphics 630 (Coffeelake 3x8 GT2)**

---

### Post by CelticWarrior on 2020-03-30
You have two options to use the dGPU:

1. Via **firmware (UEFI)** as already mentioned. It may or may not have such option and you asking for elaboration really doesn't inspire confidence about you PC knowledge (and you really need a slightly above average knowledge for setting what you want). This is entirely dependent on the specific hardware you have you have therefore no, we can't "elaborate". At best we can suggest what was already suggested, i.e., that you check your UEFI settings and try to find something about the graphics (again, it may not have such settings available to the user). 

2. Via **Nvidia X Server Settings**. Open it, select the high performance profile and reboot.

---

### Post by py-ohayo on 2020-03-30
> **CelticWarrior said:**
> You have two options to use the dGPU:

1. Via **firmware (UEFI)** as already mentioned. It may or may not have such option and you asking for elaboration really doesn't inspire confidence about you PC knowledge (and you really need a slightly above average knowledge for setting what you want). This is entirely dependent on the specific hardware you have you have therefore no, we can't "elaborate". At best we can suggest what was already suggested, i.e., that you check your UEFI settings and try to find something about the graphics (again, it may not have such settings available to the user). 

2. Via **Nvidia X Server Settings**. Open it, select the high performance profile and reboot.

1. I found here [https://itsfoss.com/check-uefi-or-bios/](https://itsfoss.com/check-uefi-or-bios/) how to check UEFI on Linux. Here it is:
```
pavel@ALABAMA:~$ ls /sys/firmware/efi/
ls: cannot access '/sys/firmware/efi/': No such file or directory

```

2. I can't open **Nvidia X Server Settings. **When I click on it, nothing happens.

---

### Post by CelticWarrior on 2020-03-30
UEFI is what replaced the old BIOS. It has nothing to do with the OS. Whenever you see UEFI mentioned just think "BIOS".

And again I have to insist: **Disable Secure Boot in UEFI ("BIOS")**. You said it was disabled but if you don't even know what UEFI is, it obviously wasn't disabled. With Secure Boot on the Nvidia drivers aren't loaded.

---

### Post by CatKiller on 2020-03-30
> **py-ohayo said:**
> Well, because I can probably not use [COLOR=#ff0000]440[/COLOR] because it matches only **CUDA 10.2** ... taking into account the fact that (at least at this time) no version of **TensorFlow** is compatible with **CUDA 10.2**.
So, I have to do efforts to install [COLOR=#ff0000]418[/COLOR] ... as it's the highest driver version that matches **CUDA 10.1** ... and this last one obviously matches **TensorFlow 2.1.0**. Right ?

Of course you can. The [requirement](https://docs.nvidia.com/deploy/cuda-compatibility/index.html) to use CUDA 10.1 is a version of the Nvidia driver &#8805; 418.39, since that's when they introduced 10.1.

---

### Post by py-ohayo on 2020-03-30
> **CelticWarrior said:**
> UEFI is what replaced the old BIOS. It has nothing to do with the OS. Whenever you see UEFI mentioned just think "BIOS".

And again I have to insist: **Disable Secure Boot in UEFI ("BIOS")**. You said it was disabled but if you don't even know what UEFI is, it obviously wasn't disabled. With Secure Boot on the Nvidia drivers aren't loaded.

Here is boot page of BIOS.

[IMG]https://i.postimg.cc/pr3ndxZQ/lenovo-bios.jpg[/IMG]

I didn't find secure option.

---

### Post by py-ohayo on 2020-03-30
> **CatKiller said:**
> Of course you can. The [requirement]("https://docs.nvidia.com/deploy/cuda-compatibility/index.html") to use CUDA 10.1 is a version of the Nvidia driver &#8805; 418.39, since that's when they introduced 10.1.
Thanks !
The challenge is now to revive [COLOR=#ff0000]440 [/COLOR]in my machine.

---

### Post by CatKiller on 2020-03-30
> **py-ohayo said:**
> Thanks !
The challenge is now to revive [COLOR=#ff0000]440 [/COLOR]in my machine.

The Nvidia driver doesn't switch between branches cleanly, so the first thing to do is to remove whichever version you've got before you install the new one. You'll also need DKMS installed to compile the shim that goes between the GPL kernel and the proprietary driver. It's installed by default, but you might have broken it with your tinkering. 

Optimus means that you have to manually set which graphics device you're using, and is generally a pain.

---

### Post by py-ohayo on 2020-03-30
> **CatKiller said:**
> The Nvidia driver doesn't switch between branches cleanly, so the first thing to do is to remove whichever version you've got before you install the new one. You'll also need DKMS installed to compile the shim that goes between the GPL kernel and the proprietary driver. It's installed by default, but you might have broken it with your tinkering. 

Optimus means that you have to manually set which graphics device you're using, and is generally a pain.

Finally works !
I don't know how, but I made it work. It happened after last restart.
But I didn't change nothing in system. Mystery !

Not sure if everything is correct, anyway actually it looks like this:
```
pavel@ALABAMA:~$ nvidia-smi
Mon Mar 30 23:28:43 2020       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 440.33.01    Driver Version: 440.33.01    CUDA Version: 10.2     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 1050    On   | 00000000:01:00.0 Off |                  N/A |
| N/A   39C    P0    N/A /  N/A |    356MiB /  2002MiB |      1%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0      1012      G   /usr/lib/xorg/Xorg                           239MiB |
|    0      1322      G   /usr/bin/gnome-shell                         113MiB |
|    0      2243      G   /usr/bin/nvidia-settings                       1MiB |
+-----------------------------------------------------------------------------+

```

```
pavel@ALABAMA:~$ dpkg -l | grep -i nvidia
rc  cuda-nvtx-10-1                                     10.1.243-1                                       amd64        NVIDIA Tools Extension
rc  cuda-nvtx-10-2                                     10.2.89-1                                        amd64        NVIDIA Tools Extension
ii  libnvidia-cfg1-440:amd64                           440.33.01-0ubuntu1                               amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-418                               418.87.00-0ubuntu1                               all          Shared files used by the NVIDIA libraries
ii  libnvidia-common-440                               440.33.01-0ubuntu1                               all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-390:i386                         390.116-0ubuntu0.18.04.1                         i386         NVIDIA libcompute package
rc  libnvidia-compute-418:amd64                        418.87.00-0ubuntu1                               amd64        NVIDIA libcompute package
ii  libnvidia-compute-440:amd64                        440.33.01-0ubuntu1                               amd64        NVIDIA libcompute package
ii  libnvidia-decode-440:amd64                         440.33.01-0ubuntu1                               amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-440:amd64                         440.33.01-0ubuntu1                               amd64        NVENC Video Encoding runtime library
ii  libnvidia-fbc1-440:amd64                           440.33.01-0ubuntu1                               amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-440:amd64                             440.33.01-0ubuntu1                               amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-440:amd64                           440.33.01-0ubuntu1                               amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
rc  nvidia-compute-utils-418                           418.87.00-0ubuntu1                               amd64        NVIDIA compute utilities
ii  nvidia-compute-utils-440                           440.33.01-0ubuntu1                               amd64        NVIDIA compute utilities
rc  nvidia-dkms-418                                    418.87.00-0ubuntu1                               amd64        NVIDIA DKMS package
ii  nvidia-dkms-440                                    440.33.01-0ubuntu1                               amd64        NVIDIA DKMS package
ii  nvidia-driver-440                                  440.33.01-0ubuntu1                               amd64        NVIDIA driver metapackage
rc  nvidia-kernel-common-418                           418.87.00-0ubuntu1                               amd64        Shared files used with the kernel module
ii  nvidia-kernel-common-440                           440.33.01-0ubuntu1                               amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-440                           440.33.01-0ubuntu1                               amd64        NVIDIA kernel source package
ii  nvidia-prime                                       0.8.8.2                                          all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                                    440.33.01-0ubuntu1                               amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-440                                   440.33.01-0ubuntu1                               amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-440                      440.33.01-0ubuntu1                               amd64        NVIDIA binary Xorg driver

```

I manipulated only inside "Software & Updates / Additional drivers" window.
Initially, the pilot was pointed to "Use of X.Org X".
I first tried to install the [COLOR=#ff0000]418[/COLOR] by selecting the corresponding radio button.
After that, nothing happened ... at least visually.
Then, I did the same manipulation with [COLOR=#ff0000]440[/COLOR].
This time the system reacted - a small panel with sliding cursor appeared making me think that the installation process has started.

---

### Post by py-ohayo on 2020-03-30
> **CelticWarrior said:**
> You have two options to use the dGPU:

2. Via **Nvidia X Server Settings**. Open it, select the high performance profile and reboot.

Finally I could open NVIDIA settings (have no idea why it didn't work before):

[IMG]https://i.postimg.cc/DZ6DqNgm/nvidia-settings.png[/IMG]

---

### Post by dljonsson2008 on 2020-05-02
I had most of the same symptoms listed in this thread. 
And tried all of the solutions I could find in this forum to now avail.

What finally worked for me was the easy process of reinstalling the kernel headers listed here.

If the Kernel headers are not installed none of the above solutions will help.
Before all else fails make sure your kernel headers are installed, just takes a few seconds.

[https://www.tecmint.com/install-kernel-headers-in-ubuntu-and-debian/](https://www.tecmint.com/install-kernel-headers-in-ubuntu-and-debian/)

---


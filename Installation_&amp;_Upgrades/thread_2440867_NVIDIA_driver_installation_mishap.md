---
title: "NVIDIA driver installation mishap"
date: 2020-04-16
forum: Installation &amp; Upgrades
---

### Post by py-ohayo on 2020-04-16
Hello,

I have made several unsuccessful attempts to install **TensorFlow** with GPU support.
None of them succeeded.
Then I found an approach (which uses **Docker** in the background) to install popular scientific packages (including **TensorFlow** which interests me):
[https://lambdalabs.com/lambda-stack-deep-learning-software](https://lambdalabs.com/lambda-stack-deep-learning-software)
This approach did not work either.
Finally I decided to follow official TensorFlow manual on installing (and using) **TensorFlow** with **Docker**.
[https://www.tensorflow.org/install/docker](https://www.tensorflow.org/install/docker)
But this approach assumes that the NVIDIA drivers must be installed separately ... as mentioned here:
[https://github.com/NVIDIA/nvidia-docker](https://github.com/NVIDIA/nvidia-docker)

So, before starting I removed whole NVIDIA staff:
   	 	 	 	 	 	    [TABLE]
 	 	[TR]
 		[TD="align: left"][FONT=FreeMono][SIZE=3]sudo apt-get purge nvidia-\*[/SIZE][/FONT]

[FONT=arial][SIZE=2]After that, I checked if nvidia was properly purged:
[/SIZE][FONT=courier new]
[/FONT][/FONT][/TD]
 	[/TR]
 [/TABLE]
[FONT=courier new]    [/FONT][FONT=courier new]pavel@ALABAMA:~$ dpkg -l | grep -i nvidia
rc  cuda-nvtx-10-1                                     10.1.243-1                                       amd64        NVIDIA Tools Extension
rc  cuda-nvtx-10-2                                     10.2.89-1                                        amd64        NVIDIA Tools Extension
rc  libnvidia-compute-390:i386                         390.116-0ubuntu0.18.04.1                         i386         NVIDIA libcompute package

[FONT=arial]3 packages were kept ... but probably it's Ok.

Then I tried to install drivers as suggested on NVIDIA manual:
[/FONT][https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#ubuntu-installation](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#ubuntu-installation)
[/FONT]
[FONT=courier new]pavel@ALABAMA:~$ sudo apt-get install cuda-drivers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cuda-drivers : Depends: libnvidia-common-440 (>= 440.64.00) but 440.64-0lambda0~18.04.1 is to be installed
                Depends: libnvidia-compute-440 (>= 440.64.00) but 440.64-0lambda0~18.04.1 is to be installed
                Depends: libnvidia-decode-440 (>= 440.64.00) but 440.64-0lambda0~18.04.1 is to be installed
                Depends: libnvidia-encode-440 (>= 440.64.00) but 440.64-0lambda0~18.04.1 is to be installed
                Depends: libnvidia-fbc1-440 (>= 440.64.00) but 440.64-0lambda0~18.04.1 is to be installed
                Depends: libnvidia-gl-440 (>= 440.64.00) but 440.64-0lambda0~18.04.1 is to be installed
                Depends: libnvidia-ifr1-440 (>= 440.64.00) but 440.64-0lambda0~18.04.1 is to be installed
                Depends: nvidia-compute-utils-440 (>= 440.64.00) but 440.64-0lambda0~18.04.1 is to be installed
                Depends: nvidia-dkms-440 (>= 440.64.00)
                Depends: nvidia-driver-440 (>= 440.64.00) but 440.64-0lambda0~18.04.1 is to be installed
                Depends: nvidia-kernel-common-440 (>= 440.64.00) but 440.64-0lambda0~18.04.1 is to be installed
                Depends: nvidia-kernel-source-440 (>= 440.64.00) but 440.64-0lambda0~18.04.1 is to be installed
                Depends: nvidia-utils-440 (>= 440.64.00) but 440.64-0lambda0~18.04.1 is to be installed
                Depends: xserver-xorg-video-nvidia-440 (>= 440.64.00) but 440.64-0lambda0~18.04.1 is to be installed
                Depends: nvidia-modprobe (>= 440.64.00)
                Depends: nvidia-settings (>= 440.64.00) but 440.64-0lambda1 is to be installed
E: Unable to correct problems, you have held broken packages.
pavel@ALABAMA:~$ [/FONT]

Where is the problem ?

Other observations:
1. Here is "Other Software" screenshot:
[IMG]https://i.postimg.cc/nLqXpR14/Screenshot-from-2020-04-16-10-21-41.png[/IMG]

Probably should I clean it up in some way ?

2. Despite the purging of NVIDIA staff there is still non-empty **cuda-repo-10-2-local-10.2.89-440.33.1** in the **/var** directory.

Any help will be appreciated.

Thanks in advance.

---

### Post by py-ohayo on 2020-04-16
After removing **lambdalabs** repository I could install NVIDIA driver

---


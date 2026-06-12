---
title: "Can not boot into Ubuntu on T420"
date: 2014-12-07
forum: Installation &amp; Upgrades
---

### Post by Will_Moonen on 2014-12-07
Hi Everyone,

I'm trying to get Ubuntu (14.04.1) running on a Lenovo laptop T420.
This one has a Nvidia - Optimus on board. However, this is disabled in the BIOS.
Meaning that the BIOS is set to use the discrete graphics and Optimus detection is disabled.
The graphics card is a NVS-4200M (beside the Intel one).

After the initial install, a reboot brings up the grub menu.
Which allows me to boot into Windows and Ubuntu - among some other things.
Booting into Windows works fine.

However booting into Ubuntu always ends up in a black screen with a blinking cursus in the top left screen.
When booting into recovery mode, the mileage varies. Most of the time, it stops with a message about the video card.
Some time, it ends with something about a MDM driver - not sure what is stands for.

Most of the times, I can boot with a USB stick that has Ubuntu 14.04.1 on it - but not always.

The strange thing is that booting with Integrated or NVidia Optimus enabled in the BIOS always works fine.
Although neither of these where configured during the initial install.

I have checked the Lenovo support site for BIOS updates. So far nothing.

All-and-all - it seems that the discrete, 4200M graphics card is the blocking one.
However, I can not figure out how to fix this.
It doesn't really matter if I install the latest NVidia drivers (the PPA from xorg-edgers), one of the drivers that come with Ubuntu or even the Nouveau one.

I have search through numerous topics pointing at simular issues with the Lenovo model - however, sofar no luck.

Anyone out there that recognizes this and knows where to start troubleshooting?
Or even better - is there someone who has a solution?


Thanks - Will

---

### Post by ajgreeny on 2014-12-07
At the grub menu hit "E" for the Ubuntu kernel item you want to boot, use cursor keys to navigate to the words **quiet splash** near the end of the kernel line and delete those two words and in their place type **nomodeset**.

Now use Ctrl+X to boot and you may get to the GUI you want.  Once there you can see if there are any Additional drivers for your nvidia card.

---

### Post by oldfred on 2014-12-07
If you have tried installing nVidia drivers, you must purge an install before attempting to install from another source. The direct download or (maybe) ppa and versions from Ubuntu repository always seem to conflict. If you totally purge, you then should be able to just download the most current version from Ubuntu repository. 

       # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices

I have different nVidia card, but always had to use nomodeset to boot live installer and first boot or until I install the nVidia driver from the repository. Generally the version in the Ubuntu repository is good choice, the ppa have newer versions which may really only be required if you have very new card or chip from nVidia. 

You may be booting with Optimus enabled as then you are really using the Intel chip for video and nomodeset not required. But sometimes Intel chip needs different boot parameters.

      
 [https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
Getting hybrid graphics to work nvidia-prime GT650M - but you want most current nVidia driver available
[http://askubuntu.com/questions/412452/getting-hybrid-graphics-to-work-nvidia-prime-gt650m](http://askubuntu.com/questions/412452/getting-hybrid-graphics-to-work-nvidia-prime-gt650m)
Testing NVIDIA Optimus / DRI PRIME On Ubuntu 14.04
[http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1)
Bumblebee - allows both nVidia & Intel to be used, nVidia Prime is just nVidia:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://askubuntu.com/questions/452556/how-to-set-up-nvidia-optimus-bumblebee-in-14-04](http://askubuntu.com/questions/452556/how-to-set-up-nvidia-optimus-bumblebee-in-14-04)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

Searching nVidia says the 340.xx is correct for your chip. But that is not the very newest from nVidia, but may be a bit newer than current in Ubuntu repository.
       nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

---

### Post by Will_Moonen on 2014-12-09
> **ajgreeny said:**
> At the grub menu hit "E" for the Ubuntu kernel item you want to boot, use cursor keys to navigate to the words **quiet splash** near the end of the kernel line and delete those two words and in their place type **nomodeset**.

Now use Ctrl+X to boot and you may get to the GUI you want.  Once there you can see if there are any Additional drivers for your nvidia card.

Thank you for the tip. However, that didn't help.
Sofar, the only way to get things going seems to be the Optimus mode and select with NVidia Prime.

---

### Post by Will_Moonen on 2014-12-09
> **oldfred said:**
> If you have tried installing nVidia drivers, you must purge an install before attempting to install from another source. The direct download or (maybe) ppa and versions from Ubuntu repository always seem to conflict. If you totally purge, you then should be able to just download the most current version from Ubuntu repository.

Tried this one too - no luck.

> **oldfred said:**
> 
       # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices


Don't understand this line - what do you mean?

> **oldfred said:**
> 
I have different nVidia card, but always had to use nomodeset to boot live installer and first boot or until I install the nVidia driver from the repository. Generally the version in the Ubuntu repository is good choice, the ppa have newer versions which may really only be required if you have very new card or chip from nVidia. 

You may be booting with Optimus enabled as then you are really using the Intel chip for video and nomodeset not required. But sometimes Intel chip needs different boot parameters.

As mentioned previously, the nomodeset didn't work for me.
Sofar, the only way to get things going seems to be the Optimus mode in the BIOS and select the NVidia card with NVidia Prime.

Even when this process is completed, switching the BIOS back to discrete is not working.
Somehow, regardless the version of the installed drivers, they do not see the NVS-4200 as NVidia card => the boot ends in a black screen.

---

### Post by oldfred on 2014-12-09
If you are booting with the Intel chip it may need one of these parameters.
       Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

            # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

    
I only have nVidia card, so it only is suggesting the nVidia drivers
```
fred@trusy-ar:~$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
vendor   : NVIDIA Corporation
modalias : pci:v000010DEd00000F01sv000019DAsd00009231bc03sc00i00
model    : GF108 [GeForce GT 620]
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-304-updates - distro non-free
driver   : nvidia-304 - distro non-free
driver   : nvidia-331 - distro non-free recommended
driver   : nvidia-331-updates - distro non-free


```

---


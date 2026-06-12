---
title: "Cannot boot from external drive"
date: 2015-11-29
forum: Installation &amp; Upgrades
---

### Post by Merlino on 2015-11-29
Hello everyone,
I posses a new asus laptop with an  intel i7-4720 and an NVIDIA gtx 950m. Originally it had windows 10 and I created a dual boot with ubuntu 14.04 without any trouble. Then I tried to install the CUDA libraries and the pandemonium started.
If I boot from windows no problem, but ubuntu fails to boot with the error "Unable to mount /boot/efi". I tried to reinstall ubuntu from a usb drive, but the process freeze at the purple screen with the the ubuntu writing and the 5 colored dots. This happens both for "Try without installing" and "Install ubuntu". I also recovered the windows bot manager and formatted the partition that held linux and its swap, with no improvement.
 I need a linux OS with a working CUDA library for work reasons, so any help would be really appreciated, both on how to recover ubuntu and how to install CUDA without screwing everything up.
Cheers, Giovanni.

---

### Post by grahammechanical on 2015-11-29
> and formatted the partition that held linux and its swap, with no improvement.

Doing that stops you from doing this

> on how to recover ubuntu

How did you try to install CUDA libraries? We can install a Nvidia drvier appropriate for ou video adapter from System Settings>Software & Updates>Additional Drivers tab. 

Regards.

---

### Post by Merlino on 2015-11-29
> [COLOR=#000000]Doing that stops you from doing this[/COLOR]
I suppose I did not express myself clearly, sorry. I do not need to recover the previous installation as it was fresh, I just need to install ubuntu and CUDA again on the same partition.
> [COLOR=#000000]How did you try to install CUDA libraries? [/COLOR]
From the official website [https://developer.nvidia.com/cuda-downloads](https://developer.nvidia.com/cuda-downloads) using the .deb installer. The system froze midway during the installation (not even the emergency shell was available).
If i press up during the boot process to get some feedback it get stuck at "startiting restore sound card state".

---

### Post by oldfred on 2015-11-30
Have not used cuda.
But did you install Ubuntu with UEFI or BIOS boot?

And how did you install newest nVidia drivers? Best to use ppa to get newest driver. If you install directly from nVidia you have to reconfigure with each new kernel update as it is not in dpkg for auto update.

       Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)

    Found this, not sure if same for newer version  or not.
[http://www.r-tutor.com/gpu-computing/cuda-installation/cuda7.5-ubuntu](http://www.r-tutor.com/gpu-computing/cuda-installation/cuda7.5-ubuntu)

---

### Post by furtom on 2015-11-30
> **Merlino said:**
> This happens both for "Try without installing" and "Install ubuntu". 

This leads me to believe you did not install ubuntu, but were booting the live DVD instead. If you tried to update that with nVidia drivers, this could explain things.

I'd try again to install ubuntu. boot the installation media and choose "Install Ubuntu."

EDIT: Scratch that. I see you were saying this happens when you are trying to reinstall. I read too fast. Sorry.

try a boot option something like vga=723 (or 771)

---

### Post by oldfred on 2015-11-30
vga settings are now obsolete.

It depends on which video mode is active when you boot. 
If nVidia you need nomodeset.
If Intel you may need one of the Intel boot parameters.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132
[/URL]
 # Usually nVidia or AMD work with this:
nomodeset
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

You really want UEFI install if Windows is UEFI. Lots of details and useful links in the link in my signature below.

[URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

### Post by furtom on 2015-11-30
> **oldfred said:**
> vga settings are now obsolete.

Ha! I guess I'm getting obsolete, myself!

Thank you for the correction.

---

### Post by Merlino on 2015-12-03
> **oldfred said:**
> vga settings are now obsolete.

It depends on which video mode is active when you boot. 
If nVidia you need nomodeset.
If Intel you may need one of the Intel boot parameters.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132
[/URL]
 # Usually nVidia or AMD work with this:
nomodeset
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

Thank you very much, this solved my problem! 
I managed to boot with the "nomodeset" option and I installed kubuntu 14.04. I had to run boot-repair after the installation though.
I also managed to install the CUDA driver by disabling x server with "sudo service lightdm stop", and then install the NVIDIA drivers from their .run file instead of their .deb.
Now ubuntu works flawlessly, aside from the realtek wifi chip, but this is another story. 
Thanks again!

---

### Post by oldfred on 2015-12-03
If you install nVidia from the .run file and not from a ppa, you have to reconfigure every new Kernel to use driver manually. When installed from repository or private repository like a ppa, then dpkg manages driver configuration with new kernel.

       #What is installed
dkms status

[http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia)

If you change driver, be sure to totally purge old driver, before installing new one. Otherwise you have major conflicts.

---


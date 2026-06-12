---
title: "Location legacy nvidia-xconfig [or using nvidia-gfx-71 in Ubuntu 9.10]"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by Syrion on 2010-01-02
Heya,

I have 9.10 running on an old computer with a Nvidia Vanta-graphics card. Unfortunately these appearently aren't supported by 9.10, since the oldest nvidia drivers in the repository for this build are nvidia-gfx-96, while vanta seem to supported up to nvidia-gfx-71.

After some hours of following tutorials, fiddling around and testing I managed to install the 71-drivers. But, the nvidia-settings require nvidia-xconfig to be around, which is embedded with later driver-builds but not with 71.

Fortunately I found a tar.gz at [this page]("http://www.nvidia.com/object/linux_display_ia32_71.86.11.html"), so I downloaded it... but -and here is finally my question- where am I supposed to extract it to and are there other things I should do to get it working?

Or, if I'm overcomplicating things, feel free to give me directions on what to do. Unfortunately I couldn't find anything on Ubuntu 9.10 and nvidia-gfx-71, hence I'm messing around for hours by now. ;)

Thanks in advance!

---

### Post by Syrion on 2010-01-03
Still no luck.

---

### Post by Syrion on 2010-01-04
No one knows?

---

### Post by Syrion on 2010-01-07
Guess it's not possible.

---

### Post by Edwin_OS on 2010-01-08
Hi, the way of installing those drivers is:

1. Download the ".run" file
2. stop your x server
3. You're gonna need the packages "gcc" "make" and the sources of your kernel I think
4. run the file as root "sh NVIDIA-Linux-x86-71.86.11.pkg1.run"
5. Then you will have (at least in theory) your nvidia drivers installed, restart the x server
6. Edit your xorg.conf to use "nvidia" instead of "nv"

I want to tell you that I recently made that process many many times, and I've got no results, It always fails, please tell me if it works because I'm about to give up

(I have an nvidia Vanta also)

---


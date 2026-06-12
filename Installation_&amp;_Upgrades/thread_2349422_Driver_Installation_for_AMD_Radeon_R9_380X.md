---
title: "Driver Installation for AMD Radeon R9 380X"
date: 2017-01-14
forum: Installation &amp; Upgrades
---

### Post by freeos2017 on 2017-01-14
Hello,
Fairly new to Linux but been playing around for a couple years already. I want to get the most performance out of my machine so do I need to install the drivers from the AMD website? If so, could you provide steps on how to do that?
Or is the AMD Tonga driver good enough? 
Thanks!

[ATTACH=CONFIG]273209[/ATTACH]

---

### Post by QIII on 2017-01-14
If you are using 16.10, you should be able to install AMDGPU-PRO and the Vulkan SDK from the Ubuntu repositories.

Do you have synaptic installed?

---

### Post by 4l3x2 on 2017-01-15
I use this thread because is somewhat similar to my issue.

I just sold my Mac Mini Late 2009 and bought a (used) Quad Core with 4Gb of ram, 600Gb Hd and (Sapphire) Ati Radeon Toxic R9 270x with 2Gb ddr3 video ram.

After installing XUbuntu 16.10 I did all the upgrades and installed all the software I need except of the video drivers.

The line I see from lspci (related to the video driver) is:
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Curacao XT / Trinidad XT [Radeon R7 370 / R9 270X/370X]

In order to obtain maximum performances I downloaded the drivers from AMD/ATI, but they are for 14.01 Ubuntu (64bits).
They are packaged in a .deb file, so I tried to install them anyway. The gui is correctly shown, but when I click on install, the procedure stops suddenly and I´m back in the initial page.

Now I´ll try to install the driver suggested by QIII, but what are the differences between these packages?

Except of being open/closed source, obviously.

Thank you very much :)

---

### Post by 4l3x2 on 2017-01-15
A little update, AMDGPU driver was already installed, Vulkan sdk is not shown by Synaptic, I installed all the possible choices:
Vulkan utils
Mesa-Vulkan drivers
Libvulkan1
Libvulkan-dev

---


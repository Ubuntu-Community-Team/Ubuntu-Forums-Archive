---
title: "USB-3 SSD for Multi System  (Different GPU)"
date: 2019-07-07
forum: Installation &amp; Upgrades
---

### Post by Mr Puffin on 2019-07-07
Hello all,
 i have used Ubuntu Mostly Xubuntu off and on since first trying out in 2007 and am most definitely not an expert mostly a Tinkerer /Intermediate user, mostly stick to Mac for productivity and Windows for Games.

i have a spare M.2 SSD in an adapter that i have setup as a USB-3 Xubuntu 19.04 that i would like to be usable on multiple Computers.
i had no issues doing this until more recently when i added an AMD GPU (Vega 56) to my Main PC all others were either Intel iGPU or nVidia Graphics.
now every time i set it up to work on other Nvidia/Intel iGPU systems it works until i add the AMD Graphics drivers. on the AMD system. 

i feel like the Drivers conflict between AMD/Nvidia and cause the system to not boot once i add the rivals Drivers

what works 
AMD GPU and Intel iGPU
Nvidia GPU and intel iGPU
but as soon as Nvdia + AMD Drivers are installed it is a No Go on Either System.
All systems i intend to use are EFI/UEFI


sorry if this is rambleing or wrong post location i would just like to have a Portable SSD with All My Stuff / Drivers for all my systems (Laptop/Desktops)

Thanks all
-Mr Puffin

---

### Post by CatKiller on 2019-07-07
If you want it to be portable, don't use the proprietary Nvidia driver. It doesn't play well with others. The only reason it works with an Intel iGPU is because Optimus was a thing Nvidia did, and even that didn't work at all well for a very long time.

Nouveau uses exactly the same infrastructure as the Intel and AMD graphics stacks, so it will work portably, but its functionality is curtailed by lack of cooperation from Nvidia.

---


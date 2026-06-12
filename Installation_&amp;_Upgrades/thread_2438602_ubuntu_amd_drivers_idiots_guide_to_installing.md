---
title: "ubuntu amd drivers idiots guide to installing?"
date: 2020-03-14
forum: Installation &amp; Upgrades
---

### Post by jebi on 2020-03-14
Hi

Is the any idiots guide to installing AMD GPU drivers on vanilla ubuntu?

thx

---

### Post by kurt18947 on 2020-03-14
There's a good chance you're already using the correct AMD GPU driver. AMD has discontinued their proprietary drivers and typically the correct AMD driver loads when the machine boots. There are only two drivers that I'm aware of, Radeon and AMDGPU, Radeon is used by older systems, AMDGPU by newer. Right now I'm on a Ryzen3 2200G (integrated graphics). AMDGPU loaded with no action on my part. If you open a terminal and type the command

```
lspci
``` (list the items on the PCIe bus)

you may see something like this:

```
38:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series] (rev c8)
```

If you were to type the command

```
lsmod
``` (list the modules loaded)

You might see something like this:

```
amdgpu               4575232  5  
```

so the driver for newer AMD GPUs is loaded.

There are graphical apps that may give more info but the above will tell you what's installed and in use. Hope this helps.

---

### Post by TheFu on 2020-03-14
2 other commands to see the VGA cards and driver used:

```
lspci -vk |perl -lne 'print if /VGA/ .. /^[\w]*$/'
```
```
sudo lshw -C video
```

---


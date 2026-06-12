---
title: "Second Monitor not Detected, Ubutnu 22.04, AMD Radeon™ RX 6600 XT"
date: 2023-03-30
forum: Installation &amp; Upgrades
---

### Post by sarah123321 on 2023-03-30
I have an AMD Radeon™ RX 6600 XT GPU installed on a supermicro motherboard running Ubuntu  22.04.2 LTS. I went through the amdgpu install process, however only one  monitor (connected to motherboard) is detected. The monitor connected  to GPU isn't detected. See outputs below. I am fairly new to linux, can anyone suggest how  to proceed? The monitor attached to the gpu displays the supermicro logo on startup, however goes black and is no longer recognised once the computer reaches the ubuntu login page.



 Outputs:

 $ lspci -k | grep -EA3 'VGA|3D|Display'
 03:00.0 VGA compatible controller: ASPEED Technology, Inc. ASPEED  Graphics Family (rev 52) DeviceName: ASPEED Video AST2600 Subsystem:  Super Micro Computer Inc ASPEED Graphics Family Kernel driver in use:  ast


 43:00.0 VGA compatible controller: Advanced Micro Devices, Inc.  [AMD/ATI] Navi 23 [Radeon RX 6600/6600 XT/6600M] (rev c1) Subsystem:  ASRock Incorporation Navi 23 [Radeon RX 6600/6600 XT/6600M] Kernel  driver in use: amdgpu Kernel modules: amdgpu


 $ xrandr --listmonitors
 Monitors: 1 0: +*VGA-1 1920/531x1080/299+0+0 VGA-1



$ echo $XDG_SESSION_TYPE 
x11


[Screenshot showing Graphics as llvmpipe in Settings -> About][1] [1]: [https://i.stack.imgur.com/epp9T.png](https://i.stack.imgur.com/epp9T.png)

---

### Post by MAFoElffen on 2023-03-31
Is the power running to it enough wattage from the PSU? Minimum for that GPU is 500W.

Check that the correct power plugs are connected to the GPU card.

Ensure the card is seated in the motherboard PCIe slot.

Ensure that the correct PCIe power plug is plugged from the PSU to the motherboard.

Has this card ever worked with this motherboard?

What is the BIOS setting for video set to? On my MicroServer board, that setting is PCI/PnP Configuration > Primary Video Controller.

---

### Post by MAFoElffen on 2023-04-02
Alibi: I have a SuperMicro Board in my Workstation, I just  remembered... On mine, there is a jumper between the card slots, that if  jumped, disables the onboard GPU. You might want to check your  motherboard manual to see it this exists on your motherboard, and if it  is jumped.

---


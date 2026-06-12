---
title: "ATI Drivers crash Unity"
date: 2015-07-15
forum: Installation &amp; Upgrades
---

### Post by dannybabbev on 2015-07-15
I am currently trying to install graphics drivers for my GPU. But my  case may be a bit different, I have an **APU A10-7770K** and a graphics card  **Radeon R7 250X**. I tried many, many times to get my rig run properly,  with the package manager :
 ```
apt-get install fglrx, 
apt-get install fglrx-updates 
```.  
With the automated installer provided by AMD for Linux, with the  packages, downloaded from AMD and using the "Additional Drivers". They  all install successfully but upon starting the OS, my GUI(Unity)  crashes. I've been trying to edit the **xorg.conf** file, but nothing works.  Every time upon error, I uninstall all the drivers from recovery mode  with networking and root access with ```
apt-get purge fglrx
```. I  think, maybe the **APU** is conflicting with the driver. Because these  drivers are compatible with the GPU: R7 250X but not the GPU in the APU  and if the APU GPU is set to be default this is where the problem may  be. Unfortunately I do not know how to check it nor set it. Please give  your suggestions. 

 _**My onboard GPU is disabled in UEFI BIOS, but still showing in linux, I have no idea why**_. *Output of lspci | grep VGA:* 
```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri [Radeon R7 200 Series] 
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde XT [Radeon HD 7770/8760 / R7 250X]
``` 

 **Upon every reboot my xorg.config file is rewritten**. All the settings made by ```
aticonfig --initial
``` are being overwritten.

---


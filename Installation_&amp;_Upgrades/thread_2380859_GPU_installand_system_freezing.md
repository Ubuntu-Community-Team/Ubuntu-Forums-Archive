---
title: "GPU install/and system freezing"
date: 2017-12-23
forum: Installation &amp; Upgrades
---

### Post by mike-a-nsd on 2017-12-23
So really weird thing happening. I have a Dell T620 with GPU kit and I am trying to install Ubuntu Server and use a Nvidia GPU for cuda computations. I can install Ubuntu 16.04.3 LTS, it is a completely clean install no RAID just 1 drive, no problem. However, whenever I try to install Nvidia Cuda or the Nvidia graphics driver the system freezes, I have tried it 3 or 4 different ways I get the farthest without freezing using Noveau. The ppa drivers did not work neither did just sudo apt-get install nvidia-384*, or even using the GUI and downloading the linux Cuda file using Nvidia's instructions. 

The other really weird thing is the system will not reboot and locks up whenever just the GPU is installed in the motherboard, as soon as i take it out bingo everything works. That is right after a fresh install I power down and install the GPU in the motherboard. 
 Bear in mind that I cannot install a driver and I do not have a GUI installed. I have tried 3 different Cuda compatible cards GForce 1080, 980, and 960. Note I have ran the same hardware in Windows and the GPUs work. 

Card in motherboard: freezes after: sudo apt-get upgrade, sudo reboot, sudo apt-get install [anything], 50/50 on boot as it goes through its checks.

Card not in motherboard: go through install process and drivers either didnt install, " You do not appear to have an NVIDIA GPU Supported", I believe they did install and rebooting to verify and freezes everywhere even in the so-called "safe mode",  

I have been at this for 3 days now and probably have reinstalled the OS 10 times because being stuck and nothing working, I need to figure this out soon.

---


---
title: "Graphics Drivers on 13.10?"
date: 2013-11-03
forum: Installation &amp; Upgrades
---

### Post by zrussellneely on 2013-11-03
Hello,

I'm pretty new to linux, so please forgive me if I make some mistakes or leave out important information. I currently am dual-booting Windows 7 and Ubuntu 13.10 (with LUKS encryption). Ubuntu was working perfectly, but I noticed that my graphics card (the Nvidia NVS 5300M) wasn't being used. I tried to install the proprietary Nvidia drivers from their webpage, which didn't work for a while; I had to stop Nouveau from being loaded on boot (I think). However, now when I boot, I see no LUKS password screen (but typing my password and pressing enter still boots the computer). When it arrives at the login screen, it's in extremely low resolution. Logging in works, but the resolution stays low and can't be increased. I've also tried 'apt-get install nvidia-current', which doesn't seem to help. I've done a lot of googling and nobody's solutions seem to help me. One thing I've noticed is that 'dpkg-reconfigure' does not produce any output.

Running 'lspci | grep -i VGA' returns:
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108GLM [NVS 5200M] (rev a1)

Running 'jockey-text -l' returns:
kmod:nvidia_319_updates - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)
kmod:nvidia_304 - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)
kmod:nvidia_304_updates - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)
kmod:nvidia_319 - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)


     

 All I want to do is get my original graphics controller back, so if anyone could help, that'd be great.

---

### Post by grahammechanical on 2013-11-03
Why were you installing from the Nvidia web site when we have a utility that will install proprietary video drivers for us? We find it in System Settings>Software and Updates>Additional Drivers tab.

Does your machine have Nvidia Optimus technology. That present special issues regarding drivers because Nvidia has been slow to make a driver available for Optimus.

Regards.

---

### Post by zrussellneely on 2013-11-04
Ahh yes it does have Optimus tech. And I was installing it from their website because going to the Additional Drivers page said that no drivers were available, and I (mistakenly) thought that would be the best way to go. Do you have any suggestions, or do I just need to wait on Nvidia?

---


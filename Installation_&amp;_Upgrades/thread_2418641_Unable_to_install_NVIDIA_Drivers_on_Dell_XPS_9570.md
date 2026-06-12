---
title: "Unable to install NVIDIA Drivers on Dell XPS 9570"
date: 2019-05-09
forum: Installation &amp; Upgrades
---

### Post by bertv96 on 2019-05-09
Hi !

My PC specs:
DELL XPS 9570 , 16 GB Ram, 512 GB M.2 SSD, 1050Ti. Screen res is 1920x1080.

I recently tried to install Ubuntu 19.04 on my Dell XPS 9570. But that failed, so I tried it with the [respin ISO]("https://github.com/JackHack96/dell-xps-9570-ubuntu-respin") from Jack, which is 18.04.2 with some tweaks especially for my laptop. 

What i did:
- I installed this respin IS. Went pretty smooth. (added the nouveau modeset=0 in the GRUB, ...)
- I did run the XPS tweaks afterwards (which is located in the Github from this respin ISO.)

The problem:
My laptop screen is 1920x1080 and I have an external monitor 32inches running a 2550x1440 resolution, and this external display is not working in this higher resolution. 

When I go to display settings. i can see the resolution that I need for my external display. When I click apply, my external display goes black, but I can drag windows to it.
But when I go to a higher screen resolutions for my external display, like 1920x1080, that my external display works, but it doesn't look very good...

These are issues related because the drivers are not (correctly) installed.
But i'm unable to install them. Links below are the tutorial/forums I read trying to install it.

Everytime when i reboot and check with 'nvidia-smi' in Terminal if they are correctly installed. It gives me this error:
[ATTACH=CONFIG]283232[/ATTACH]

link 1: [https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)
link 2: [https://www.mvps.net/docs/install-nvidia-drivers-ubuntu-18-04-lts-bionic-beaver-linux/](https://www.mvps.net/docs/install-nvidia-drivers-ubuntu-18-04-lts-bionic-beaver-linux/)

[ATTACH=CONFIG]283233[/ATTACH][ATTACH=CONFIG]283230[/ATTACH][ATTACH=CONFIG]283231[/ATTACH]
[ATTACH=CONFIG]283234[/ATTACH]
So, can anyone help me please !? 

Thanks,
Bert



EDIT: I also tried [this approach]("https://medium.com/@peterpang_84917/personal-experience-of-installing-ubuntu-18-04-lts-on-xps-15-9570-3e53b6cfeefe"). See section "Install NVIDIA Drivers"
But it didn't work...

---

### Post by TheFu on 2019-05-09
Have you tried changing the video cable?  Perhaps the very high resolution is too much for the current cable?
Best to install proprietary video drivers using the built-in methods for the OS through existing menus.  It is not a good idea to install those using the packages from the vendor.

---


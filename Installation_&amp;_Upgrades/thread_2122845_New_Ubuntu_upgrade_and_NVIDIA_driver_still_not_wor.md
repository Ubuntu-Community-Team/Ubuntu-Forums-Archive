---
title: "New Ubuntu upgrade and NVIDIA driver still not working"
date: 2013-03-06
forum: Installation &amp; Upgrades
---

### Post by fjanos on 2013-03-06
After new Ubuntu 12.10 upgrade the menu taskbar, launchpad disappeared and nowhere to click. I get only the background screen in high resolution After some previous Ubuntu updates I got the same result so I serached in forums and I knew what I had to do and I followed the steps to reinstall Nvidia driver. After this last ubuntu 12.10 update I did it again but now I get the same useless Ubuntu. 
Nvidia driver: 310.32
Graphic card: Nvidia Gforce 430
Ubuntu version: 12.10

These are the steps I made.
[LIST=1]
[*]CTRL+ALT+F2 to prompt login 
[*]sudo apt-get update 
[*]I stopped xserver sudo service lightdm stop 
[*]sudo chmod 755 Nvidia- LInux-x86-64-310.32.run 
[*]sudo ./Nvidia-Linu-x86-64.310.32.run 
[*]Installation process started 
[*]I get "The distribution-provided pre-install script failed!  Continue installation anyway?" (Answer: Yes) 
[*]I get "Would you like to register the kernel module sources with DKMS? This will allow DKMS to automatically build a new module, if you install a different kernel later. (Answer: Yes) 
[*]When prompted to *install 32*-*bit compatibility libraries* (Answer: Yes) 
[*]I get "*Would you like to run the nvidia-xconfig utility to automatically  update your X configuration file so that the NVIDIA X driver will be  used when you restart X?" *(Answer: Yes) 
[*]I get ""Would you like to run the nvidia-xconfig utility to update your X configuration Automatically 
That file so the NVIDIA X driver will be Used When you restart X? Any pre-existing X configuration file will have backed up." (Answer: Yes) 
[*]sudo start lightdm 
[*]It returns and I get the same USELESS UBUNTU QUETZAL 
[/LIST]

It drives me crazy. It stops me in my work. Please any hint or tip. What else can I do??? I don't want to return to use Windows.

---

### Post by bogan on 2013-03-06
Hi!, **fijanos,**

 Check that: ```
linux-headers-generic # and: 
linux-headers-'uname -r' 
```are installed, if not install them and rerun the nvidia installer.

[Run 'uname -r' and insert the output in place of 'uname -r' in the above command.]

Chao!, **bogan.**

---

### Post by Cheesemill on 2013-03-06
If you use the drivers from the Ubuntu repositories instead of downloading the ones from the ATI website then you wouldn't have this problem.

At the moment you are having to manually compile the kernel modules for your video card every time your kernel is upgraded, with the drivers from the 'Additional Drivers' application all of this is taken care of for you.

---

### Post by bogan on 2013-03-07
> **Cheesemill said:**
> If you use the drivers from the Ubuntu repositories instead of downloading the ones from the ATI website then you wouldn't have this problem.

At the moment you are having to manually compile the kernel modules for your video card every time your kernel is upgraded, with the drivers from the 'Additional Drivers' application all of this is taken care of for you.This is just not true any longer for Nvidia drivers - I can not speak for ATI.

As You can see, from the OP's Post, the nvidia-installer gives the option to register the kernal module with DKMS:>  "Would you like to register the kernel module sources with DKMS? This  will allow DKMS to automatically build a new module, if you install a  different kernel later. (Answer: Yes)This has been available for several months with drivers of version 304.xx and later.

Chao!, **bogan**.

---

### Post by wribeiro on 2013-03-07
Integration between Unity and nVidia Driver is a disaster.
Open source project seems to have been abandoned.

---

### Post by venik212 on 2013-03-07
I have the very same problem.  Some "upgrade" has degraded the resolution of my screen from 1920... to 1600. 
I went through several step-by-step installation procedures for the nvidia driver, but my screen is stuck in this lower resolution, even though it worked fine a few days ago.  I am running the Nouveau driver now (open source) which seems unable to drive my Quadro FX570 at its full resolution.  Need I tell you that running WINDOWS on the very same hardware (dual boot) gives me the full resolution?  THis is PATHETIC-- and I hope Shuttleworth is aware of it.

---


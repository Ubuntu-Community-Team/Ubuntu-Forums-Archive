---
title: "installing nvidia 540M(cuda 2GB) drivers on ubuntu"
date: 2012-07-26
forum: Installation &amp; Upgrades
---

### Post by aujamal20 on 2012-07-26
Dear
I am using ubuntu 10.04 installed on my lapy asus k53sv. 
Specs can be found on 
[http://www.asus.com/Notebooks/Versatile_Performance/K53SV/#specifications](http://www.asus.com/Notebooks/Versatile_Performance/K53SV/#specifications)

I need to use my nvidia graphics card which I was unable to use. I have been try to solve this problem via instructions given on different forums and threads. I have tried almost, i think, every step to enable graphics card, but failed. :(
Following is the error image while installing the drivers....(NVIDIA® GeForce® GT 540M with 2GB DDR3 VRAM, CUDA enabled).

I am using Asus k53sv 64 bit, ubuntu 10.04......and i need to run openFoam and paraview application.....

Thanks in anticipation for your suggestions and help.

---

### Post by 2F4U on 2012-07-26
Not sure what to tell you, but it seems as if indeed this version of the driver doesn't support your card:

[http://www.nvidia.com/object/linux-display-ia32-295.59-driver.html](http://www.nvidia.com/object/linux-display-ia32-295.59-driver.html)

---

### Post by bogan on 2012-07-26
Hi!,** aujamal20**,

According to Nvidia .com/downloads>Supported Products,  the GT540M card is included as one that is supported by the 295.59 driver; despite the error message you are getting, and its absence from the list in 2F4U's link.

Edit: Unfortunately. their Technical Development Help=Line is off-line at the moment, due to a hacking attack.

A: Are you sure that is the installed video card ? Please Post:```
 lspci -nnk | grep -iA3 VGA
```B: Was it working before you installed CUDA?

C: If you also have Windows installed , does it work OK there?

Chao!,** bogan.**

---

### Post by Marric on 2012-08-15
[http://ubuntuforums.org/showthread.php?t=2042259](http://ubuntuforums.org/showthread.php?t=2042259)
> **Marric said:**
> I'm also running Ubuntu 12.04 with the nvidia gt  520m optimus graphics card. Gave me quite some trouble to make the  graphics work after the installation. But it's working very good now  with Bumblebee [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee).  It keeps the card turned off at startup. To use the card for an application  is simple, just put "optirun" in front of the executing command (add it  to the desktop launcher) and the card is activated. Saves a great deal  of power too. To install it follow the link.
To see the nvidia config tool use
```
optirun nvidia-settings -c :8
```BUT do NOT save anything in the default file, you'll mess up X11.
Use this path to save the settings
```
/etc/bumblebee/xorg.conf.nvidia
```Test it```
glxspheres
optirun glxspheres
```Bumblebee Project FAQ [https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ](https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ)
For CUDA check Lekensteyn's post (member of the Bumblebee Project) [http://askubuntu.com/questions/131506/how-can-i-get-nvidia-cuda-or-opencl-working-on-a-laptop-with-nvidia-discrete-car](http://askubuntu.com/questions/131506/how-can-i-get-nvidia-cuda-or-opencl-working-on-a-laptop-with-nvidia-discrete-car)

---


---
title: "Sigh... Nvidia drivers..."
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by band-aid on 2007-04-20
I figured it would happen when I upgraded. It did when I recompiled my own kernel. My nvidia drivers have died... *sniff*. This time I am not going to fall back on scripts though. I would like to learn how to install them without the help of Automatix and Envy. I have installed:

nvidia-glx-dev
nvidia-glx
nvidia-kernel-common

I did dpkg-reconfigure and picked nvidia as my driver. Whenever I do startx I get this.

```

(EE) Failed to load /urs/lib/xorg/modules//libglx.so
(EE) Failed to load module "glx" (loader failed, 7)
(EE) NVIDIA(0):  Failed to initialize the GLX module; please check in your X log file that the GLS module is the NVIDIA  GLX module. If you continue to encounter problems, Please try reinstalling the NVIDIA driver.

```
There some more stuff after that but it appears that this libglx is the problem. What do you suggest I do? Thanks for the help. 
Band-aid

---

### Post by K.Mandla on 2007-04-20
If you really want to get into the nitty gritty of it, you could download the Linux driver from the Nvidia Web site. It's not nearly as complicated as it sounds; it has an installer program that does all the dirty work for you. It might even be necessary if you built your own kernel. 

Check it out [here]("http://www.nvidia.com/object/unix.html"). If you've compiled your own kernel, it'll be a piece of cake to get the Nvidia driver going. ;)

---

### Post by band-aid on 2007-04-20
Ok, it failed trying to compile the kernel module because GCC was a different version than the one used to compile the kernel. I know I'm being capt. Quitter but I REALLY don't feel like straightening all this out using lynx and a terminal. So, what do I need to grab off of apt-get to get this garbage working lol.

EDIT: I am not using a kernel I compiled right now. This is the kernel that install with the upgrade from edgy to feisty.

---


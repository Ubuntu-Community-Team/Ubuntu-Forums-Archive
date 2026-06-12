---
title: "Feisty Upgrade Hosed NVidia"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by WelterPelter on 2007-03-19
The title says it all. I've been keeping my NVidia up to date using tseliot's excellent "Envy" script. However, I found out the hard way that it doesn't yet support Feisty. 

I have gone through about four different full threads supposedly telling me how to get my NVidia up and running again, but none of them have worked. 

Does anyone have a recommendation for how to proceed? 

Thanks.

---

### Post by Monk-e on 2007-03-19
Using Synaptic:
1- Install the restricted modules for the installed kernel
2- Install nvidia-glx

Then use restricted driver manager (in system->preferences) to enable the drivers

And you should be done.

---

### Post by WelterPelter on 2007-03-19
> **Monk-e said:**
> Using Synaptic:
1- Install the restricted modules for the installed kernel
2- Install nvidia-glx

Then use restricted driver manager (in system->preferences) to enable the drivers

And you should be done.

Step three doesn't work if your X server is down. I've done steps 1 and 2 several times already.

---

### Post by WelterPelter on 2007-03-20
I'm now using vesa in order to at least be able to access my Desktop.

The xserver complains that it cannot load the nvidia-glx driver, although it's definitely installed.

---

### Post by bulldog on 2007-03-20
Boot in recovery mode and login in console.
Now perform the uname -a command to see your exact kernel [mine is 2.6.12-20-generic]
If you found your kernel type the next command,```
sudo aptitude install linux-restricted-modules-2.6.12-20-generic
```
After that is finished type,```
sudo aptitude install nvidia-glx
```

Reboot and it should be fine,if not try the reconfigure command,```
sudo dpkg-reconfigure xserver-xorg
``` and choose the nvidia driver.
You can edit the xorg.conf manually if you choose ```
sudo nano /etc/X11/xorg.conf
``` and make the driver "nvidia" instead of "nv"

If done and you can startx and GDM type in a terminal,```
sudo nvidia-settings
``` which allow you to set some configuration for your graphics.

---

### Post by garybrlow on 2007-03-20
Since your using envy it will install the official Closed source NVIDIA drivers from [http://www.nvidia.com](http://www.nvidia.com). It actually downloads, compiles and installs the NVIDIA driver for you. Normally you would do everything manually. The official NVIDIA drivers are bleeding edge and constantly updated while the  repo version is not. The problem with compiled driver installation is that you have to recompile every time the kernel is updated/upgraded. 

In the absence of Envy you have to manually download, compile, and install the driver yourself. Detailed information is found here [http://www.ubuntuforums.org/showthread.php?t=301499](http://www.ubuntuforums.org/showthread.php?t=301499). The Edgy instructions work the same for feisty. Its not really hard to compile the NVIDIA driver, it has a text based wizard and technically compiles and install itself interactively.  Make sure you install build-essential and linux-generic packages to make the compilation. Read the guide first before doing anything else.


Cheers!!!


GaryBrlow :biggrin:

---

### Post by WelterPelter on 2007-03-20
> **bulldog said:**
> Boot in recovery mode and login in console.
Now perform the uname -a command to see your exact kernel [mine is 2.6.12-20-generic]
If you found your kernel type the next command,```
sudo aptitude install linux-restricted-modules-2.6.12-20-generic
```After that is finished type,```
sudo aptitude install nvidia-glx
```Reboot and it should be fine,if not try the reconfigure command,```
sudo dpkg-reconfigure xserver-xorg
``` and choose the nvidia driver.
You can edit the xorg.conf manually if you choose ```
sudo nano /etc/X11/xorg.conf
``` and make the driver "nvidia" instead of "nv"

If done and you can startx and GDM type in a terminal,```
sudo nvidia-settings
``` which allow you to set some configuration for your graphics.

I did all this (and have done it many times already), but it keeps complaining that it cannot initialize the glx module. Of course I have downloaded the nvidia-glx module, so I am not sure why this is happening. 

Then it says that it failed to load the nvidia kernel module. 

I have checked several times, and I am using the correct kernel modules and restricted modules (it's for 2.6.20-12-386).

---

### Post by WelterPelter on 2007-03-20
> **garybrlow said:**
> Since your using envy it will install the official Closed source NVIDIA drivers from [http://www.nvidia.com](http://www.nvidia.com). It actually downloads, compiles and installs the NVIDIA driver for you. Normally you would do everything manually. The official NVIDIA drivers are bleeding edge and constantly updated while the  repo version is not. The problem with compiled driver installation is that you have to recompile every time the kernel is updated/upgraded. 

In the absence of Envy you have to manually download, compile, and install the driver yourself. Detailed information is found here [http://www.ubuntuforums.org/showthread.php?t=301499](http://www.ubuntuforums.org/showthread.php?t=301499). The Edgy instructions work the same for feisty. Its not really hard to compile the NVIDIA driver, it has a text based wizard and technically compiles and install itself interactively.  Make sure you install build-essential and linux-generic packages to make the compilation. Read the guide first before doing anything else.


Cheers!!!


GaryBrlow :biggrin:

I've done the compilation before (in the days before Envy). It worked fine. My understanding was that it isn't necessary to do that for Feisty, since it contains the driver already. Wrong?

---

### Post by rsambuca on 2007-03-20
I got mine to work by installing the restricted modules first, then nvidia-glx, then "sudo nvidia-glx-config enable"

---

### Post by WelterPelter on 2007-03-20
> **rsambuca said:**
> I got mine to work by installing the restricted modules first, then nvidia-glx, then "sudo nvidia-glx-config enable"

No go. Same problems as before. glx isn't loading.

---

### Post by bulldog on 2007-03-20
Try installing an older kernel and configure it.
Maybe it  will  work.

My generic kernels weren't working till the last two,and I used the i386 kernel instead.

---

### Post by WelterPelter on 2007-04-01
Just to guide this thread to completion, I'd like to comment that the latest updates (as of late March '07) completely cured my nVidia woes.

---

### Post by old_geekster on 2007-04-03
Here, try this guide:

[http://www.ubuntuforums.org/showthread.php?t=336412&highlight=Hub](http://www.ubuntuforums.org/showthread.php?t=336412&highlight=Hub)

I used this when I was in the Terminal when Feisty rebooted.  I simply typed the following:

sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run

I rebooted and it worked perfectly.

I have used this guide numerous times in the past month.  I reinstalled Edgy 13 times.  I used the guide each time.

---

### Post by rsambuca on 2007-04-03
> **old_geekster said:**
> I have used this guide numerous times in the past month.  I reinstalled Edgy 13 times.  I used the guide each time.13 times in a month?  Whatcha been doin?:shock:

---

### Post by old_geekster on 2007-04-04
> **rsambuca said:**
> 13 times in a month?  Whatcha been doin?:shock:
A clean install is my way of shortening the trouble-shooting process.:) 

At the time, I didn't know that much about Ubuntu and I can't keep from tweaking my OS.  This is a prescription for problems; especially for a newbie.  So, when I screwed things up --- I did a clean install.  Thus the 13 times in a month.

Two days ago I upgraded to Feisty.  Hopefully, I have learned enough to keep myself out of trouble.:) 

We'll see!:lolflag:

---


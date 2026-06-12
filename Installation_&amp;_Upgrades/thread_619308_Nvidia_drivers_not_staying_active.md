---
title: "Nvidia drivers not staying active"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by MrCrim on 2007-11-21
I downloaded NVIDIA's most recent drivers and installed them from runlevel 1 as root using the sh command as the recommendations on NVIDIA's site say. Upon returning to runlevel 3, everything worked fine and I was able to enable extra effects and everything. I shutdown last night and come this morning when I restart my computer, the system is no longer using the driver and doesn't list it as an option. I didn't have time to mess with it since I had to go to work so that's all I really know so far. The built in drivers in Ubuntu won't let me raise resolution beyond 800x600 or activate any extra effects. Anyone know why the drivers I installed didn't stick and how I can get them to? Also, do I have to reinstall them or how can I track them down again. My Linux skills are only at a beginner level so keep that in mind when offering suggestions.

-EDIT: BTW Running a Nvidia GeForce 6600

---

### Post by monktbd on 2007-11-21
did you use the ubuntu packages for the nvidia driver before and just wanted now the latest from the site?

i had the exact same problem when i switched on my old dapper from the last one available in the repositories to the newest on the nvidia site.
i solved the problem by uninstalling the ubuntu package first and then installing the nvidia  driver from nvidia directly.

unless you really need the latest nvdidia driver that might not be in the repositories i would recommend using the one in the repositories though.

---

### Post by MrCrim on 2007-11-21
As I said, very new to Linux, so I apalogize if this is a dumb question. You mean through the Synaptic Package Manager?

-EDIT No I didn't use the repository files first. I don't think.

---

### Post by monktbd on 2007-11-21
yes, synaptic is the graphical frontend for apt, apt-get, etc...
look for your nvidia drivers there after uninstaling the nvidia drivers you installed manually and try the package in synaptic.

---

### Post by MrCrim on 2007-11-22
So I tried removing the restricted driver and using the packaged driver and it doesn't want to use the 2d/3d acceleration. After rebooting it says it doesn't recognize my graphics hardware and makes me resetup everyting.

---

### Post by chaquira on 2007-11-22
hey, i got the same problem
i put vesa drivers instead of nv in my xorg.conf
it makes the system work, on the other hand, i cant do anything related to video
if i install the nvidia drivers from the site, it works perfectly, until i reboot
then the X doesnt even open...
the nvidia-glx packages in synaptic dont work either..
if you find the answer, please post it here

---

### Post by monktbd on 2007-11-23
i cannot remember properly anymore but i think that after uninstalling the driver with apt-get not everything got uninstalled. maybe the kernel module stayed.

below is my output for
>  sudo dpkg -l "nvidia*"

> 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
rc  nvidia-glx     1.0.8776+2.6.1 NVIDIA binary XFree86 4.x/X.Org driver
un  nvidia-glx-leg <none>         (no description available)
un  nvidia-glx-src <none>         (no description available)
un  nvidia-kernel  <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
rc  nvidia-kernel- 20051028+1     NVIDIA binary kernel module common files
un  nvidia-kernel- <none>         (no description available)
un  nvidia-setting <none>         (no description available)
un  nvidia-xconfig <none>         (no description available)


the problem for me was that the newest nvidia driver in the repos did not work with my older nvidia chipset anymore, that is why i had to install the driver from nvidia.com.

---


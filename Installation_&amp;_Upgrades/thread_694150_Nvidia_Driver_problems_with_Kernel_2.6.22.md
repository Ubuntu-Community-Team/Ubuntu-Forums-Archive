---
title: "Nvidia Driver problems with Kernel 2.6.22"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by Lgndryhr on 2008-02-11
I just updated to version 7.10 of Ubuntu. Along with the update I gained the new kernel 2.6.22-14-386 and 2.6.22-14-generic. Well upon restarting, which has been broken since I have been on 6.10 so I just shut off and re-turn on manually. I go to load the newest kernel and from here things differ from the last kernel I was on, 2.6.17-12-386.

 I am not able to see the usual loading screen but instead a black screen with a blinking cursor that is not in the right resolution either. It would usually load with correct resolution and show loading of necessary things with "[OK]" across from it and fsck also would be used I believe when loading.  It then loads to either of the following: telling me it's loading into low-graphics mode and asks me what to do OR loads to login screen with a resolution that is not what it was before, which is also now messed up on 2.6.17 kernel as well. I know I have to reconfig the driver for new kernels but I am not able to due to when I hit ALT+CTRL+F2 (any number from 1 to 5 or so I think) so I can stop GDM and install said driver, which is 169.09 Nvidia Driver for a GeForce FX 5700 LE. I come to a black screen with a blinking cursor like before when I boot into 2.6.22 kernel. 

So basically I am lost as to what to do. Any help would be greatly appreciated. I am still sort of new to Ubuntu too so sorry if I am missing something simple here. Oh yea also, I dual boot using GRUB and 2 hard drives. One has Windows XP and the other has Ubuntu.

---

### Post by Partyboi2 on 2008-02-12
Have you tried booting into recovery? If so, same results?

---

### Post by Lgndryhr on 2008-02-12
> **Partyboi2 said:**
> Have you tried booting into recovery? If so, same results?

Am not am my computer right now but did try this. I was able to be in terminal with X not started but upon trying to compile the driver I had 2 problems. The first problem was something about me not being in the correct level -- i believe i was level 1 and it wanted level 3 or maybe vice versa. cant remember since i am not at my computer currently. --  but could still continue installation, which i did. Then I was not able to connect to the internet for some reason at all on this kernel, 2.6.22, or even before. This hindered me from being able to connect to the server to compile and find a kernel, module -- i think --  or something to the extent.

---

### Post by Lgndryhr on 2008-02-12
bump.

---

### Post by Lgndryhr on 2008-02-12
anyone's advice would be greatly appreciated.

---

### Post by jimk0512 on 2008-02-12
I have the identical problem that you have. The update to Ubuntu 2.6.20-14 broke my system. It now continuously boots into low graphics mode.

---

### Post by Lgndryhr on 2008-02-12
> **jimk0512 said:**
> I have the identical problem that you have. The update to Ubuntu 2.6.20-14 broke my system. It now continuously boots into low graphics mode.

Ah yes I had that problem back when I was on 7.04 using 2.6.20 excpet that I couldn't even get X to start at all or even compile the driver for 2.6.20. Upon updating 7.10 the update manager removed 2.6.20 and installed 2.6.22. Now I have the problem I do now.

---

### Post by Lgndryhr on 2008-02-14
bump. anyone's help would be greatly appreciated.

---

### Post by xekon on 2008-02-14
I can say that when the computer boots into low graphics if you cant get past that change it from the 800x600 to 640x480 and it will load, this of coarse is not a fix but atleast you can get to your GUI of the OS. I am still looking for this fix myself.

---

### Post by xekon on 2008-02-14
OK so I was a normal Envy user and while its a great tool it just wasnt working for me It would install the nvidia driver then I would restart and turn compiz back on and it would turn around and uninstall the driver that envy just got finished installing and I would have to run in a resolution of 640x480 in order to get the Ubuntu GUI to load.

below is what I did NOTE make sure to follow the right case, this is Case sensative.

I booted into ubuntu and had to set my resolution to 640x480 to get it to load.

first:
```
sudo apt-get install build-essential
```

second (case sensative):
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.09/NVIDIA-Linux-x86-169.09-pkg1.run
```

third:
```
gksudo gedit /etc/default/linux-restricted-modules-common
```
add both  "nv " and "nvidia_new" to the Line at the bottom, not the example shown at the top of the file.
```
DISABLED_MODULES="nv nvidia_new" 
```
Save and exit

fourth press ctrl+alt+F1 for the command line then type (case sensative):
```

sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-169.09-pkg1.run

```

The following line I just clicked next through everything except the part where you pick the driver, I selected "nvidia" and then the part where you select the resolutions.
```
sudo dpkg-reconfigure xserver-xorg
```

```
sudo /etc/init.d/gdm start
```

Then after restarting I renabled compiz by going to System > Preferences > Appearance and selecting custom

Then renabled the options you want in the compiz manager

---


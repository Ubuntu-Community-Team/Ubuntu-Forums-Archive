---
title: "How To Install Nvidia 260.19.12 drivers in Ubuntu 10.10"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by legionarius on 2010-10-14
Hello! I have got to install nvidia 260.19.12 drivers in ubuntu 10.10 64 bit. I have got a GTX 460, so I think these are the right drivers [http://www.nvidia.co.uk/object/linux-display-amd64-260.19.12-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-amd64-260.19.12-driver-uk.html)
The question is: how do I download and install 260.19.12 drivers? I would need a step by step guide, because I'm not familiar at all with Ubuntu, so it can be difficult for me, even if I will try my best.
Thanks in advance.

---

### Post by efflandt on 2010-10-14
Nevermind, I had replied thinking you were looking for default 260.19.06 and did not notice the .12

---

### Post by ncohea on 2010-10-15
As it turns out, proprietary drivers are annoying. I look forward to a robust open source driver implementation of OpenGL 4.1.

I have tried installing these drivers as well, and I have had great difficulty. I am putting together an xorg log and a kernel log, and I might post a new thread soon. 

The normal procedure to install the driver is to check Synaptic to make sure the packages linux and linux-source are installed. If not, you must install them. This is because installation of the nVidia driver involves compiling the module against the kernel. Print these instructions out. Open a terminal and type
```
sudo /etc/init.d/gdm stop
sudo ./NVIDIA-Linux-x86_64-260.19.12.run -a
sudo /etc/init.d/gdm start
```
Note that this will stop your X server which will also mean you have no GUI. (Which is why I say print these instructions out.) The first command will drop you to a tty1 console, so enter your username and password to log in. Running the second command installs the driver module, in theory. The last command will restart your X server, in theory.

The steps I have been following include booting to the recovery mode by selecting the second option in grub and choosing the netroot console. Then I tried
```
telinit 3
sudo apt-get remove nvidia-current
sudo ./NVIDIA-Linux-x86_64-260.19.12.run -a
sudo shutdown -r now
```

Either of those options might work for you. If they do work, it would be cool to hear about it. If the second one does not work, I will not have destroyed your computer as you can always rollback into a working system with

```
sudo ./NVIDIA-Linux-x86_64-260.19.12.run --uninstall
sudo apt-get install nvidia-current
```

Also, if you just install nvidia-current and ignore all this garbage, you will still have driver version 260.19.06, which is pretty damn current, whereas 260.19.12, the subject of this thread, came out yesterday.

Is there any particular reason you require 260.19.12? (In my case, it's because I want to do OpenCL development.)

---

### Post by legionarius on 2010-10-15
Thank you very much for the reply ncohea. I've installed them in a slightly different way (I hope I have not committed mistakes).
Yeah I really needed to install 260.19.12 drivers, because when I installed the drivers ubuntu suggested me to install (System - Admininstration - Additional Drivers), a huge problem has happened (after a few seconds a red screen appeared, and I had to shut down the pc turnning the power supply unit off). Here is the post that explains my problem: [http://ubuntuforums.org/showthread.php?t=1595509](http://ubuntuforums.org/showthread.php?t=1595509)
Fortunately I think I've definitively solved the problem with 260.19.12 drivers. Thank you again for the reply ncohea :)

---

### Post by kuckunniwi on 2010-10-17
> **ncohea said:**
> As it turns out, proprietary drivers are annoying. I look forward to a robust open source driver implementation of OpenGL 4.1.

I have tried installing these drivers as well, and I have had great difficulty. I am putting together an xorg log and a kernel log, and I might post a new thread soon. 

The normal procedure to install the driver is to check Synaptic to make sure the packages linux and linux-source are installed. If not, you must install them. This is because installation of the nVidia driver involves compiling the module against the kernel. Print these instructions out. Open a terminal and type
```
sudo /etc/init.d/gdm stop
sudo ./NVIDIA-Linux-x86_64-260.19.12.run -a
sudo /etc/init.d/gdm start
```
Note that this will stop your X server which will also mean you have no GUI. (Which is why I say print these instructions out.) The first command will drop you to a tty1 console, so enter your username and password to log in. Running the second command installs the driver module, in theory. The last command will restart your X server, in theory.

The steps I have been following include booting to the recovery mode by selecting the second option in grub and choosing the netroot console. Then I tried
```
telinit 3
sudo apt-get remove nvidia-current
sudo ./NVIDIA-Linux-x86_64-260.19.12.run -a
sudo shutdown -r now
```

Either of those options might work for you. If they do work, it would be cool to hear about it. If the second one does not work, I will not have destroyed your computer as you can always rollback into a working system with

```
sudo ./NVIDIA-Linux-x86_64-260.19.12.run --uninstall
sudo apt-get install nvidia-current
```

Also, if you just install nvidia-current and ignore all this garbage, you will still have driver version 260.19.06, which is pretty damn current, whereas 260.19.12, the subject of this thread, came out yesterday.

Is there any particular reason you require 260.19.12? (In my case, it's because I want to do OpenCL development.)

Do you know if this would work on Kubuntu 10.10? (sorry, newbie here)

---

### Post by FerhatBingol on 2010-10-18
worked perfect on my GeForce 7600 GS, thank you...

---

### Post by element23 on 2010-10-21
I have Nvidia 8200M G & I've installed the NVidia 260.19.12 drivers as per the PPA method mentioned here on Webupd8 [http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html]("http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html")
After installing the driver performs terrible. Compiz cube looks garbled, animation is sketchy, etc. I've used past nvidia drivers on 10.04 32bit when it was first released and they worked a lot better then. Please help :(:confused:

Compaq Presario CQ50-215NR
AMD Athlon X2, 2GB Ram 
NVidia 8200M G
Ubuntu 10.10 64bit

---

### Post by Calgary-Mark on 2010-10-21
I am installing on a HP With a GeForce 9500 GT, Downloading all the new drivers for NVIDIA, but still no go.  I have tried everything in this tread and its still not going, anyone have any other advice?
 
:(

---

### Post by kkaldroma on 2010-10-22
After stopping gdm I am stuck looking at my background.
I get no terminal.

I have tried booting into xterm and killing gdm from there, 
I have tried from the gnome-terminal,
I have tried removing gdm from rc.d,

I can't figure out how to get to the damn terminal.

---

### Post by kkaldroma on 2010-10-22
OK, I got to the terminal by removing gdm.... 
```
sudo apt-get remove gdm
```
There has to be a right way to do this?

---

### Post by fallenshadow on 2010-10-23
You might want to reinstall gdm.

sudo apt-get install gdm.

Now you dont need to go and uninstall gdm. An easy way to get to a terminal at boot up is to hold shift when your PC is booting.

This brings up a recovery menu. Select root terminal from this menu.

---

### Post by Pconfig on 2010-10-23
You might want to try ctrl+alt+F3..

---

### Post by seenthelite on 2010-10-23
This is an alternate way to stay up to date with Nvidia Drivers.

[http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

---

### Post by Cavsfan on 2010-12-20
> **seenthelite said:**
> This is an alternate way to stay up to date with Nvidia Drivers.

[http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

The only problem with this is that the new driver will not automagically be installed in a new kernel. Believe me, I tried having this PPA 
and got a beta nvidia driver and none of my kernels would boot up. I figured out that there has to be a way to install the driver into the 
kernel when one gets added. So, I decided to stay with the same version of the nvidea driver and go by this tutorial:
[[COLOR=blue]_HOWTO: Automatically update manually installed NVidia drivers after kernel updates_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=835573")

Mixing the PPA with this method will cause problems. I have the latest nvidia driver 260.19.29 installed and just got a new kernel 
this morning and it was installed into the kernel without any problem.
You see a message "Building NVIDIA driver for kernel xxxx" and then after that you should see "SUCCESS: Driver installed for kernel xxxx".

I don't like beta video drivers myself.

---

### Post by brainbuz on 2010-12-20
I'm trying to install an older GEForce 440 (requires [96.43.19 legacy driver). ]("http://www.nvidia.com/object/linux-display-ia32-96.43.19-driver.html")

To install get in the system at all it requres adding nomodeset and forcevesa during boot prompt. After stopping gdm to install the drivers I keep encountering dependcies.

So far I've gotten:
binutils
cc
and now it wants kernel source, so now what's the best way to get the source for the stock kernel installed on the machine. [at the moment I'm working in Lucid because I wanted to try an older version to see if I had better luck on install with it, but I will reinstall Maverick once I figure this out]. 

Does anyone know what it will ask for next?

---

### Post by Cavsfan on 2010-12-20
> **brainbuz said:**
> I'm trying to install an older GEForce 440 (requires [96.43.19 legacy driver). ]("http://www.nvidia.com/object/linux-display-ia32-96.43.19-driver.html")

To install get in the system at all it requres adding nomodeset and forcevesa during boot prompt. After stopping gdm to install the drivers I keep encountering dependcies.

So far I've gotten:
binutils
cc
and now it wants kernel source, so now what's the best way to get the source for the stock kernel installed on the machine. [at the moment I'm working in Lucid because I wanted to try an older version to see if I had better luck on install with it, but I will reinstall Maverick once I figure this out]. 

Does anyone know what it will ask for next?

Try looking in Synaptic for the source of the kernel you are using. I installed linux-source-2.6.35 and linux-tools-2.6.35-24 for Maverick and probably some others.
That 1st one for your kernel might be all you need. 
Also, I would pose a question to drs305 about where you put "nomodeset and forcevesa" in your GRUB2. Here is the thread: [[COLOR=blue]_drs305's GRUB2 Basics_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")
Hope this helps!

---


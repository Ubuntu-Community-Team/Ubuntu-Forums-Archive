---
title: "Nvidia drivers fails with Feisty upgrade"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by globemast on 2007-06-09
Hello,

Yesterday i upgraded my Edgy distribution to the Feisty distr. through the Update Manager.


When the PC rebooted ...(using the new kernel: 2.6.20-16-generic ) , X failed to start due to the Nvidia drivers.

I knew this would happen since i am using the drivers from Nvidia site. This happened to me every time i upgraded the kernel but i always fixed it by unistalling and installing/compiling the Nvidia drivers for the new kernel.

This time though, this procedure does not work. I tried to compile the drivers for  kernels **2.6.20-16-generic** and** 2.6.20-15-generic **but it failed.

The only time X seems to work, is when i boot from kernel : **2.6.20-15-386** and compile the drivers for this kernel. (HINT: for generic kernels the driver fails)

Any suggestions to fix this problem?

P.S. The graphics card in a** NVIDIA 7300GT** and the driver is: **NVIDIA-Linux-x86-1.0-9755-pkg1**


Thanks in advance.

---

### Post by Pumalite on 2007-06-09
> **globemast said:**
> Hello,

Yesterday i upgraded my Edgy distribution to the Feisty distr. through the Update Manager.


When the PC rebooted ...(using the new kernel: 2.6.20-16-generic ) , X failed to start due to the Nvidia drivers.

I knew this would happen since i am using the drivers from Nvidia site. This happened to me every time i upgraded the kernel but i always fixed it by unistalling and installing/compiling the Nvidia drivers for the new kernel.

This time though, this procedure does not work. I tried to compile the drivers for  kernels **2.6.20-16-generic** and** 2.6.20-15-generic **but it failed.

The only time X seems to work, is when i boot from kernel : **2.6.20-15-386** and compile the drivers for this kernel. (HINT: for generic kernels the driver fails)

Any suggestions to fix this problem?

P.S. The graphics card in a** NVIDIA 7300GT** and the driver is: **NVIDIA-Linux-x86-1.0-9755-pkg1**


Thanks in advance.

That should work for you independent of the kernel, but you have to make sure you have the right kernel-source or headers for your new kernel. Besides I'm sure you know you need: gcc, make, automake, autoconf. The procedure I follow is: go to init 3, become root and then: sh /path/to/driver/NVIDIA-Linux-x86-1.0-9755-pkg1.run.

Good luck.

---

### Post by Paulo79 on 2007-06-09
You have to disable the restricted module that comes with ubuntu. Otherwise the wrong module will be loaded in the kernel.

See file /etc/default/linux-restricted-modules-common and change the line

DISABLED_MODULES=""

to:

DISABLED_MODULES="nv"

Now re-install the driver you downloaded from Nvidia's web site.

---

### Post by globemast on 2007-06-11
I tried disabling the restricted modules as mentioned above but no luck.


Any suggestions???

---

### Post by globemast on 2007-06-11
This is my Xorg log file for reference. 

The log file was created when running kernel **2.6.20-16-generic** with compiled Nvidia drivers version 1.0-9755

---

### Post by globemast on 2007-06-11
Sorry forgot to attach file... file is now attached.

---

### Post by Pumalite on 2007-06-11
> **Paulo79 said:**
> You have to disable the restricted module that comes with ubuntu. Otherwise the wrong module will be loaded in the kernel.

See file /etc/default/linux-restricted-modules-common and change the line

DISABLED_MODULES=""

to:

DISABLED_MODULES="nv"

Now re-install the driver you downloaded from Nvidia's web site.

The NVIDIAxxx.run file does that automatically if you haven't done it yet.

---

### Post by Pumalite on 2007-06-11
> **globemast said:**
> Sorry forgot to attach file... file is now attached.

After you download your NVIDIA Driver and place it in /home/<username>, you get out of xterm, run the file with sh /path/to/driver/NVIDIA.xxxxx.run. It does everything automatically for you; including removing old drivers if you haven't done it and reconfiguring your xorg file. If it doesn't work for you, please state the errors that you encountered or copy and paste.

---

### Post by globemast on 2007-06-12
Hi Pumalite,

I have used the Nvidia drivers as i mentioned above. The Xorg.log file that i attached above is the errors that i get when X Server tries to start.

---

### Post by globemast on 2007-06-12
Today i tried installing Nvidia's new drivers (NVIDIA-Linux-x86-100.14.09-pkg1.run) with kernel 2.6.20-16-generic.

I also disabled the "nv" and "nvidia_new" restricted modules.

Again this doesn't work and the error that i get is the following:

```

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select, nvidia-auto-select"
(**) NVIDIA(0): Option "LoadKernelModule" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

```

---

### Post by Pumalite on 2007-06-12
> **globemast said:**
> Today i tried installing Nvidia's new drivers (NVIDIA-Linux-x86-100.14.09-pkg1.run) with kernel 2.6.20-16-generic.

I also disabled the "nv" and "nvidia_new" restricted modules.

Again this doesn't work and the error that i get is the following:

```

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select, nvidia-auto-select"
(**) NVIDIA(0): Option "LoadKernelModule" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

```

Why are you not installing 9755? Also make sure your kernel headers match your new kernel.

---

### Post by globemast on 2007-06-13
I tried also with the 9755 Nvidia drivers but still no luck.


if i install the driver manually, with the following command

```

sudo insmod /lib/modules/2.6.20-16-generic/kernel/drivers/video/nvidia.ko 

```

then everything works fine .

---

### Post by willcox on 2007-06-13
Hi!
  You may want to read this,  total success here.
[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

---

### Post by globemast on 2007-06-14
Hi willcox,

Been there, done that :) :p

No result :)

---

### Post by EtanSivad on 2007-06-14
Hi Globemast,

I had this exact issue about ten minutes ago.  The solution is really odd.
Apprently when you uninstall the Nvidia drivers that ubuntu installs, it leaves behind one file: /lib/linux-restricted-modules/.nvidia_new_installed.
The solution for me anyway:
(After I uninstalled the restricited drivers as you did earlier, And I installed the newest nvidia drivers)

sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
modprobe -r nvidia
startx

(Startx will test it right from that terminal - it worked for me)

You can read about the bug [here]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217").

Hope that helps.

---


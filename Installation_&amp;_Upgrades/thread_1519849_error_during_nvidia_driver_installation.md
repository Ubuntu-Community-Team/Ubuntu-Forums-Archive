---
title: "error during nvidia driver installation"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by nebu1a on 2010-06-28
i need help to install the nvidia driver in my new laptop.
 i have a nvidia geforce gt 330m and ubuntu 10.4 (64 bit).

without the driver, the monitor is set by default with 2000x... (more or less, i don't remember), but with this configuration part of the screen is out of the monitor.
when i set the correct resolution (1920x1080), the dysplay becomes too tight.

when i use the ubuntu nvidia drivers, the system crashes at the startup.

i downloaded the drivers from the nvidia website, but i think i made some mistakes triyng to install them.

at the startup, i chose a command line session, using ```
telinit 3
```
the i gave the command ```
sudo sh nvidia[...].run
```
(*nvidia[...].run* is the name of the driver).

then, errors begin to appear. the first one:
> the distribution-provided pre-install script failed! continue installation anyway?
i tried to continue anyway, but a second error was waiting for me:
> error: unable to find the kernel modile 'nvidia.ko'. this happens most frequently when this kernel is built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build kernel, or if a driver suche as rivafb/nvidiafb is present and prevents the nvidia kernel module from obtaining the ownership of the nvidia graphic device(s), or nvidia gpu installed in thi system is not supported by this nvidia linux driver release.
please see the log entries 'kernel module load error' and 'kernel messages' at the end of the file '/var/log/nvidia-installer.log' for more informations.
i don't even know what it means...

what can i do?

thanks

---

### Post by HomeSlixe on 2010-06-28
Have you  removed nouveau?```
sudo apt-get --purge remove xserver-xorg-video-nouveau 
```

---

### Post by HomeSlixe on 2010-06-28
also check this out! 

[http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+driver](http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+driver)

---

### Post by nebu1a on 2010-06-29
thank you homeslixe, i have finally installed the nvidia driver.
but...
new error!!!
or, to be more precise, the same error that occured using the ubuntu nvidia driver:
> (EE) jun 27 18:47 nvidia(0) no display devices found for this x screen.
(EE) screen(s) found, but none have a usable configuration.

i couldn't find anything helpful...

---

### Post by HomeSlixe on 2010-06-29
make sure you are using the right driver for your card and all other nvidia drivers are purged (including nouveau)... if that doesn't work maybe consider reinstalling xorg and if that doesnt work a new kernel.

---

### Post by HomeSlixe on 2010-06-29
have you tried using synaptic to install the driver... it may not be as bleeding edge as the driver on nvidias webpage but it still works good!

---

### Post by nebu1a on 2010-07-02
mmm... the main problem is that i'm not that skilled...
i reinstalled xorg by synaptic, but it didn't work.

about reinstalling the kernel, could you give me a link with some instructions?

i also have a new doubt. i read in the driver documentation:
> Installing the Kernel Interface

The NVIDIA kernel module has a kernel interface layer that must be compiled specifically for each kernel. NVIDIA distributes the source code to this kernel interface layer.

When the installer is run, it will check your system for the required kernel sources and compile the kernel interface. You must have the source code for your kernel installed for compilation to work. On most systems, this means that you will need to locate and install the correct kernel-source, kernel-headers, or kernel-devel package; on some distributions, no additional packages are required.

After the correct kernel interface has been compiled, the kernel interface will be linked with the closed-source portion of the NVIDIA kernel module. This requires that you have a linker installed on your system. The linker, usually /usr/bin/ld, is part of the binutils package. You must have a linker installed prior to installing the NVIDIA driver.

if i need something more than the basic installation of 10.4 i think i miss it.

ps. i checked, it's the right driver.

---

### Post by HomeSlixe on 2010-07-02
try this in terminal  ```
sudo nano /etc/modprobe.d/blacklist.conftv 
``` Add these:


blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

Then...

ctrl O to write
crtl X to quit

```
sudo apt-get --purge remove nvidia-*

``````
sudo apt-get install nvidia-current
```

---

### Post by HomeSlixe on 2010-07-02
If you at all uncomfortable with command based installing the synaptic package manager does a great job! also when you first install Ubuntu you will notice that it will ask you to install proprietary hardware drivers... there will include your Nvidia drivers and it will install them flawlessly.

---

### Post by davidmohammed on 2010-07-02
> **nebu1a said:**
> thank you homeslixe, i have finally installed the nvidia driver.
but...
new error!!!
or, to be more precise, the same error that occured using the ubuntu nvidia driver:


i couldn't find anything helpful...


remove the file /etc/X11/xorg.conf

then regenerate it via

gksudo nvidia-settings

reboot

---

### Post by nebu1a on 2010-07-03
> **HomeSlixe said:**
> try this in terminal  ```
sudo nano /etc/modprobe.d/blacklist.conftv 
``` Add these:


blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

Then...

ctrl O to write
crtl X to quit

```
sudo apt-get --purge remove nvidia-*

``````
sudo apt-get install nvidia-current
```
is blacklist.conftv a new file? it opened a blank screen.
in the link(s) you posted me they used blacklist.conf
however, it didn't work...](*,)

> **davidmohammed said:**
> remove the file /etc/X11/xorg.conf

then regenerate it via

gksudo nvidia-settings

reboot

answer after gksudo nvidia-settings:
> (gksudo: 1583) gtk-warning **: cannot open display:

and at the reboot, the usual errors...

---

### Post by HomeSlixe on 2010-07-03
sorry its not .conftv its just .conf

---

### Post by HomeSlixe on 2010-07-03
if you have the nvidia driver from the website already downloaded follow the terminal commands i showed you (taking note of my typo :p)and instead of using nvidia-current just sh NVIDIA-blah-blah-version since it looks like you are not in a GUI environment any ways just do everything in the terminal for now and it should work. once again befor you do any nvidia installing by hand remove nouveau first. 

sudo apt-get --purge remove xserver-xorg-video-nouveau

---

### Post by nebu1a on 2010-07-04
to be sure i didn't forgot anything, i purged again nouveau and any nvidia stuff previously installed.
i checked again in the blacklist file, and everything was correctly blacklisted (usbmouse, usbkbd, cepro100, de4x5, eth1394, snd_intel18x0m, snd_aw2, i2c_i801, prism54, bcm43xx, garmin_gps, asus_acpi, snd_pcsp and pcspkr are also blacklisted).
i downloaded again the driver, and i reinstalled it. i also selected "yes" when the installing script told me if i wanted a 32 bit interface.

and still doesn't work...

---

### Post by HomeSlixe on 2010-07-04
the question may seem a little inane but are you using a 32 bit system?

---

### Post by nebu1a on 2010-07-04
if you knew what i am able to, you wouldn't call this question inane...

however, i have a 64 bit system. i installed also that 32 bit interface because i don't know what it is, maybe an interface for old softwares?

---

### Post by HomeSlixe on 2010-07-05
Have you tried them both or just the 32 bit  driver? That may be what's wrong. If not the link to the driver you need can be found here:

[http://www.nvidia.com/object/linux-display-amd64-256.35-driver.html](http://www.nvidia.com/object/linux-display-amd64-256.35-driver.html)

---

### Post by nebu1a on 2010-07-05
no, i tried the **64 bit** driver, and after the installarion i chose "yes" when the software asked me if i wanted the 32 bit interface.

---

### Post by HomeSlixe on 2010-07-05
have you tried using the Ubuntu nvidia-current repository driver?

---

### Post by nebu1a on 2010-07-06
yes, i did.
i noticed i haven't written the last error yet, that is the error i have seen at the startup since i managed to install the driver.
here it is:
> (ee) nvidia: failed to load the nvidia kernel module, please check your system's kernek for additional error messages.
(ee) failed to load module "nvidia" (module-spercific error, 0)
(ee) no drivers available.


ps. the driver i installed is the correct one, gt330m for a vpcf11m1e/h vaio ([http://www.sony.co.uk/product/vn-f-series/vpcf11m1e-h](http://www.sony.co.uk/product/vn-f-series/vpcf11m1e-h))

---

### Post by HomeSlixe on 2010-07-06
can u show me your xorg.conf?

---

### Post by HomeSlixe on 2010-07-06
> **davidmohammed said:**
> remove the file /etc/X11/xorg.conf

then regenerate it via

gksudo nvidia-settings

reboot

have you tried this too? remember to sudo before punching thses commands in 

```
sudo rm /etc/X11/xorg.conf
```
```
gksudo nvidia-settings
```

---

### Post by HomeSlixe on 2010-07-06
If you want I can SSH into your computer and see if I can get it to work for you

---


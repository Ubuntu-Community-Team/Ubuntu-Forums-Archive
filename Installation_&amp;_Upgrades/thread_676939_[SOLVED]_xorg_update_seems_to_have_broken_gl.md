---
title: "[SOLVED] xorg update seems to have broken gl"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by danzinho on 2008-01-24
Hi

Quite unexpectedly a graphic-intensive program that was running happily now crashes my Gnome windows manager.  I can also crash the WM if I go into Nvidia X Server Settings and try to access information about gl/glx.  I have no proof that it is the origin of the problem, but I recall that I allowed some minor xorg updates via Synaptic recently.  This seems too much to be coincidence.

Has anyone else seen this, or can anyone offer advice?  I've always taken the nvidia installer approach to drivers.  Might it help to try a more recent version than NVIDIA-Linux-x86-1.0-8776-pkg1.run?

Any help much appreciated

Dan

---

### Post by PmDematagoda on 2008-01-24
Could you please post the specifications of your PC.

---

### Post by danzinho on 2008-01-24
Thanks for the quick reply

It's a Dell Precision 650 (2 x Xeon, 2GB) with 64 MB nVIDIA card
Graphics processor NVS 280 SD running driver version 1.0-8776

xorg.conf contains

Section "Device"
    Identifier     "NVIDIA Corporation NV18GL [Quadro4 NVS AGP 8x]"
    Driver         "nvidia"
EndSection

/proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) CPU 2.66GHz
stepping        : 7
cpu MHz         : 2658.413
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no

/proc/version
Linux version 2.6.17-12-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 18 02:12:38 UTC 2007 (Ubuntu 2.6.17-12.42-generic)


Is that enough to help the diagnosis?

Many thanks again

---

### Post by PaulJD on 2008-01-26
I am running Edgy 64-bit (still) with an NVidia card. Just rebooted for the first time in weeks and have the same symptoms. Looking back through History in Synaptic Package Manager I can´t see any obvious culprits in recent updates.

The error at the time in daemon.log is:
Jan 26 13:37:04 merope gdm[9594]: Error reinitilizing server

grep EE /var/log/Xorg.0.log gives me:
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.

I going to try installing the latest NVidia driver (currently running 100.14.11)... and will report back.

Some time later:
Decided to just reinstall current driver as simplest option (using NVidia installler):  NVIDIA-Linux-x86_64-100.14.11-pkg2.run
Error on opting to install 32-bit compatible OpenGL libraries about missing link. Looks like this was the actual problem and the simplest fix is to put this back, as per this thread: [http://ubuntuforums.org/showthread.php?t=671261&highlight=nvidia+opengl+crash](http://ubuntuforums.org/showthread.php?t=671261&highlight=nvidia+opengl+crash)
but reinstall worked fine too.

---

### Post by Protoss on 2008-01-26
Just thought I'd chime in that I am suffering from the same problem. I can get to some sort of functional desktop by changing my Session to XFCE, but if I try to run anything under Wine, or view the GL/GLX info in nvidia-settings, I get kicked back to the login screen.
I just downloaded the new driver (169.09) from nvidia.com and installed it and everything is back and functional.

---

### Post by danzinho on 2008-01-28
Many thanks to PaulJD for tracking down a thread that had already solved this problem.  He and 'protoss' found that driver reinstallation worked.  I tried the other route of

cd /usr/lib/xorg/modules/extensions/
sudo cp libglx.so libglx.so.back
sudo rm libglx.so
sudo ln -s libglx.so.xxxx.xxxx libglx.so

[in my case sudo ln -s libglx.so.1.0.8776 libglx.so]

and it works a treat!

Thanks again!

---


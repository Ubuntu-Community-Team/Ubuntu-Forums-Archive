---
title: "Install everything in SERVER ubuntu"
date: 2005-07-08
forum: Installation &amp; Upgrades
---

### Post by KLG on 2005-07-08
After many many failed attempts to install ubuntu in my laptop 
[http://www.ubuntuforums.org/showthread.php?t=47220](http://www.ubuntuforums.org/showthread.php?t=47220)

i tried installing in server mode, and it worked \\:D/ 

do i have any chance installing everything? or i should continue trying installing the "normal" mode?


[EDIT] -last update-
after installing server mode, and unpacking packages manually it crashes in xserver display configuration screen... even in 640x480

---

### Post by defkewl on 2005-07-08
Perhaps there are something wrong with your installation CD. Try downloading it once more.

---

### Post by KLG on 2005-07-08
thank u for your response but as u have explained in the other thread i have downloaded twice and checked with md5 checksums... after 10-15 attempts i am sure that nothing else can be done

---

### Post by WildTangent on 2005-07-08
to install the other packages, "sudo apt-get install ubuntu-desktop" i dont think you need to enable the repos for it, its not in universe

-Wild

---

### Post by KLG on 2005-07-09
i' ve tried it but when it comes to configure display resolution in xserver-xorg and i chose 1024x768 it crashes again. this resolution works fine in LiveCD...

---

### Post by mohaham on 2005-07-09
what are your system specs..
and what graphics card do you have (NVIDIA or ATI)..

---

### Post by KLG on 2005-07-09
Laptop specifications (FJS Amilo M3438G)
Intel Pentium M Processor 750
1.86GHz,2MB L2 cache,533MHz FSB
1024MB RAM
80GB+80GB SATA Hdisks
Ge Force Go 6800 256MB DDR1  Nvidia
-----------------
I also made an attempt at 680x480 with the same disapointing results...

I suspect i must install the nvidia drivers, in server mode , but i am completely newbie... do u have any advice to spare?

---

### Post by mingus on 2005-07-09
[QUOTE=KLG]
Ge Force Go 6800 256MB DDR1  Nvidia

I suspect i must install the nvidia drivers, in server mode[/QUOTE]

Hello again, KLG . . . maybe, maybe not.  There is a generic nvidia video driver already with the kernel.  Do dpkg-reconfigure xserver-xorg; the "nv" driver should be autodetected, but if it is not, configure it.  You may be sent to a sub-screen asking you to indicate which nvidia card this is for.  When you come to screen resolution, choose 800x600; for the default color depth choose 15; for the frame-buffer choose [no].  You can change these settings later; for now you are just trying to get the driver working.  Reboot.

In a terminal, $lspci should show you the nvidia device detected.  And $lsmod should show you the nvidia modules loaded; for example, look for "nvidia_agp".

I believe the additional nvidia drivers in the repository (or downloaded from the nvidia website) are for hardware acceleration and additional control.

---

### Post by KLG on 2005-07-09
YES YES!!!!

when i run $lspci I saw "Nvidia compatible controller,,,,, unknown device"

then i installed nvidia manually:

"sudo apt-get install nvidia-glx"

then installed ubuntu desktop and in xserver-xorg resolution screen i chose only 800x600 as u suggested.... 

it worked! the installation proceeded... i typed startx (thank god i have an Red hat 5.2 manual, so i can do the basics) and here i am. Everything is very big in 640x480, but i dont mind :D, i'll find a way to step to 1440x900 :DDD

Thanks for for your help mingus, couldn't have done without you

---

### Post by mingus on 2005-07-10
*Everything is very big in 640x480, but i dont mind, i'll find a way to step to 1440x900*

Give a try at dropping the default color depth; you may get higher resolution with a smaller color palette.

*Thanks for for your help mingus, couldn't have done without you*

Happy to have been of some help . . .

---


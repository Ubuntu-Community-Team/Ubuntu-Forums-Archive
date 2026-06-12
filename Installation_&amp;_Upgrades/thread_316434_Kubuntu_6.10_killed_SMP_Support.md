---
title: "Kubuntu 6.10 killed SMP Support"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by greylica on 2006-12-10
I'm having a problem to reenable smp support to my machine. 6.06 was very fine but when I did a upgrade to 6.10 a nightmare starts. Until generic kernel modules was up and I'm using Mesa ( which kills Blender ) SMP support was very fine. But I have to enable GLX and OpenGl support to work, and I need HT enabled to acelerate Rendering tasks. 

Someone knows what happened since 6.06 that killed smp support after installing a driver ?

I'm really thinking in come back to 6.06 but yafray 0.0.9 break packages and Blender 2.42a does not work well with 0.0.8.2 wich is supllied in the multiverse oficial packages.

---

### Post by greylica on 2006-12-11
I discovered what is happening, The kernel 386 suplied is different from the kernel generic that is suplied from Canonical in a manner that is not fully trheaded. 
When we install the driver of Nvidia and do a full upgrade, teh New ACPI tells there is a device/conflict error and make the 386 kernel the only to boot in conjunction with Nvidia kernel.
What I did to solve the problem is reinstall the kernell headers and files from all of the availabble kernels and make a new config for X files that reinstalls  the driver and the xorg.conf, booting the machine with the correct kernel. 
The SMP correct kernel is the generic 686 kernel.
 
Thanks.

---

### Post by ElBuscador on 2006-12-11
Could you please provide more details on exactly what you did? I am having the same problem.

---

### Post by greylica on 2006-12-12
Thats what I did:

Run adept.
find the kernel packages.
install:
linux headers 2.6.17-10-generic
linux image-debug- 2.6.17-10-generic

restart your computer.
In Grub these options will appear

switch to 2.6.17-10-generic ( normal image kernel )
The system will try to run X but an error will hapen and you will be prompted to login.
When you login, be certain that the SMP is enabled reading the lines showed after you login.
With this kernel image loaded, type in the bash.

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-kernel-common
sudo nvidia-xconfig

this will force a reinstall of nvidia driver under the right kernel.
reboot you computer
run with the generic image
if everything goes well, the KDE or Gnome will start normally. If nothing happens. Do the proccess again.

---

### Post by ElBuscador on 2006-12-12
Thanks. It did not solve my problem, BUT it made me think. I realized that when I originally ran the Envy script <http://albertomilone.com/nvidia_scripts1.html>, I had probably done so while logged into the 386 kernel. I restarted, selected the generic kernel, ran the script, uninstalled the Nvidia driver, then ran it again to reinstall the driver. Success! Seems obvious in retrospect, but I spent hours trying to fix this before I realized the problem.

---


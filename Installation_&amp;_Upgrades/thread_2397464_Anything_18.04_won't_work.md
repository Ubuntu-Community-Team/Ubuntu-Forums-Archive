---
title: "Anything 18.04 won't work"
date: 2018-07-29
forum: Installation &amp; Upgrades
---

### Post by silent_20 on 2018-07-29
I have an HP Omen AX250WM laptop it has i7 7700HQ, gtx1050ti, 12g of ram. I'm trying to use "Try before you install" with ubuntu, xubuntu, and ubuntu mate all of them 18.04. When they boot to desktop I can't click or type anything its like if the computer froze, the only thing I can do is move the cursor. I have to do a hard shutdown by pressing and holding the power button. The weird thing is that I can use Ubuntu 16.04 and 17.10 without a problem. I haven't tried installing any of them on this laptop. The same usb drive that I used on this laptop I used on my desktop and it works fine on the desktop.

---

### Post by seattlechris on 2018-07-31
> **silent_20 said:**
> When they boot to desktop I can't click or type anything its like if the computer froze, the only thing I can do is move the cursor. I have to do a hard shutdown by pressing and holding the power button. 

I had the same problem installing Ubuntu 18.04 on my machine which has a Nvidia 1050Ti graphics card. On the grub2 menu where it gives you the option to "try ubuntu before install" or to "install", you can press 'e' to edit the commands for which ever option you are selected on. From there you find where it says splash and right after that type a space and nomodeset. Press F10 (or other methods to run the install). This will allow you to run the "try before install" (or install) without the mouse clicks and keyboard freezing up. So now you can run the install and select the correct graphics card drivers.

---

### Post by silent_20 on 2018-08-01
> **seattlechris said:**
> I had the same problem installing Ubuntu 18.04 on my machine which has a Nvidia 1050Ti graphics card. On the grub2 menu where it gives you the option to "try ubuntu before install" or to "install", you can press 'e' to edit the commands for which ever option you are selected on. From there you find where it says splash and right after that type a space and nomodeset. Press F10 (or other methods to run the install). This will allow you to run the "try before install" (or install) without the mouse clicks and keyboard freezing up. So now you can run the install and select the correct graphics card drivers.

Thanks I was able to get it boot with nomodeset. What gpu drivers I'm i supposed to use. I install nvidia drivers 
```
ubuntu@ubuntu:~$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001C8Csv0000103Csd00008259bc03sc02i00
vendor   : NVIDIA Corporation
model    : GP107M [GeForce GTX 1050 Ti Mobile]
driver   : nvidia-driver-390 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin
```
by using sudo ubuntu-drivers autoinstall

I then did a reboot but have the original problem. I'm I having this problem because I'm using "try before you install" or because I have to install another driver for nvidia, Thanks

---

### Post by deadflowr on 2018-08-01
> I'm I having this problem because I'm using "try before you install" or because I have to install another driver for nvidia, Thanks
The try ubuntu before install is the problem.
No matter what you do in that setting anything and everything is lost at reboot. Drivers included.
Try before install will run with the default open source nouveau drivers, which are probably inadequate for the task.

You might be able to set nouveau to use the nouveau.nomodeset=0 parameter in the kernel at boot.
Such as from this
[https://askubuntu.com/questions/747314/is-nomodeset-still-required]("https://askubuntu.com/questions/747314/is-nomodeset-still-required")
That might at least allow usage during the try before install, and allow an installation to proceed from there.

I would forgo the advice in the link to install the nvidia -352 drivers and such and instead post install run the ubuntu drivers commands you already tried.

---


---
title: "ubuntu  14.04 : after an upgrade, no graphic modes possible and blank screen"
date: 2015-01-03
forum: Installation &amp; Upgrades
---

### Post by denis-royer on 2015-01-03
ubuntu  14.04 : after an upgrade, no graphic modes possible and blank screen with nvidia 7300gt.

How can we change the graphic configuration ? (no recovery modes work)

thanks.

---

### Post by MAFoElffen on 2015-01-03
On an installed system- 
1. If you have a multi-boot yss installed skip #2
2. At just as the BIOS messages pass, start intermittently pressing the <left-shift> key. 
3. When the Grub Menu appears, prees <E> to enter an edit mode
4. While in edit mode, <Arrow-Down> to Linux Boot line. It starts with "linux". 
5. <Arrow-Right> to the end of the line.
6. ** append the end of that line with the kernel boot option "text".
7. Press <cntrl><X> to boot
That will let you boot to a text tty console...
8. Log in with your credentials. Then, do this (ignore a file not found on the second, which is just to remove if there...)
```

sudo apt-get update
sudo nvidia-installer --uninstall
sudo apt-get remove nvidia-*
Kversion=(uname -r)
sudo apt-get install linux-headers-$Kversion
sudo apt-get install nvidia-current  
sudo nvidia-xconfig
sudo apt-get update
sudo apt-get upgrade
sudo reboot

```

Tell me how it goes and ask question if you have them...

---

### Post by denis-royer on 2015-01-04
hello !
I 've done all you told me (but line 4 : Kversion=uname -r  then : -r command not found)
but after reboot, same box, something like :  recorded configuration of screens can't be applied  /  no choosen modes are compatible with the possible ones  /  test of modes for CRTC81 ....

I just can close the box, then black screen.

so, if you have new idea ...

---

### Post by tokyobadger on 2015-01-04
Try this (should achieve what line 4 and 5 above would)
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by MAFoElffen on 2015-01-04
Sorry, my 3rd command edited now...

Or just do line 3 to return what Linux kernel version you are running on, copy that down... and use that result to install the correct version of it's header package.

---

### Post by denis-royer on 2015-01-04
I try the new lines you told me, it doesn't seemed to work completely ("can't find linux-headers-$" for example) but finally I could reboot.
So it works but the graphic card is now called (in the system parameters) : gallium 0.4 on nv4b (instead of NVIDIA 7300gt)
It has to be changed ?

thanks for all.

---


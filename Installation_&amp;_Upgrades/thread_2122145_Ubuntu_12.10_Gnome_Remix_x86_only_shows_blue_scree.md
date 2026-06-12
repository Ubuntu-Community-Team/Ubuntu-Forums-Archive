---
title: "Ubuntu 12.10 Gnome Remix x86 only shows blue screen after startup"
date: 2013-03-04
forum: Installation &amp; Upgrades
---

### Post by JoelSteiger on 2013-03-04
hello,

i installed ubuntu 12.10 gnome remix (32bit) and the amd catalyst 13.1 driver for my gigabyte amd radeon hd 6450 graphics card (by downloading it from the amd website and running the installer via "./" in the terminal), which worked very well until i updated my system using the updatemanager. since i've been rebooting the first time after the update-manager suggested it i get a blue screen everytime i boot ubuntu.
i tried killing the x-server, but i think i doesn't even load, due to Ctrl + Alt + F1 doesnt work and the screen stays blue. it doesnt work anything to be exactly.
then i tried to boot with the VESA mode by adding "xforcevesa" in the "linux (...)" line in grub and/or adding "text" to start in the console mode, but this didnt help either and i still get the blue screen.
of course, i also tried the recovery mode: when i select the option dpkg, that repairs damaged packages, im told (in the console) nothing has been repaired and i get back to the recovery mode menu.
when i try the "failsafeX" failsafe graphics mode i get a window that tells me the system is running the low graphics mode and my screen, graphics or input device settings are not correctly detected and i have to configure them by myself. if i click ok, i get to another window, where i can select 4 options:
1. run in low-graphics mode for one session (i get back to the recovery menu)
2. reconfigure graphics (nothing happens)
3. exit to console login (i get back to the recovery mode menu)
4. troubleshoot: i can view the startup errors logfile. everythings seems to be OK, except these last lines:
```
atiddxDriScreenInit failed (kernel module missing or incompatible)
(EE)fglrx(0): DRi Initialization failed
(WW)fglrx(0): kernel module (fglrx.ko) missing or incompatible
(WW)fglrx(0): 2D and 3D acceleration disabled
(II)fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x10000000
/usr/bin/X: symbol lookup error: /usr/lib/xorg/modules/drivers/fglrx_drv.so: undefined symbol:
GlxInitVisuals2D

```

so what can i do to fix this error?

sorry for my bad english and thanks in advance :)

---


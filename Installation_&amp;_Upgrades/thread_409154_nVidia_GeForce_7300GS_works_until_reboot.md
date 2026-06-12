---
title: "nVidia GeForce 7300GS works until reboot"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by sparky-steve on 2007-04-14
Hiya,

Just built a new PC, and put an nVidia GeForce7300GS (Gigabyte) graphics card in.

Kubuntu 6.10, fully updated, on 2.6.17-11-generic #2 SMP

I downloaded NVIDIA-Linux-x86-1.0-9755-pkg1.run from nVidia and run it - everything works fine, and my Acer 2416 monitor runs smooth at 1920x1200.  

I'm also running Beryl (which rocks!) but this problem occurs with & without Beryl.

The problem is - as soon as I reboot the system, it "forgets" everything, and I have to run the nvidia program again as root, then su to my local user, and "startx" - I'd much rather have a normal boot.

This is the error shown on screen:

```

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

Any ideas and pointers very welcome!

Happy ubuntu!
Steve

---

### Post by lucky2 on 2007-04-14
Im using a 6200 with exactly hte same problem although I did not know to su to local user and login, so least I can log in now ;F but I'm still left with the ame problem as you mate, any help bump bump cheers

---

### Post by sparky-steve on 2007-04-14
Hey Buddy,

Well, I've solved mine - it was embarrassingly obvious; The linux-restricted-modules driver "nv" was default, and started at bootup.

This is the site I found: [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

Specifically:

> If you use Ubuntu, please also ensure that the linux-restricted-modules packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv"

If you require further assistance after following the instructions above, please see:
[http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678).

So I dropped to root, edited the file (in my case it was /etc/default/linux-restricted-modules-common) rebooted, and all was fine.

Hope this helps you out.

Steve

---

### Post by roopesh on 2007-04-15
Steve -

Thanks, that was perfect.

Roopesh

---

### Post by lucky2 on 2007-04-15
Yup same for me, now to get sound working in Quake3.......... .   . . . .. ...        . . .  ..

---


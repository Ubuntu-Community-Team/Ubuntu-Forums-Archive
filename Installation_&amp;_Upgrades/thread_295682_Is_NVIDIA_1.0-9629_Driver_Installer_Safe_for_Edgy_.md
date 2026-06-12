---
title: "Is NVIDIA 1.0-9629 Driver Installer Safe for Edgy 64?"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by foxmajik on 2006-11-08
Is the installer for the new nVidia driver available here safe for use on Ubuntu Edgy 64?

[http://www.nvidia.com/object/linux_display_ia32_1.0-9629.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9629.html)

My system is working nicely with an existing accelerated driver and I don't want to risk hosing it (after having to go into rescue to restore my fstab last night following the installation of dchroot :mrgreen: ).

If the installer isn't safe, is there another way to install the new driver that supports GLX_EXT_texture_from_pixmap that will work better?

---

### Post by foxmajik on 2006-11-08
Answering my own question, the installer seems to work just fine on my system as described.

The only small problem I had was that beryl-manager generated a crash report on first launch, but I think that's because I have it running twice on login, once in my beryl init script and again in my gnome startup programs panel.

---

### Post by Cariboo1938 on 2006-12-13
> **foxmajik said:**
> Answering my own question, the installer seems to work just fine on my system as described.
.....
 
Hello,
I have a problem using the NVIDIA installer. I run Ubuntu Edgy-amd64 and I downloaded the NVIDIA driver version 1.0-9631. Using ```
sudo sh NVIDIA-Linux-x86_64-1.0-9631-pkg2.run
``` I had no errors. But after reboot the computer my X window server was killed. I found Error message in /var/log/xorg.0.log> Failed to initialize the NVIDIA kernel module. Please ensure that there is a supported NVIDIA GPU in this system and that the NVIDIA device files have been created properly.Aborting: 
UnloadModul "nvidia"
UnloadModul "ramdac"
UnloadModul "cfb"
Screens found, but none have a usable configuration.Has one an idea what went wrong? I have no clue...this is far to much Linux for me!

---


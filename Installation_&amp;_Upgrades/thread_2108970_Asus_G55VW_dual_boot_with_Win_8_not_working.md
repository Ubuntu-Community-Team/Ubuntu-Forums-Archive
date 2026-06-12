---
title: "Asus G55VW dual boot with Win 8 not working"
date: 2013-01-26
forum: Installation &amp; Upgrades
---

### Post by Lothas on 2013-01-26
Hi, I just bought a new Asus G55VW ROG notebook. I'm trying to install Ubuntu 12.04 LTS alongside Windows 8 without success.

I tried several different things:
1. I installed from Windows using wubi. Now in win boot loader I get Win 8 and Ubuntu but Ubuntu won't load (I get an black error screen about wubildr)
2. I tried installing Ubuntu from a live-USB but Ubuntu wouldn't load the desktop environment, just a command line.
3. So I tried to install Ubuntu without trying it before and the installer run "smoothly" (with GUI). After rebooting the PC I get to grub and I have all the options: Ubuntu, recovery, Win 8, etc. The problem is that Ubuntu still won't load the desktop environment.
4. I tried installing the nvidia-current drivers from the command line but it keeps complaining about held back packages and missing dependencies

HELP!!! ](*,)

---

### Post by oldfred on 2013-01-26
Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)

     You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

IF you have nvidia, then you need nomodeset on first boot.

            How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I had to install linux headers first to get nVidia drivers to install correctly.
       [http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

---


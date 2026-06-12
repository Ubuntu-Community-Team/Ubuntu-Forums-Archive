---
title: "Overnight update broke Ubuntu 12.04 LTS Nvidia GT640 support"
date: 2013-07-10
forum: Installation &amp; Upgrades
---

### Post by John Nagle on 2013-07-10
Today's overnight auto-update to Ubuntu 12.04 LTS broke NVidia display support.

I'm now stuck at 800x600, and Displays says "Laptop" instead of the actual display, which is much larger and on an Nvidia GT640. 
"Detect displays" does nothing. 

Settings/Graphics says "Driver VESA: GK107 board - 20110000" 

This is a brand new AMD64 machine, a week old, with Ubuntu installed by the dealer. 

Why is auto-update doing something this stupid, and how can I fix it?

---

### Post by BreezyBrooke on 2013-07-10
Who is the dealer you bought it from? Contact them. They will probably give you better support than we can. They built the thing and configured it for Ubuntu right?

---

### Post by snowpine on 2013-07-10
Does it work if you select your previous kernel from the GRUB boot menu?

as described here: [http://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version](http://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version)

---

### Post by John Nagle on 2013-07-10
This appears to be a common problem, and at least five articles discuss how to fix it. All have different fixes. 

[http://ubuntuforums.org/showthread.php?t=1678203](http://ubuntuforums.org/showthread.php?t=1678203)
[http://askubuntu.com/questions/202677/nvidia-driver-doesnt-work-in-12-10](http://askubuntu.com/questions/202677/nvidia-driver-doesnt-work-in-12-10)
[http://askubuntu.com/questions/223928/ubuntu-stops-using-nvidia-driver-after-kernel-upgrade](http://askubuntu.com/questions/223928/ubuntu-stops-using-nvidia-driver-after-kernel-upgrade)
[http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal](http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal)
[http://askubuntu.com/questions/302628/resolution-and-unity-broken-after-kernel-update-in-12-04-with-nvida](http://askubuntu.com/questions/302628/resolution-and-unity-broken-after-kernel-update-in-12-04-with-nvida)

I thought that things like this weren't supposed to happen when running a "Long Term Support" version.

---

### Post by John Nagle on 2013-07-10
"GRUB boot menu"...

**There is no GRUB**. This is a brand new machine with UEFI and Canonical's Ubuntu. See:

[http://www.extremetech.com/computing/131628-canonical-explains-decision-to-ditch-grub-2-on-uefi-systems](http://www.extremetech.com/computing/131628-canonical-explains-decision-to-ditch-grub-2-on-uefi-systems)

---

### Post by Cavsfan on 2013-07-10
> **John Nagle said:**
> "GRUB boot menu"...

**There is no GRUB**. This is a brand new machine with UEFI and Canonical's Ubuntu. See:

[http://www.extremetech.com/computing/131628-canonical-explains-decision-to-ditch-grub-2-on-uefi-systems](http://www.extremetech.com/computing/131628-canonical-explains-decision-to-ditch-grub-2-on-uefi-systems)

I just thought I hated windows 8 but, now I really know that I hate windows 8. I'm going to stick with Windows 7 until the last moment of support. Everyone I know complains about W 8.

---

### Post by John Nagle on 2013-07-10
OK, with UEFI, ESC will get into GRUB.  So I booted the previous kernel, "3.2.0-29-generic". Still at 800x600 "Laptop" mode, with no other options available under "Display".  

However, Settings->Additional Drivers allowed me to re-install the supported NVidia proprietary driver. After a reboot, everything worked as before. That's what I should have done in the first place.

So why did auto-update knock out a supported driver?

---

### Post by Cavsfan on 2013-07-10
> **John Nagle said:**
> OK, with UEFI, ESC will get into GRUB.  So I booted the previous kernel, "3.2.0-29-generic". Still at 800x600 "Laptop" mode, with no other options available under "Display".  

However, Settings->Additional Drivers allowed me to re-install the supported NVidia proprietary driver. After a reboot, everything worked as before. That's what I should have done in the first place.

So why did auto-update knock out a supported driver?

Not sure but, I have had problems with 12.04's nvidia driver myself. I almost lost it once. I tried xswat's ppa to get the latest stable driver and ended up having to re-install.
Do you use update manager? If so I would suggest using manual CLI commands.
**sudo apt-get update & sudo apt-get upgrade** and then if you see an nvidia driver in the mix just enter **apt-cache policy *file-name***. Then you can see what is going to happen.
Then if anything is held back, enter **sudo apt-get dist-upgrade** and you will probably see other new files will be installed and some upgraded. This is how to get new kernels.

To make the above easy as pie edit .bashrc and add these aliases at about line 92:
**gedit ~/.bashrc**

```
# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade' 
```

Then you logout and back in to use them. You just enter **ud** and your password or **ud2** after getting updates if anything is held back.

---

### Post by snowpine on 2013-07-10
If you want more control, then disable auto-updates. Linux is all about choice, and we can choose how much control to have over the system. :)

---

### Post by oldfred on 2013-07-10
Canonical reversed themselves and are using grub2 with shim to secure boot UEFI with Windows. If not dual booting Windows you do not need secure boot.
      
 UEFI generic shim - Secure Boot bootloader
[http://mjg59.dreamwidth.org/20303.html](http://mjg59.dreamwidth.org/20303.html)

With 12.10 I had to install the headers before doing anything with nVidia, so that kernel updates would run including the nVidia drivers. If 12.04.2 you are using the same kernel and may also need the headers.


 sudo apt-get install linux-headers-generic


 From  bogan
To bring it fully up to date, instead of: 'nvidia-installer --update', use 'nvidia-installer -f --dkms'.
The '-f' option implies the inclusion of: '--update', but will force a re-installation even if the currently installed version is the same as the 'latest' which it will download and install.
The '--dkms' option, with driver versions 3.04.xx and later, will check that 'dkms' is installed and offer the option to register the driver with dkms, so the kernal module gets updated automatically when a new kernal is installed. and does not need to be manually re-installed.

 Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

---

### Post by Cavsfan on 2013-07-11
> **oldfred said:**
> Canonical reversed themselves and are using grub2 with shim to secure boot UEFI with Windows. If not dual booting Windows you do not need secure boot.
      
 UEFI generic shim - Secure Boot bootloader
[http://mjg59.dreamwidth.org/20303.html](http://mjg59.dreamwidth.org/20303.html)

With 12.10 I had to install the headers before doing anything with nVidia, so that kernel updates would run including the nVidia drivers. If 12.04.2 you are using the same kernel and may also need the headers.


 sudo apt-get install linux-headers-generic


 From  bogan
To bring it fully up to date, instead of: 'nvidia-installer --update', use 'nvidia-installer -f --dkms'.
The '-f' option implies the inclusion of: '--update', but will force a re-installation even if the currently installed version is the same as the 'latest' which it will download and install.
The '--dkms' option, with driver versions 3.04.xx and later, will check that 'dkms' is installed and offer the option to register the driver with dkms, so the kernal module gets updated automatically when a new kernal is installed. and does not need to be manually re-installed.

 Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

Thank you Canonical for that decision! Thank you **oldfred** and **bogan** for the information! :) I just might give that a shot on my Precise install.

---


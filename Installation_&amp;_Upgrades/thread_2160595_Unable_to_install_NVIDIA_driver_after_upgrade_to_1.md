---
title: "Unable to install NVIDIA driver after upgrade to 13.04"
date: 2013-07-07
forum: Installation &amp; Upgrades
---

### Post by Ambidextrous on 2013-07-07
I upgraded from 12.10 to 13.05 a few days ago.  I ran software updates and installed everything offered before running the upgrade, but something didn't go quite as it should have: the upgrade seemed to have trouble installing the kernel.  I ran *apt-get install* which seemed to fix things... until I tried to get both monitors working at their correct resolutions.

None of the installed drivers worked, so I went to NVIDIA and downloaded the latest for my card (GeForce GT 640).  I discovered the installer wouldn't work with X running, so I tried booting into recovery mode.  I got a blank screen with the two versions on the main menu of GRUB, and with one of the "previous versions".  The other previous versions gave me an error message to the effect that they weren't really there. I booted into Gnome, switched to TTY-2, used *sudo stop lightdm* to stop X and ran the installer (*NVIDIA-Linux-x86_64-295.53.run*). I then got a series of error messages (which I don't remember verbatim, sorry) the gist of which seemed to be the kernel isn't the one the installer was expecting and the GCC compiler was the wrong version.

I believe the real problem is the incomplete upgrade.  Can I salvage it?  I'd really rather not do a complete re-install.

Thanks in advance.

Terry

---

### Post by gordintoronto on 2013-07-07
I'm no fan of upgrading. I have separate / and Home partitions, and I've never lost any data doing a full install.

Video drivers have moved: they are now in one of the sub-menus of Software Centre. I always take nvidia-current.

"Seemed to have trouble installing the kernel" isn't very descriptive. Have you removed obsolete kernels, or just let them pile up?

---

### Post by Ambidextrous on 2013-07-08
1. I have made it a habit to remove old kernels.  Normally only the three latest remain on my system.  Why is that important or relevant to my issue?

2. Are you suggesting that I should attempt to install the nvidia-current driver from the Ubuntu software centre?

---

### Post by Frogs Hair on 2013-07-08
It looks like you may have an Optimus card and if that is the case you can look into Bumblebee. I am not suggesting you install Bumblebee  until you are sure it is applicable to your card .  

[www.nvidia.in/object/geforce-gt-640m-in.html](www.nvidia.in/object/geforce-gt-640m-in.html)  
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by 2Stoned on 2013-07-08
Remove the older Nvidia files from your system. 
```
sudo apt-get remove --purge nvidia*
```

When you have removed the older Nvidia files from your system install the current drivers from the command line and reboot:
```
sudo apt-get update
sudo apt-get install nvidia-current
sudo reboot
```

---

### Post by Ambidextrous on 2013-07-08
> **Frogs Hair said:**
> It looks like you may have an Optimus card and if that is the case you can look into Bumblebee. I am not suggesting you install Bumblebee  until you are sure it is applicable to your card .  

[www.nvidia.in/object/geforce-gt-640m-in.html]("http://www.nvidia.in/object/geforce-gt-640m-in.html")  
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

This is a desktop, not a laptop.  The link you included to NVIDIA's Indian website only mentioned laptops/notebooks. Some quick research suggests that the Optimus chip is only used on cards with the "M" suffix (eg GT 640M), presumably it stands for "mobile" so I'm giving Bumblebee a miss until I've explored more promising options.

Thanks for the suggestion, though.

---

### Post by gordintoronto on 2013-07-09
> **Ambidextrous said:**
> 1. I have made it a habit to remove old kernels.  Normally only the three latest remain on my system.  Why is that important or relevant to my issue?

2. Are you suggesting that I should attempt to install the nvidia-current driver from the Ubuntu software centre?

If there is a boot partition, it can be overwhelmed by a build-up of kernels, and this could show up at upgrade time.

Yes, I was suggesting installing nvidia-current from the software centre. Or the command-line, as per 2Stoned's suggestion.

---

### Post by Ambidextrous on 2013-07-09
Thank you all for your suggestions, but nothing worked until I reinstalled 13.04 :(

Even after that it took several attempts but eventually 
[I]
sudo apt-get --purge nvidia*
sudo apt-get install nvidia-current[/I]

followed by a reboot did the trick.  Now all I have to do is get rid of Unity and reinstall the software which was lost in the reinstallation.

Terry

---

### Post by 2Stoned on 2013-07-10
> **Ambidextrous said:**
> Now all I have to do is get rid of Unity and reinstall the software which was lost in the reinstallation.

Terry

There should be a file somewhere containing all the names of previous applications, i just forgot what the name was :-k

To remove Unity completely from your system, try the following commands: 

   ```
sudo apt-get --purge remove unity unity-2d unity-2d-panel unity-2d-spread
sudo apt-get --purge remove unity-asset-pool unity-services unity-lens-* unity-scope-*
sudo apt-get --purge remove liboverlay-scrollbar*
sudo apt-get --purge remove appmenu-gtk appmenu-gtk3 appmenu-qt
sudo apt-get --purge remove unity-2d-common unity-common
sudo apt-get --purge remove libunity-misc4 libunity-core-5*
```

Make sure you have another window manager installed.

---


---
title: "a bit complicated mess"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by njcf on 2010-05-23
i tried to triple boot ubuntu, xubuntu and xp. I know you can put the XFCE environment on ubuntu but i wanted a new installation. Long story short, in xp the ubuntu folder was renamed to allow the xubuntu to be installed. when i restarted grub only showed xubuntu and windows. When i uninstalled xubuntu and renamed the ubuntu folder back to "ubuntu" it never showed up on grub, only xp shows. i have alot of important files on ubuntu, the installation is still there, i just need it to be back on grub
thanks

---

### Post by darkod on 2010-05-23
You tried to install two different versions of wubi inside windows???

First of all, especially since you said you have important files in wubi (it's not ubuntu, it's wubi), you should know that wubi was never meant to be a long term install. Just a quick way to try ubuntu. And you can also try it in live mode from the ubuntu cd.

The triple boot you wanted would have worked just fine if you did proper installs, not inside windows.

Set XP to show you the hidden files and find C:\boot.ini. Open it with notepad and add a line for wubi, it should be something like:

C:\wubildr.mbr ubuntu

or similar, depending if you installed wubi in C:, D:, etc. Reboot and see if that helped.

You might also wanna read around first how the entry in boot.ini should look like, I'm not 100% sure.

PS. And you don't have grub, that's the windows bootloader you are seeing. Wubi doesn't install grub to the MBR. Which makes saving your wubi more complicated, as you noticed.

---

### Post by njcf on 2010-05-23
> **darkod said:**
> You tried to install two different versions of wubi inside windows???

First of all, especially since you said you have important files in wubi (it's not ubuntu, it's wubi), you should know that wubi was never meant to be a long term install. Just a quick way to try ubuntu. And you can also try it in live mode from the ubuntu cd.

The triple boot you wanted would have worked just fine if you did proper installs, not inside windows.

Set XP to show you the hidden files and find C:\boot.ini. Open it with notepad and add a line for wubi, it should be something like:

C:\wubildr.mbr ubuntu

or similar, depending if you installed wubi in C:, D:, etc. Reboot and see if that helped.

You might also wanna read around first how the entry in boot.ini should look like, I'm not 100% sure.

PS. And you don't have grub, that's the windows bootloader you are seeing. Wubi doesn't install grub to the MBR. Which makes saving your wubi more complicated, as you noticed.


i cant find that file.
also, what do you mean wubi was not meant for long term installation. everyone i know has a dual boot, not just ubuntu

---

### Post by darkod on 2010-05-23
> **njcf said:**
> i cant find that file.

Which one, I mentioned two files?

Better yet, can you run these instructions from live mode and post the content of your results file:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---


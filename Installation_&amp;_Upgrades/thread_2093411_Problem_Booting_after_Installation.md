---
title: "Problem Booting after Installation"
date: 2012-12-10
forum: Installation &amp; Upgrades
---

### Post by dstnvns on 2012-12-10
After installing Lubuntu 12.10 the system reboots and shows disk activity but the screen remains blank. This has been problematic on two systems, one a dual boot with Windows 7 and the other a clean install. Both systems have AMD Processors and at least 2GB of RAM. Both systems have use nVidia chipsets, and were able to boot from USB without any problems. The ISO image used to create the Live USB drive had the correct MD5 (I was used to install Lubuntu on the system I'm using at the moment)

I hope I'm not asking a question that has already been addressed, but after searching I was only able to find issues where something was displayed on the screen while the boot was failing.

---

### Post by oldfred on 2012-12-10
With nVidia I have had to add nomodeset to get liveCD or first boot to work since they integrated video into kernel.

But with 12.10 I also had to download headers to then get the default nvidia drivers to correctly install. 

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
       [http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available  versions:
apt-cache search nvidia-sett*
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current, use version you prefer
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

   Fix for nVidia with 12.10 missing kernel dpkg reconfigure:
[http://ubuntuforums.org/showthread.php?t=2072862](http://ubuntuforums.org/showthread.php?t=2072862)

---

### Post by dstnvns on 2012-12-10
The information about nomodset that you provided a link to gives me the impression that you can either specify it from the boot menu or make the change using a terminal. Since I don't have the option of doing so at boot I would have to do so after installation but before rebooting the system. If I make the necessary changes after installation but while still running a Live session its my guess I will need to ensure I specify the correct GRUB (On the system disk)?

Likewise with regards to downloading headers and the other tasks adding or removing packages. Can I do so to the installed version without the reboot first?

---

### Post by dstnvns on 2012-12-10
I should have read things with more care, if I had the previous question wouldn't have been necessary. Problem fixed and thank you!

---


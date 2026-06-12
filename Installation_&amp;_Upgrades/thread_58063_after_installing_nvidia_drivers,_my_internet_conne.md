---
title: "after installing nvidia drivers, my internet connection doesn't work"
date: 2005-08-18
forum: Installation &amp; Upgrades
---

### Post by vitruvio on 2005-08-18
hi all

after a clean install of ubuntu 5.04 all works fine (except sound, solved changing oss to alsa), and network connection works with dhcp.
But after installing nvidia drivers with these commands

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

(i wrote this code in the file)

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

so nvidia after a reboot works fine, but not my inet connection...
i cant connect to the router trough 192.168.1.1 ....and if i try an ifup eth0 computer crashes.
I checked all options and seems to be ok, my connection works with dhcp, so i dont know what is happening.

anyone have a similar problem?, or just know what can be?

thanks

---

### Post by tseliot on 2005-08-18
I don't know what can be causing your problem but you can try my HOWTO, otherwise I wouldn't know how to help you:

[http://www.ubuntuforums.org/showthread.php?t=57368](http://www.ubuntuforums.org/showthread.php?t=57368)

---

### Post by vitruvio on 2005-08-21
Ok, after a week of headcaches and 3 or 4 reinstallations of the system i have found the solution.
I remembered some days ago i was changing my bios (my card doesnt not work at AGP 8x so i have to use 4x, but videocard is not the problem), and a similar problem happens to me in windows....and the problem was the soundcard, i have two installed, a cmedia and the motherboard one, the motherboard one is deactivated, but the gameport is, and this wasthe cause of my headcache, i think this is because the irqs,system get out of irqs or just not share well and crash my system.

problem solved! \\:D/

---


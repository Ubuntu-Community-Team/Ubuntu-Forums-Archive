---
title: "system hang up during install"
date: 2006-03-24
forum: Installation &amp; Upgrades
---

### Post by axelbjel on 2006-03-24
I've tried for hours installing Ubuntu but I get a system crash every time. This is what happens: The installation CD is out and the installer is working with the HDD. Suddenly a window named "Configuring xserver-xorg" is popping up and asks to "Select the video modes you would like the X server to use". (I have a 20"LCD Widescreen 1680*1050.) System platform is: Asus A8N-VM CSM motherboard based on the NVIDIA GeForce 6150 + nForce 430 with integrated sound, GB LAN with firewall, 1394, graphics, SATA II with RAID, DVI-D. could som of this integrated stuff cause problems? I run WinXP on 1. primary partition, trying to make a dual boot configuration. I really want to try out Linux, but this is difficult.](*,)

---

### Post by Sef on 2006-03-24
Have you tried to use a live cd?  By using a live cd, you could see if the problem was with the hardware or the cd itself.

---

### Post by Mustard on 2006-03-24
[QUOTE=axelbjel]I've tried for hours installing Ubuntu but I get a system crash every time. This is what happens: The installation CD is out and the installer is working with the HDD. Suddenly a window named "Configuring xserver-xorg" is popping up and asks to "Select the video modes you would like the X server to use". (I have a 20"LCD Widescreen 1680*1050.) System platform is: Asus A8N-VM CSM motherboard based on the NVIDIA GeForce 6150 + nForce 430 with integrated sound, GB LAN with firewall, 1394, graphics, SATA II with RAID, DVI-D. could som of this integrated stuff cause problems? I run WinXP on 1. primary partition, trying to make a dual boot configuration. I really want to try out Linux, but this is difficult.](*,)[/QUOTE]

If its having display issues it might be best to try using the 'vesa' drivers rather than the 'nv' drivers for nvidia.

If you get dropped to a command line/login prompt, you can use this command below to attempt to reconfigure you xorg.conf file. With a login prompt,  login using your username and password that you chose on the install. Then try do the command...

```
sudo dpkg-reconfigure xserver-xorg
```

If you can't see a command prompt try ctrl + alt + f1 (or use any other function key in this combination from f1 to f6).  

If it reconfigures successfully do one of these commands below to restart the display..

```
startx
```

or 

```
sudo /etc/init.d/gdm restart
```

If you get any errrors along the way that cause these steps to fail, then post them in here so we can troubleshoot further.

Its likely that you are going to end up getting some resolution setting that you don't really want, but the main part of this exercise is to get GUI.  From there its going to be another process to get your display working at the resolution you want.

---

### Post by axelbjel on 2006-03-25
I thought it was the CD so I downloaded the file, burned it and tried over again. Same shit happens, so I guess thats not the problem.

What happens is the screen get crowded with all these commands, and when I hit ctrl + alt + f1 nothing happens.

---


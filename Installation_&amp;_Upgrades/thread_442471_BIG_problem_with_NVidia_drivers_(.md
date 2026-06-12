---
title: "BIG problem with NVidia drivers :("
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by BorgCymru on 2007-05-13
Very VERY new to Ubuntu

I downloaded the drivers from NVidia and followed their instructions but it kept saying it couldn't find the file.

> STEP 3: Install
Type "sh NVIDIA-Linux-x86-1.0-9755-pkg1.run" to install the driver. NVIDIA now provides a utility to assist you with configuration of your X config file. 
HELP HELP HELP



So I Started to do what is written in the 'how to' 


used the command in step 2

> sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-`uname -r`

Got an error message which I didn't read :( was to busy trying to read the web page

I then followed step 3 

> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
sudo nvidia-glx-config enable 
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

Then step 4  wrote this in the text window that opened and saved it.

> [Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;}}

After the 

> CTRL+ALT+BACKSPACE

Then I get a large page of something telling me X server couldn't start because there was no video drovers.

I tried logging in with the safe mode GFX option but still get a GFX warning but do get to a command prompt but have no idea how to restore the GFX drivers.

HRLP please, what do I do

---

### Post by hal8000 on 2007-05-13
Just try this in a terminal


sudo apt-get install nvidia-glx nvidia-kernel-common

the password is your normal password, restart the x server, ctrl-alt-backspace and hopefully all will be working. Thats all I did for Feisty 7.04.

---

### Post by BorgCymru on 2007-05-13
Excellent that worked great and even gave me a NVidia control panel in system tool, wonder why the new downloaded drivers won't run/install.

Thanks mate nice one.

---


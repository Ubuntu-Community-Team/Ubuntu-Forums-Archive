---
title: "black screen"
date: 2005-06-08
forum: Installation &amp; Upgrades
---

### Post by xirix on 2005-06-08
well i'm newby in linux software.

i install ubuntu 5.04 but when it get start the monitor get black.

i was trying the nvidia install notes

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

i don`t much about, but i think that ubuntu doesn`t recognize my old monitor please i need help for someone 

pc:
athlon 2800
geforce fx5200
msi kt600
syncMaster 550v

---

### Post by Seti on 2005-06-09
If anything it looks like you didn't do it correctly.
```
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
``` 
is what you have to do.

then...

"Insert the following lines into the new file

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;
..."
Otherwise it should work. After you restart X you should see that big beautiful nVIDIA splash-screen.

---

### Post by xirix on 2005-06-10
seti thanks for you reply

i did what you said in (recovery mode), but didn't work

i couldn't edit 

appear: (gedit:5811):Gtk-warning**:cannot open display

please be patience!, and help me!

---


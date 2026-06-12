---
title: "unable to use gui"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by joyson20 on 2008-08-29
Yesterday i did a great mistake....i have an intel graphics card...but i dont know the details of it ....i was trying to change the driver configuration through the menu...instead of choosing intel i chose nvidia and gave ok....but now when i log in it says some x11 error....i dont know to use the command line ....i am stuck and dont know what to do...can some one please help me with how to change the configuration to intel experimental mode...please..please

---

### Post by nicolaary on 2008-08-29
Can you please post your X error and your Xorg.conf file?

---

### Post by nicolaary on 2008-08-29
at least this part of xorg.conf


Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"                <==================
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

---

### Post by joyson20 on 2008-08-29
sorry i am hopeless without a gui and i dont know where to go or what to do....all i can understand is now it says  no hardware for the driver....this may not be enough...but i dont know to go anywhere beyond this...can you please tell me how to get it

---

### Post by joyson20 on 2008-08-29
today morning even when i typed some directory path it showed it said permission denied

---

### Post by nicolaary on 2008-08-29
Anyway if you rename your /etc/X11/xorg.conf the system offer you a repair tool to fix your problem with default values...

---

### Post by nicolaary on 2008-08-29
can you please type in your console the > startx command and post here your error message?

---

### Post by joyson20 on 2008-08-29
can you please tell me how to do it in command line

---

### Post by neurostu on 2008-08-29
Here is something you can try:
Uninstall all nvidia drivers:
```

sudo apt-get remove nvidia*

```
then move your xorg.conf file to a backup location and boot without one... X should then generate a new generic one...
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

---

### Post by perlluver on 2008-08-29
post the output of xorg, ```
cat /etc/X11/xorg.conf
```

then ```
sudo nano /etc/X11/xorg.conf
```

Look for driver, which should say nvidia, or nv.  Change that to intel.

---

### Post by joyson20 on 2008-08-29
thanks...i am on the net fron a surfing centre...will try it ...thanks a lot for your kind advice

---

### Post by sisco311 on 2008-08-29
Press Ctrl+Alt+F1 and log in in text mode.
Backup your xorg.conf file:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```Generate a new file with default settings:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```Restart the x server:
```
sudo /etc/init.d/gdm restart
```

---

### Post by nicolaary on 2008-08-29
in anycase the command that they have suggested above must be inserted with sudo word before.. The system will prompt for the password.. 

Like they have suggested to you! ;-)

You than type in your password!

---

### Post by joyson20 on 2008-08-31
Thanks a lot for your advice...It worked...thank God...

---

